# API для проекта Yatube. ![YaMDB](https://github.com/pichugina-v/yamdb_final/actions/workflows/main.yml/badge.svg)

Проект API YaMDB - хранилище отзывов пользователей о произведениях в категориях "Музыка", "Книги", "Фильмы". Список категорий может быть расширен администратором. 

В каждой категории представлены произведения, права на добавление новых произведений есть только у администратора. 

При добавлении нового проиведения администратор может выбрать категорию и жанр из предустановленных. Права на расширение списка категорий и жанров есть только у администратора. 

Пользователи могут оставлять отзывы с оценками (от 1 до 10) и комментарии на произведения. На одно произведение пользователь может оставить только один отзыв. Произведению присваивается рейтинг - усредненная оценка, сформированная на основе всех оценок пользователей.

# Установка на локальном компьютере:

## Начало работы:

* Клонируйте репозиторий `yamdb_final`
```bash
git clone https://github.com/pichugina-v/yamdb_final.git
```

* В корневой директории проекта создайте файл `.env` и заполните переменные окружения
```python
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=<логин для подключения к базе данных>
POSTGRES_PASSWORD=<пароль для подключения к базе данных>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=<секретный ключ Django>
```

* Запустите docker-compose командой 
```bash
docker-compose up -d --build
```

* Примените миграции
```bash
docker-compose exec web python manage.py makemigrations --noinput
docker-compose exec web python manage.py migrate --noinput
```

* Создайте пользователя с правами администратора
```bash
docker-compose exec web python manage.py createsuperuser
```

* Соберите статику
```bash
docker-compose exec web python manage.py collectstatic --no-input
```

* Загрузите начальные данные в базу данных
```bash
docker-compose exec web python manage.py loaddata fixtures.json
```

Все запросы к API начинаются с `/api/v1/`

Для входа в панель администратора необходимо перейти по адресу `http://127.0.0.1/admin/`

Документация к проекту доступна по адресу `http://127.0.0.1/redoc/`

Проект доступен по ссылке: `http://62.84.114.36/api/v1/`