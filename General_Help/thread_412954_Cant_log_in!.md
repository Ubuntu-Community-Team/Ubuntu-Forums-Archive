---
title: "Cant log in!"
date: 2007-04-18
forum: General Help
---

### Post by humkar on 2007-04-18
Hi guys,

I should start by clarifying I'm a newbie to Ubuntu but i LOVE it. :) Ii did do searches but couldn't find anything on the forums. but my problem is as follows:

I cant log into my account because I get the following error message as shown in the picture below: 





I would appreciate it if someone can give me an insight into how I can get around this

---

### Post by taurus on 2007-04-18
Press <Ctrl><Alt>F2 and see if you can log in with your name and password.  Then, post the output of this command here.

```
df -h
```

You could be running out of disk space!

p.s.  Are you running Dapper or Edgy (or even Feisty)?

---

### Post by floke on 2007-04-18
can you log in at the terminal?

press ctrl-alt-F1 /f2 / F3 etc. and login there?

* Pah! Taurus beat me to it *

---

### Post by humkar on 2007-04-18
Sorry I should have said i'm running Dapper. No I aint running out of disk space. I've got 22+gig spare. 



I can log in via a failsafe session but not through my normal session. 



I can log in via login terminal. But i don't know many commands so cant do much else.





thanx for the quick reply


```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              34G  2.3G   30G   8% /
varrun                506M   88K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  487M   4% /lib/modules/2.6.15-28-386/volatile
/dev/sdb              999M  178M  821M  18% /media/usbdisk

```

---

### Post by taurus on 2007-04-18
What's the output of this command then?

```
ls -la /etc/profile
```

---

### Post by humkar on 2007-04-18
i've logged into the failsafe session and entered the above command in terminal.

i got the following output

```
-rw------- 1 root root 368 2007-04-16 15:52 /etc/profile

```

thanx again

---

### Post by taurus on 2007-04-18
It should be

```
-rw-r--r-- 1 root root 369 2006-10-28 09:39 /etc/profile
```
So, change the permission of that file with

```
sudo chmod 644 /etc/profile
```
Reboot and see if you can log in now.

---

### Post by humkar on 2007-04-18
That worked a treat. thats fantastic mate.

thanx for all you help :)

---

