---
title: "Problem with mysql"
date: 2020-07-10
forum: General Help
---

### Post by programercek on 2020-07-10
hello,

Hello,


I can't found any resolved question for my problem.


After restart linux and today I want to check mysql I can't because I got:
root@mail:~# sudo /etc/init.d/mysql start
Starting mysql (via systemctl): mysql.serviceJob for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.


I tried a lot of different options but it's the same.

Please help

---

### Post by dragonfly41 on 2020-07-10
The idea is that you now run the command

systemctl status mysql.service

to get more clues.[FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT]

---

