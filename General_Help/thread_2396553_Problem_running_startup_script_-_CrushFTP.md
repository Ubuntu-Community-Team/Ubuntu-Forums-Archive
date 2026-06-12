---
title: "Problem running startup script - CrushFTP"
date: 2018-07-17
forum: General Help
---

### Post by stormnet2 on 2018-07-17
I am sure i'm overlooking something VERY obvious. So i'm installing CrushFTP on box running Ubuntu Server 18.04 LTS. Everything is fine, until i need to start the webserver to run CrushFTP.

The file i need to run is: **crushftp_init.sh** but i when i go to run it (*crushftp_init.sh start*)i get the following error:

*crushftp_init.sh: command not found*

I thought maybe i just need to raise the permission, so i tried **sudo**, but even that gives me an error:

*sudo: crushftp_init.sh: command not found*

Its been a while since i've ran linux on a daily basis, so i am very rusty. I am begining to think that it might be related to my permission level. The file list looks like this:

```
drwxr-xr-x  5 root root    4096 Jul 17 19:20 .
drwxr-xr-x  3 root root    4096 Jul 17 19:20 ..
-rw-r--r--  1 root root   29184 Jul  4  2016 CrushFTP.exe
-rw-r--r--  1 root root   13450 Apr 13 15:42 crushftp_init.sh
-rw-r--r--  1 root root 5970248 Jul  9 14:09 CrushFTP.jar
drwxr-xr-x  3 root root    4096 Jul 17 19:20 plugins
drwxr-xr-x  3 root root    4096 Jul 17 19:20 users
drwxr-xr-x 19 root root    4096 Jul 17 19:20 WebInterface

```

The account i'm using is not root, but it does have the permission to use sudo when necessary. I know i'm missing something simple as to why i cant run the script, but for the life of me, i cant see my mistake. Any suggestion of what I should be doing to run the script?

Thanks.

---

### Post by steeldriver on 2018-07-17
Hello and welcome to the forums

By default, the current directory is not in either your PATH or the sudo `secure_path` - if you want to run a file that is in the current directory you need to add a path explicitly

```

./crushftp_init.sh start

```
or
```

sudo ./crushftp_init.sh start

```

---

### Post by stormnet2 on 2018-07-17
Thank you for the response. 

I had tried both of those and got this:

```
username@server2:/var/opt/CrushFTP8_PC$ sudo ./crushftp_init.sh start
[sudo] password for username:
sudo: ./crushftp_init.sh: command not found

```

that is why i am thinking im missing something simple. I did notice that Tab completion is not working with this file. Even if i put the ./c nothing from the directory auto completes or prompts me to pic one.

---

### Post by Holger_Gehrke on 2018-07-17
Your script is missing something - the executable bit. You can either start it like this```
sh /var/opt/CrushFTP8_PC/crushftp_init.sh
``` or you can set the executable bit```
chmod a+x /var/opt/CrushFTP8_PC/crushftp_init.sh
``` to make it executable for all or replace the a in that command with one of u,g or o for user, group or others.

Holger

---

### Post by stormnet2 on 2018-07-18
The executable bit.... yup. That did it.

Is there a reason you have to have the full path when trying to run it, or is it to make sure you REALLY want to run the script?

---

