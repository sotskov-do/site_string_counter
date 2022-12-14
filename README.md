Консольное приложение, которое принимает в качестве параметра список URL страниц. И выводит общее кол-во строк на странице, включая теги head, script и т.д.

Пример (кол-во строк в примере произвольное):

```
> myApp "ya.ru, google.com, mts.ru"
> processing...
> ya.ru: 234
> google.com: 123
> mts.ru: 345
```

Особенности реализации:
* все запросы на получение страниц должны выполняться параллельно. Максимум 4 запроса одновременно
* при нажатии Ctrl-C приложение должно остановить обработку запросов и вывести для каждой необработанной страницы в качестве результата cancel
* кол-во строк на страницах должно выводится в том же порядке, что и в параметре команды
* в случае ошибки получения страницы должен выводится код http ответа, не нарушая при этом порядок страниц

Пример команды для запуска:

```
go run cmd/main.go "ya.ru, google.com, mts.ru, stepik.org, mail.ru, mts.ru/personal/gdfgdfhtfdbht, dghfshgfhf.com"
```