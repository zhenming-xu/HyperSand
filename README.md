# HyperSand
---
HyperSand - библиотека для языка программирования Python, позволяющая рассчитывать объемы n-мерных фигур методом Монте-Карло. Для определения попаданий случайных точек внутрь фигуры используется алгоритм HyperSand.

Основные возможности:
  - Генерация сигналов-синусоид с переменными периодами и амплитудами (с помощью [numpy])
  - Интерполяция многомерных функций (с помощью [scipy])
  - Вычисление объема фигуры, используя метод Монте-Карло
  - Вывод графиков (с помощью [matplotlib])

## Содержание:
1. [Техническая информация](#Техническая_информация)
2. [Примеры и обучающие файлы](#Примеры-и-обучающие-файлы)
3. [Основной алгоритм](#Основной-алгоритм)
4. [Установка](#Установка)
5. [Удаление](#Удаление)
6. [License](#License)

## Техническая информация
Используемые библиотеки:
  - [numpy] - удобная работа с многомерными массивами
  - [pandas] - основной объект библиотеки hypersand, в котором содержатся данные - DataFrame
  - [scipy] - интерполяция функций
  - [matplotlib] - построение графиков

## Примеры и обучающие файлы
Примеры и обучающие файлы находятся в папке Examples. Их можно открыть с помощью [Jupyter] локально, или посмотреть онлайн на [github].

Вычисление площади окружности - [circle.ipynb]  
Вычисление площади двумерной фигуры - [2d.ipynb]  
Вычисление объёма сферы - [sphere.ipynb]  
Вычисление объёма трёхмерной фигуры - [3d.ipynb]  
Вычисление объёма n-мерной фигуры - [nd.ipynb]

## Основной алгоритм
Основной алгоритм определения попаданий точек внутрь фигуры (HyperSand) описан в функциях get_intersections, is_hit и hit_analysis модуля montecarlo.

Основные понятия:  
Сгенерированная точка - точка, с координатами, сгенерированными случайным образом (см. [Метод Монте-Карло]).  
Гиперплоскость - обобщение понятия плоскости для пространства произвольной размерности (см. [Гиперплоскость]).  
Интерполяция - нахождение промежуточных значений по заданному дискретному набору величин (см. [Интерполяция]).

1. Для сгенерированной точки, по каждой координате строятся перпендикулярные друг другу гиперплоскости, пересекающие данную точку. Например, для 2-мерного случая, строятся две перпендикулярные прямые, параллельные осям. Точка пересечения этих прямых - сгенерированная точка.
2. Проекция графика на каждую ось интерполируется.
3. Происходит поиск пересечений интерполированных графиков с построенными гиперплоскостями с заданной точностью.
4. По каждой координате сравниваются точки пересечений с сгенерированной точкой. Если хотя бы по одной оси окажется, что соответствующая координата сгенерированной точки меньше, или больше всех координат точек пересечений, то считается, что эта точка не попала внутрь фигуры.

## Установка
1. Загрузка  
1 способ:  
Загрузите библиотеку по [ссылке](https://github.com/deverte/HyperSand/archive/master.zip ).  
2 способ:  
Если у вас установлен [git], то выполните в терминале команду:  
```git clone https://github.com/deverte/HyperSand
```
2. Перейдите в директорию с библиотекой  
```cd HyperSand/hypersand
```
3. Установите библиотеку с помощью [pip]  
```pip install .
```

## Удаление
Выполните команду:  
```pip uninstall hypersand
```

## License

MIT

[//]: # (Reference links)

   [numpy]: <http://www.numpy.org/>
   [scipy]: <https://scipy.org/>
   [matplotlib]: <https://matplotlib.org/>
   [pandas]: <http://pandas.pydata.org/>

   [Jupyter]: <https://jupyter.org/>
   [git]: <https://git-scm.com/>
   [pip]: <https://pip.pypa.io/en/stable/>

   [github]: <https://github.com/deverte/HyperSand/tree/master/Examples>
   [circle.ipynb]: <https://github.com/deverte/HyperSand/blob/master/Examples/circle.ipynb>
   [2d.ipynb]: <https://github.com/deverte/HyperSand/blob/master/Examples/2d.ipynb>
   [sphere.ipynb]: <https://github.com/deverte/HyperSand/blob/master/Examples/sphere.ipynb>
   [3d.ipynb]: <https://github.com/deverte/HyperSand/blob/master/Examples/3d.ipynb>
   [nd.ipynb]: <https://github.com/deverte/HyperSand/blob/master/Examples/nd.ipynb>

   [Метод Монте-Карло]: <https://ru.wikipedia.org/wiki/%D0%9C%D0%B5%D1%82%D0%BE%D0%B4_%D0%9C%D0%BE%D0%BD%D1%82%D0%B5-%D0%9A%D0%B0%D1%80%D0%BB%D0%BE#%D0%93%D0%B5%D0%BE%D0%BC%D0%B5%D1%82%D1%80%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B9_%D0%B0%D0%BB%D0%B3%D0%BE%D1%80%D0%B8%D1%82%D0%BC_%D0%9C%D0%BE%D0%BD%D1%82%D0%B5-%D0%9A%D0%B0%D1%80%D0%BB%D0%BE_%D0%B8%D0%BD%D1%82%D0%B5%D0%B3%D1%80%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F>
   [Гиперплоскость]: <https://ru.wikipedia.org/wiki/%D0%93%D0%B8%D0%BF%D0%B5%D1%80%D0%BF%D0%BB%D0%BE%D1%81%D0%BA%D0%BE%D1%81%D1%82%D1%8C>
   [Интерполяция]: <https://ru.wikipedia.org/wiki/%D0%98%D0%BD%D1%82%D0%B5%D1%80%D0%BF%D0%BE%D0%BB%D1%8F%D1%86%D0%B8%D1%8F>
