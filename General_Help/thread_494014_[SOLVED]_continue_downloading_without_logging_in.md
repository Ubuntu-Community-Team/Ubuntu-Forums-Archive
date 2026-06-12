---
title: "[SOLVED] continue downloading without logging in"
date: 2007-07-06
forum: General Help
---

### Post by delfick on 2007-07-06
hello

i was wondering....

i've found out i can make my computer start itself, which means i could start it at a particular time so it can continue downloading large files....

but that would mean i'd have to make it automatically log in which i don't want to do....

is there a way to make the computer continue downloading particular files without having to have it log in ?? 

thnx

---

### Post by Rui Pais on 2007-07-06
hi,
maybe with a cron job owned by root... 
if you use wget with -c flag it will take the download and continued from where it ended, independent of who started or who owned.

---

### Post by delfick on 2007-07-06
cool :D

what about bittorrent files ??

also, do you know of a decent place to figure out how to use cron ?? :D

thnx

---

### Post by Rui Pais on 2007-07-07
> **delfick said:**
> cool :D

what about bittorrent files ??

also, do you know of a decent place to figure out how to use cron ?? :D

thnx

hi,
about bittorrent i don't know... i used only once a long time ago and don't remember how or what i done the torrent download (i make my installations with mini.iso or any minimal cd a distro have, and other then that i never download big files...)
But if you use bittorrent using some kind of line command or a automatic GUI (that work without any assistance, as son as launched) it's just pass that command or app on cron task, i think.

to use cron tab you must edit with -e flag and with sudo to belong to root:
```
sudo crontab -e
```
and something like:
```
0 3 * * * cd downloads/; wget -c http://mirrors.gigenet.com/ubuntu/7.04/ubuntu-7.04-desktop-amd64.iso
```
that one will download or complete download that file on downloads/ folder at 3:00.
Of course if your box boot automatically at a certain hour you can simply add the commands, temporarily, to /etc/rc.local...

Her some sites about cron formats:
[http://www.nncron.ru/help/EN/working/cron-format.htm](http://www.nncron.ru/help/EN/working/cron-format.htm)
[http://mkaz.com/ref/unix_cron.html](http://mkaz.com/ref/unix_cron.html)
[http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)

A nice and easier way to add/edit them is use some gui, like gnome-schedule (in repos) or kcron (not sure about the name) for kde.

hth

---

### Post by delfick on 2007-07-07
cool :D

thankyou very much :D

---

