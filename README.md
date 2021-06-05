# SkillFactory: DEVOPS. Практикум. Модуль 23.5

## Задание 23.5.1

1) Напишите плейбук, который будет на удаленной системе создавать пользователя user1 и задавать ему SSH-ключ (создавая заданный ключ в /home/user1/.ssh/id_rsa.pub). Ключ не должен передаваться в открытом виде. Используйте для шифрования ключа ansible-vault/.
1) Создайте плейбук, который устанавливает, либо удаляет почтовый сервер postfix в зависимости от тега.

## Решение

Для создания пользователя и копирования ключей необходимо использовать команду
ansible-playbook playbook_user.yml -i inventory.yml --ask-vault-pass
При этом копируется не только id_rsa.pub, но и id_rsa (закрытая часть ключа)

Для установки почтового сервера нужно выполнить команду
ansible-playbook playbook_postfix.yml -i inventory.yml -t postfix-init

Для удаления почтового сервера нужно использовать команду
ansible-playbook playbook_postfix.yml -i inventory.yml -t postfix-drop
