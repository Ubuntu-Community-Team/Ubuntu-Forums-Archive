---
title: "[SOLVED] unable to resolve host"
date: 2008-05-12
forum: General Help
---

### Post by vishzilla on 2008-05-12
when I try sudo to update or install any program i get this error
```
vishal@v-desk:~$ sudo apt-get update
sudo: unable to resolve host v-desk
```

Please help :confused:

---

### Post by Monicker on 2008-05-12
[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by forestpixie on 2008-05-12
Did this earlier for someone else

If the name of you pc is not the same in these two files you need to change one. Open a terminal run these commands separately -

cat /etc/hosts
cat /etc/hostname

For example these are mine

cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 kevin-desktop

cat /etc/hostname
kevin-desktop

If they are not the same you can try editing the file within ubuntu using gksudo instead of sudo with gedit

gksudo gedit /etc/hosts

If you are able to open the file with that command - edit it so that the names match in both files, then reboot

If you are not able to do that - reboot into recovery mode - you will end up at a command prompt. You can use nano to edit the file here, in nano to save changes Ctrl+O then enter, to exit Ctrl+X

nano /etc/hosts

make changes then Ctrl+O, enter, Ctrl+X

type reboot and then enter

---

### Post by forestpixie on 2008-05-12
Wish I'd seen the workaround earlier :)

---

### Post by vishzilla on 2008-05-13
I came across this problem before. I didn't pay attention as I was up the whole night and was tired. Thanks a lot guys

---

