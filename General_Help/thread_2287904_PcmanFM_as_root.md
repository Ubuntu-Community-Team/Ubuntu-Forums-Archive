---
title: "PcmanFM as root?"
date: 2015-07-23
forum: General Help
---

### Post by flex567 on 2015-07-23
I have PcmanFM installed in Lubuntu. How can I now if I PcmanFM is opened as root? I can alter file permissions with it, does that mean that it is opened as root?

---

### Post by Bucky Ball on 2015-07-23
*Thread moved to **General Help**.*

It will look totally different and make you unmistakably aware that you are logged in as root. Unless you have logged in as root, this is unlikely. Yes, you can change permissions, but do they stick when you close and open the permissions again?

To open as root you would normally need to manually do via a terminal with 'gksudo pcmanfm'. You would then be asked for your password. If none of this has happened, doubtful you are root.

---

### Post by flex567 on 2015-07-23
I have gksudo pcmanfm but restarted computer after that. I jsut successfully altered permissions to a file, so that means it is sill opened as root. How can I make pcmanfm not have root privileges

---

### Post by sudodus on 2015-07-23
Unless you have changed something, pcmanfm is not run as root in Lubuntu. It is run 'as a standard user', with the same permissions as if you start it from a terminal window with the command

```
pcmanfm
```

If you want to check it you can create a file with higher permissions.

```

sudodus@ssd-grund ~ $ cd
sudodus@ssd-grund ~ $ sudo -s
[sudo] password for sudodus: 
root@ssd-grund ~ # echo 'Hello World'>hello.txt
root@ssd-grund ~ # exit   # from superuser
sudodus@ssd-grund ~ $ ls -l hello.txt
-rw-r--r-- 1 root root 12 jul 23 09:46 hello.txt

```

Now you can try to edit or delete that file via pcmanfm. If you double-click the file icon (for hello.txt), and try to edit it, you will find that it is read-only, because only the owner root is allowed to write to it. It is possible to delete the file, and I think it is because it is stored in a directory owned by you (your own home directory), where you are allowed to delete files.

If you have a file in root's home directory it will be different.

```

sudodus@ssd-grund ~ $ cd /root
sudodus@ssd-grund /root $ sudo -s
[sudo] password for sudodus: 
root@ssd-grund /root # echo 'Hello World'>hello.txt
root@ssd-grund /root # exit   # from superuser
sudodus@ssd-grund /root $ ls -l hello.txt
-rw-r--r-- 1 root root 12 jul 23 09:58 hello.txt

```

Now you cannot delete the file via pcmanfm, and this shows definitely that you are not running pcmanfm as root.

---

### Post by sudodus on 2015-07-23
> **flex567 said:**
> I have gksudo pcmanfm but restarted computer after that. I jsut successfully altered permissions to a file, so that means it is sill opened as root. How can I make pcmanfm not have root privileges

pcmanfm has root privileges ***only*** when launched via ```
gksudo pcmanfm
``` and I suggest that you avoid running it like that, because you might forget the elevated permissions and damage your system by mistake. Instead it is better to use command line tools and use sudo, when elevated permissions are necessary. For example use

```
chmod ...
``` in order to change the permissions for a file or group of files, that you own, and
```
sudo chmod ...
``` in order to change the permissions for a file or group of files, that is owned by someone else, for example root.

---

### Post by flex567 on 2015-07-23
I cannot even enter the file /root via pcmanfm. So if I can alter permissions via pcmanfm that doesn't mean that I am running it as root.

---

### Post by sudodus on 2015-07-23
You can alter permissions of ***your own files*** via pcmanfm as well as with chmod (without gksudo or sudo).

---

### Post by flex567 on 2015-07-24
there is also "!" sing on the left side to know that is open as root

---

