# Бот для проведения викторины. Для Telegram и VK
Учебный проект по урокам https://dvmn.org/

## 📌 О проекте
Чат-бот с каверзными вопросами и единственным правильным вариантом ответа.   

#### Пример Telegram бота https://t.me/dvmn_quiz_89487u38u89y_bot 
![Telegram Bot GIF](https://dvmn.org/filer/canonical/1569215494/324/)

#### Пример VK чата: 
![VK Bot GIF](https://dvmn.org/filer/canonical/1569215498/325/)


## ⚙️ Предварительно
1. Создайте бота в **Telegram**
2. Создайте группу в **VK**

## 📜 Переменные окружения
`TELEGRAM_BOT_TOKEN` - секретный ключ вашего телеграмм бота  
`TELEGRAM_ADMIN_CHAT_ID` - chat_id администратора. Чтобы получить свой chat_id, напишите в Telegram специальному боту: @userinfobot  
`VK_GROUP_TOKEN` - токен группы в VK

## 💿 Установка проекта

### Способ 1 (virtualenv):
1. Создайте виртуальное окружение `python -m venv venv_quiz_bot`  
2. Зайдите в директорию виртуального окружения `cd venv_quiz_bot`  
3. Скачайте репозиторий `git clone git@github.com:val-os/quiz_bot.git`  
4. Пройдите в директорию репозитория `cd quiz_bots`  
5. Cоздайте файл `cp env.example .env` (на одном уровне с `env.example`)
6. Присвойте значения всем переменным в файле `.env`
7. Активируйте виртуальное окружение `source ../bin/activate`
7. Установите зависимости `pip install -r requirements.txt`
   
### Способ 2 (Poetry):
1. Скачайте репозиторий `git clone git@github.com:val-os/quiz_bot.git`  
2. Пройдите в директорию репозитория `cd quiz_bots`
3. Установите нужные зависимости `poetry install`
4. Активируйте виртуальное окружение `poetry shell`

## 🚀 Запуск проекта
1. Запустите ботов:
   ```sh
   python ./quiz_bots/tg_bot.py
   python ./quiz_bots/vk_bot.py
   ```


## 🤯 Возможные проблемы
- **vk_api: [901] Can't send messages for users without permission:** Зайти в группу, справа в шапке нажать "Ещё". Выбрать "Разрешить сообщения"


## 🤖 Запуск проекта в качестве сервиса Linux
В примере ниже используется редактор кода `vim`, который можно заменить на `nano`
Предпологается, что путь к виртуальному окружению `/opt/venv_quiz_bot/`
Вам нужно создать два файла `tg_quiz_bot.service` и `vk_quiz_bot.service`

### Создание и запуск сервиса для бота Telegram
1. `vim /etc/systemd/system/tg_quiz_bot.service`
2. ```editorconfig
   [Unit]
   Description=Quiz Telegram Bot
   After=multi-user.target

   [Service]
   Type=simple
   Restart=always
   ExecStart=/opt/venv_quiz_bot/bin/python3 /opt/venv_quiz_bot/quiz_bots/bots/tg_bot.py

   [Install]
   WantedBy=multi-user.target
   ```
3. `sudo systemctl daemon-reload`
4. `systemctl enable tg_quiz_bot.service`
5. `systemctl start tg_quiz_bot.service`


### Создание и запуск сервиса для бота VK
1. `vim /etc/systemd/system/vk_quiz_bot.service`
2. ```editorconfig
   [Unit]
   Description=Quiz VK Bot
   After=multi-user.target

   [Service]
   Type=simple
   Restart=always
   ExecStart=/opt/venv_quiz_bot/bin/python3 /opt/venv_quiz_bot/quiz_bots/bots/vk_bot.py

   [Install]
   WantedBy=multi-user.target
   ```
3. `sudo systemctl daemon-reload`
4. `systemctl enable vk_quiz_bot.service`
5. `systemctl start vk_quiz_bot.service`


## 🎯 Цели проекта
Код написан в учебных целях — это урок в курсе по Python и веб-разработке на сайте [Devman](https://dvmn.org).
