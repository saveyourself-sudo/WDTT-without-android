# WDTT without Android

Установка **WDTT VPN Server** напрямую на VPS без использования Android-устройства.

Скрипт автоматически:

* Обновит систему
* скачивает официальный APK WDTT;
* извлекает серверный бинарник;
* устанавливает зависимости;
* настраивает systemd-сервис;
* открывает необходимые порты;
* запускает сервер автоматически после перезагрузки VPS.

---

## Поддерживаемые системы
* Ubuntu 24.04+ 

## Требования
* Чистый сервер
---

## Быстрый запуск

Выполните на сервере:

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/saveyourself-sudo/WDTT-without-android/main/install-wdtt.sh)
```

Во время установки будет предложено указать:

* Пароль VPN (по умолчанию: `000`)
* Telegram Bot Token (необязательно)
* Telegram Admin ID (необязательно)
* DTLS порт (по умолчанию: `56000`)
* WireGuard порт (по умолчанию: `56001`)

Если просто нажимать Enter, будут использованы значения по умолчанию.

---

## Проверка работы сервера

Проверить статус службы:

```bash
systemctl status wdtt
```

Проверить открытые порты:

```bash
ss -lunp | grep -E '56000|56001'
```

Просмотр логов:

```bash
journalctl -u wdtt -f
```

---

## Расположение файлов

Конфигурация:

```text
/etc/wdtt
```

Бинарный файл сервера:

```text
/usr/local/bin/wdtt-server
```

Systemd-сервис:

```text
/etc/systemd/system/wdtt.service
```

---

## Управление сервисом

Перезапуск:

```bash
systemctl restart wdtt
```

Остановка:

```bash
systemctl stop wdtt
```

Запуск:

```bash
systemctl start wdtt
```

Автозапуск:

```bash
systemctl enable wdtt
```

---

## Удаление

Повторно запустите скрипт и выбрать пунк 2:

## Используемые порты

По умолчанию:

| Сервис    | Порт      |
| --------- | --------- |
| DTLS      | 56000/UDP |
| WireGuard | 56001/UDP |

Во время установки порты можно изменить.

---

## Примечание

Данный проект является неофициальным установщиком WDTT для VPS.

Все права на WDTT принадлежат его оригинальным разработчикам.
https://github.com/amurcanov/proxy-turn-vk-android
