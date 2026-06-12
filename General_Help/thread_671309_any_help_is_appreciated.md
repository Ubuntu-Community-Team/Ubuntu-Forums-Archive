---
title: "any help is appreciated"
date: 2008-01-18
forum: General Help
---

### Post by ser1alsn1per on 2008-01-18
[root@vicidialnow ~]# [root@vicidialnow ~]# startx
-bash: [root@vicidialnow: command not found
[root@vicidialnow ~]# xauth:  creating new authority file /root/.serverauth.14339
-bash: xauth:: command not found
[root@vicidialnow ~]# xinit:  No such file or directory (errno 2):  no server "X" in PATH
-bash: syntax error near unexpected token `('
[root@vicidialnow ~]#
[root@vicidialnow ~]# Use the -- option, or make sure that /usr/bin is in your path and
-bash: Use: command not found
[root@vicidialnow ~]# that "X" is a program or a link to the right type of server
-bash: that: command not found
[root@vicidialnow ~]# for your display.  Possible server names include:
-bash: syntax error near unexpected token `display.'

    Xorg         X.Org displays
[root@vicidialnow ~]#
[root@vicidialnow ~]#     Xorg         X.Org displays

xinit:  Server error.
-bash: Xorg: command not found







does anyone know what this means or what comand I need to input to get this working 

Also this is based on centos and i know that this is a ubuntu forum which i also run its just a unix comand i need 

many thanks

---

### Post by lswest on 2008-01-18
well, looks to me like your x server isnt configured, have you tried running "sudo dpkg-reconfigure xserver-xorg --phigh" i think is the command, anyone realizes it's wrong, feel free to correct me:P and then try running either startx or xinit

---

