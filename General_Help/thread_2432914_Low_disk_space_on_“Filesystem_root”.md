---
title: "Low disk space on “Filesystem root”"
date: 2019-12-10
forum: General Help
---

### Post by daniel-s19 on 2019-12-10
[COLOR=#141414][FONT=&amp]Hello,[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]I'm a new user of linux, i´ve using Ubuntu 18.04 for a month, and everything has been working properly, until now.[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]Currently, i'm trying to run a program using docker, and i have not been able to build it because everytime i try to run the command[/FONT][/COLOR]```
sudo docker build -t virmine .
```[COLOR=#141414][FONT=&amp] i get an error message that says: Low disk space on "Filesystem root" 0 bytes disk remaining.[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]I have already used the commands [/FONT][/COLOR]```
apt-get autoremove
```[COLOR=#141414][FONT=&amp] and [/FONT][/COLOR]```
apt-get autoclean
```[COLOR=#141414][FONT=&amp] but the error message kepps popping up.[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]I don´t know why this is happening, since the root partition has 11Gb available, as the GParted screenshot shows.

[/FONT][/COLOR][COLOR=#141414][FONT=&amp]When i do [/FONT][/COLOR]```
df -h
```[COLOR=#141414][FONT=&amp] i get what the second image shows. 

[/FONT][/COLOR][COLOR=#141414][FONT=&amp]I would really appreciate any help. Thank you.[/FONT][/COLOR][COLOR=#141414][FONT=&amp]

[/FONT][/COLOR][IMG]https://www.linux.org/threads/low-disk-space-on-%E2%80%9Cfilesystem-root%E2%80%9D.26392/#post-80804[/IMG]

---

### Post by SeijiSensei on 2019-12-11
Your docker is installed as a snap and has no free space (see the line for /dev/loop18 in the image above).  See if you can install a version from an ordinary .deb in the repositories. I never use snaps so I can't give you more advice than this.

---

### Post by daniel-s19 on 2019-12-11
Thanks for your reply SeijiSensei. I removed the docker installed as a snap and installed the version 19.03.5 from the official Docker repository. Now i don't have the /dev/loop18 line, but when i try to use the build command it keeps giving me the same error.

---

### Post by Frogs Hair on 2019-12-11
Closed per OP request.

---

