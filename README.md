# GraphAlgorithms
## Part 1. Обход графа в глубину и в ширину
В данном проекте реализована библиотека s21_graph.h:
* Библиотека разработана на языке С++ стандарта C++17
* При написании кода использовался Google Style
* Библиотека представлена в виде класса `Graph`, который хранит в себе информацию о графе с помощью **матрицы смежности**. Размерность матрицы смежности задается динамически при инициализации графа (при его загрузке из файла)
* Сборка программы настроена с помощью Makefile со стандартным набором целей для GNU-программ: all, clean, test, s21_graph.a_
* Класс `Graph` содержит следующие публичные методы:
    + `loadGraphFromFile(string filename)` - загрузка графа из файла в формате матрицы смежности
    + `exportGraphToDot(string filename)` - выгрузка графа в файл в формате dot

Реализована библиотека s21_graph_algorithms.h_
* Библиотека представлена в виде класса `GraphAlgorithms`, который содержит в себе реализацию алгоритмов на графах.
* Класс `GraphAlgorithms` содержит в себе следующие публичные методы:    
    + `depthFirstSearch(Graph &graph, int startVertex)` - *нерекурентный* поиск в глубину в графе от заданной вершины. Функция возвращает массив, содержащий в себе обойдённые вершины в порядке их обхода. При реализации этой функции использована *самописную* структура данных **стек**.
    + `breadthFirstSearch(Graph &graph, int startVertex)` - поиск в ширину в графе от заданной вершины. Функция возвращает массив, содержащий в себе обойдённые вершины в порядке их обхода. При реализации этой функции использована *самописную* структуру данных **очередь**.
* Использованы *самописные* вспомогательные классы `Stack` и `Queue`.

## Part 2. Поиск кратчайших путей в графе.

* В классе `GraphAlgorithms`содержатся:
    + `getShortestPathBetweenVertices(Graph &graph, int vertex1, int vertex2)` - поиск кратчайшего пути между двумя вершинами в графе с использованием *алгоритма Дейкстры*. Функция принимает на вход номера двух вершин и возвращает численный результат, равный наименьшему расстоянию между ними.
    + `getShortestPathsBetweenAllVertices(Graph &graph)` - поиск кратчайших путей между всеми парами вершин в графе с использованием *алгоритма Флойда-Уоршелла*. В качестве результата функция возвращает матрицу кратчайших путей между всеми вершинами графа.

    + `getLeastSpanningTree(Graph &graph)` - поиск наименьшего остовного дерева в графе с помощью *алгоритма Прима*. В качестве результата функция должна возвращать матрицу смежности для минимального остовного дерева
    + `solveTravelingSalesmanProblem(Graph &graph)` - решение задачи коммивояжера с помощью *муравьиного алгоритма*. Необходимо найти самый выгодный (короткий) маршрут, проходящий через все вершины графа хотя бы по одному разу с последующим возвратом в исходную вершину. В качестве результата функция должна возвращать структуру `TsmResult`, описанную ниже:

    ```cpp
    struct TsmResult {
        int* vertices;    // массив с искомым маршрутом (с порядком обхода вершин). Вместо int* можно использовать std::vector<int>
        double distance;  // длина этого маршрута
    }
    ``` 

## Part 3. Консольный интерфейс

* Данный проект представляет собой программу - консольное приложение для проверки работоспособности реализованных библиотек s21_graph.h и s21_graph_algorithms.h
* Консольный интерфейс покрывает следующий функционал:
    1. загрузка исходного графа из файла
    2. обход графа в ширину с выводом результата обхода в консоль
    3. обход графа в глубину с выводом результата обхода в консоль
    4. поиск кратчайшего пути между произвольными двумя вершинами с выводом результата в консоль
    5. поиск кратчайших путей между всеми парами вершин в графе с выводом результирующей матрицы в консоль
    6. поиск минимального остовного дерева в графе с выводом результирующей матрицы смежности в консоль
    7. решение задачи комивояжера с выводом результирующего маршрута и его длины в консоль
