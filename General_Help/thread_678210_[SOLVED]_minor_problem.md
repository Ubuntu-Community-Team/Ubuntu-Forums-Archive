---
title: "[SOLVED] minor problem"
date: 2008-01-25
forum: General Help
---

### Post by Sammael5 on 2008-01-25
I have a 500 gb xternal western digital HD... it will not mount.  suggestions?

---

### Post by PinkFloyd102489 on 2008-01-25
What did you do to try and mount it?

---

### Post by Sammael5 on 2008-01-25
plugged it in... im sorta a newb generally works

---

### Post by PinkFloyd102489 on 2008-01-25
Generally, external hard drives wont automount.


You need to make a directory in /media or /mnt to do this. So here's the codes you need to enter. Open a terminal to enter these:

```

sudo mkdir /media/INSERTNAMEHERE    *You can name it whatever you want*

sudo mount -t vfat /dev/sda /media/INSERTNAMEHERE

```


And so that you dont have to do it again in the future, do this:

```

gksudo gedit /etc/fstab

```


Add this to the end of the file:

```

/dev/sda /media/INSERTNAMEHERE  vfat  user,auto 0 0

```



If you get confused with anything, you can contact me on AIM if you wish.

---

### Post by Sammael5 on 2008-01-25
mine usually does... anyway... how should i go about this?

---

### Post by Sammael5 on 2008-01-25
sammael@addonis:~$ sudo mount -t vfat /dev/sda /media/xternal
mount: special device /dev/sda does not exist

---

### Post by Jelmoh on 2008-01-25
Check your other post, a detailed explanation of your problem with a solution.. :)
[Ubuntu Forums: Minor Problem](http://ubuntuforums.org/showthread.php?t=678195)

Good luck! ;)

---

### Post by Jelmoh on 2008-01-25
There should be a number after sda (/dev/sda#), depending on which device number the hard drive has! :)
I don't know exactly how to find that out, but that's all in the solutions I gave you! :)

Good luck

---

