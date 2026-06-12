---
title: "Jailing user the right way"
date: 2015-06-16
forum: General Help
---

### Post by Dmitry_Samokhin_Ic on 2015-06-16
Hello everyone. These may be a dumb question for most of you but i would like to know how to jail user the right way.

I would like to create a virtual host for my LAMP stack on VPS and give it to someone else.

Now i locked user in FTP and restricted SSH login only to localhost so that he can not login using ssh but he can still use FTP.
As he will be allowed to use PHP he can access any directory that has read rights for everyone/others. I would like to disallow him going anywhere higher than his home directory. What would be the right way of doing it? I guess its jailing him by using shell but im a casual user that just runs VPS with web host and few other things for personal use. As im the only one that uses VPS security is not a problem but now it becomes a challenge and i would like to learn about it, and if possible how to do it the right way without learning it by making mistakes...

If you could provide some step by step tutorial or send some good articles for noob's i would appreciate it. Thx in advance.

---

### Post by raja.genupula on 2015-06-16
we got good reference for you 
[http://unix.stackexchange.com/questions/94603/limit-ftp-access-only-to-the-var-www-with-vsftpd](http://unix.stackexchange.com/questions/94603/limit-ftp-access-only-to-the-var-www-with-vsftpd)

just adapt the process.

---

### Post by Dmitry_Samokhin_Ic on 2015-06-16
Well i did lock user using FPT. Thing is PHP has functions like fopen and fread that seems harmless but they are expecting path and if user use ../../../  (you get it) he can read files from root. Maybe he cant modify them but he can read them and that is very big security risk.

---

