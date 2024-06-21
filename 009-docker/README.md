# Домашнее задание к занятию «2.4 Docker, установка и настройка»

## Задание 1 - Docker CLI
1. Загрузите образ `busybox` последней версии - `docker pull busybox`
1. Запустите новый контейнер `busybox` с командой `ping` сайта `netology.ru`, и количеством пингов 7, поименуйте контейнер `pinger` - `docker run --name pinger -i -t busybox ping -c 7 netology.ru`
1. Выведите на список всех контейнеров - запущенных и остановленных - `docker ps -a`
1. Выведите на экран логи контейнера с именем `pinger` - `docker logs -t pinger`
1. Запустите второй раз контейнера с именем `pinger` - `docker start pinger`
1. Выведите на список всех контейнеров - запущенных и остановленных - `docker ps -a`
1. Выведите на экран логи контейнера с именем `pinger` - ```docker logs -t pinger```
1. Определите по логам общее количество запусков команды `ping` и какое общее количество отправленых запросов - ` 2 раза по 7 в каждом `
1. Удалите контейнер с именем `pinger` - `docker rm pinger`
1. Удалите образ `busybox` - `docker rmi -f busybox`

## Задание 2 - Environment Variables

Используя Docker CLI выполните следующие действия:
1. Загрузите образ node версии 15.14 - `docker pull node:18`
1. Запустите контейнер node в интерактивном режиме подключения терминала, поименуйте его `mynode`, передайте две переменные среды `NAME=<ваше имя>` и `SURNAME=<ваша фамилия>` - `docker run --name mynode -e NAME=Antom -e SURNAME=Golikov -i -t node:18`
1. В интерактивной среде выполнения node выполните скрипт, который выведет на экран приветсвтие: `Привет, <ваше имя> <ваша фамилия>!`, эти данные должны быть получены из переменных среды - ``console.log(`Привет, меня зову ${process.env.NAME} ${process.env.SURNAME}`)``
1. Остановите контейнер - `docker stop mynode`
1. Удалите образ node версии 15.14 - `docker rmi node:18`

## Задание 3 - Volumes

Используя Docker CLI выполните следующие действия:
1. Загрузите образ node версии 15.14 - `docker pull node:18`
1. Запустите контейнер с именем `first_node` из образа node версии 15.14 в фоновом режиме, подключив папку `data` из текущей директории в `/var/first/data` контейнера - `docker run -d --name first_node -v /:/var/first/data node:18`
1. Запустите контейнер с именем `second_node` из образа node версии 15.14 в фоновом режиме, подключив папку `data` из текущей директории в `/var/second/data` контейнера - `docker run -d --name second_node -v /:/var/second/data node:18`
1. Подключитесь к контейнеру `first_node` с помощью exec и создайте текстовый файл любого содержания в `/var/first/data` - `docker exec first_node touch /var/first/data/text.txt`
1. Добавьте еще один файл в папку `data` на хостовой машине
1. Подключитесь к контейнеру `second_node` с помощью `exec` и получите список файлов в директории `/var/second/data`, выведете на экран содержимое файлов - `docker exec second_node ls /var/second/data`
1. Остановите оба контейнера - `docker stop first_node second_node`
1. Удалите оба контейнера - `docker rm first_node second_node`
1. Удалите образ node версии 15.14 - `docker rmi node:18`
