# модуль поиска подстроки в строке

В этом модуле предусмотрено:
1) чувствительность/нечувствительность к регистру
2) параметр отвечающий за поиск `k` первых вхождений
3) параметр отвечающий за поиск с начала/конца
4) поиск в файле

Использован алгоритм Рабина-Карпа

Алгоритм поиска реализован в модуле `kmp_search.py`.
Функция поиска с сигнатурой:

```python
search(string: str, sub_string: Union[str, list[str]],
	   case_sensitivity=False: bool,
	   method: str='first', count: Optional[int]=None) -> Optional[Union[tuple[int, ...], dict[str, tuple[int, ...]]]]
```

Описание аргументов:

- ```string```           - исходная строка
- ```sub_string```       - одна или несколько подстрок, которые необходимо найти
- ```case_sensitivity``` - флаг чувствительности к регистру
- ```method```           - метод поиска, возможные значения:<br>
						   ```'first'``` - поиск идет в прямом порядке<br>
						   ```'last'``` - поиск идет в обратном порядке<br>
- ```count```            - количество совпадений `k`, которые нужно найти


## Входные и выходные данные

Пример: <br>
Строка: ```ababbababa```<br>
Подстрока: ```aba```<br>
Результат: ```(0, 5, 7)```<br>

Строка: ```abc```<br>
Подстрока: ```aba```<br>
Результат: ```None```<br>

При поиске нескольких подстрок результат представлен в виде словаря:

Строка: ```ababbababa```<br>
Подстроки: ```aba```, ```bba```<br>
Результат: ```{'aba': (0, 5, 7), 'bba': (3, )}```<br>

## Возможные команды

1. Поиск одной подстроки в строке:

```bash
python search.py -string "Строка для поиска" -substr "для"
```

2. Поиск нескольких подстрок в строке:

```bash
python search.py -string "Строка для поиска" -substr "для" "поиска"
```

3. Поиск нескольких подстрок в файле:

```bash
python search.py -file_path "search.py" -substr "def" "time"
```

4. Поиск с учетом регистра:

```bash
python search.py -string "Строка для поиска" -substr "Для" -case_sensitivity True
```

5. Поиск с ограничением на количество вхождений:

```bash
python search.py -string "Строка для поиска строка" -substr "строка" -count 2
```

6. Измерение времени выполнения:

```bash
python search.py -string "Длинная строка для поиска" -substr "строка" "поиска" -case_sensitivity True
```

7. Поиск с использованием направления:

```bash
python search.py -string "Это строка для поиска  строка" -substr "строка" -method "last"
```