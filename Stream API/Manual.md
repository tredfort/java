## Основные определения.
В языке **Java** есть понятие потоков, но ни классы **InputStream** (поток ввода) и **OutputStream** (поток вывода),
ни **Thread** (поток исполнения) не имеют ничего общего с новшеством **Java 8** — **Stream API**. **Stream API**
работает не с потоком в прямом смысле слова, а с цепочкой функций, вызываемых из самих себя. Он обеспечивает
функциональное программирование в **Java 8**. Поток — это последовательность элементов и функций, которые поддерживают
различные виды операций.

В **примере 2** с помощью **Stream API** мы можем в одну строку решить такую задачу: из списка сотрудников, выбрать
только инженеров, затем отсортировать их в порядке увеличения возрастов, получить имена этих сотрудников в том же 
порядке и сохранить их в коллекцию **List<String>**. Операции со стримами могут относиться к терминальным или 
промежуточным. Все промежуточные операции возвращают модифицированный стрим, так что их можно объединять. Терминальные
операции возвращают либо результат, не относящийся к стриму, либо ничего (**void**). В приведённом листинге
**filter()**, **map()** и **sorted()** — промежуточные операции. А **collect()** — терминальная операция и может
возвращать коллекцию. Полный список таких операций доступен в **JavaDoc** к **Java 8** или
[тут](https://habr.com/ru/company/luxoft/blog/270383/). Большинство операций стрима могут принимать лямбда-выражения.

### Способы создания и виды стримов
* Стримы создаются из различных источников данных, но в большинстве случаев — из коллекций **List** и **Set** с помощью
метода **stream()** **пример 3**.
* Для создания стрима, состоящего из произвольного набора элементов, можно использовать статический метод **Stream.of()**
**пример 4**.
* Чтобы создать стрим из существующего массива, можно воспользоваться статическим методом
класса Arrays.stream() или передать массив в качестве аргумента методу Stream.of():