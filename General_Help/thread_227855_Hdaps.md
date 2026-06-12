---
title: "Hdaps"
date: 2006-08-02
forum: General Help
---

### Post by buttari on 2006-08-02
Hi all,
I have a Thinkpad T60P laptop and I would like to use HDAPS. For the moment I just want to play with this:

[http://www-128.ibm.com/developerworks/linux/library/l-knockage.html?ca=dgr-lnxw01Knock-Knock]("http://www-128.ibm.com/developerworks/linux/library/l-knockage.html?ca=dgr-lnxw01Knock-Knock")

Unfortunately I have problems using the hdaps module:

```

[~]$ sudo modprobe hdaps
FATAL: Error inserting hdaps (/lib/modules/2.6.15-26-686/kernel/drivers/hwmon/hdaps.ko): No such device or address

```
The /lib/modules/2.6.15-26-686/kernel/drivers/hwmon/hdaps.ko module is at its place.
Is there anybody that can help me?
Thanks

alfredo

---

### Post by buttari on 2006-08-03
I found the problem by myself:
the thinkpad T60P is not supported by the 2.6.15 kernel.

alfredo

---

### Post by dizzy1234 on 2006-08-16
Hi

I'm getting a similar error on a Thinkpad X60 - is there any way to overcome this... I want to play with the knock-knock thing too!

---

### Post by buttari on 2006-08-16
> **dizzy1234 said:**
> Hi

I'm getting a similar error on a Thinkpad X60 - is there any way to overcome this... I want to play with the knock-knock thing too!

As far as I know, the only way to enable it on my laptop, is to compile by myself the 2.6.17 linux kernel. I'm not sure about the X60 but it should me the same.
Alfredo

---

### Post by Mihelog on 2006-10-24
What kernel version does the queuefreeze patch cleanly apply to? I patched 2.16.28 but the computer freezes when hdapsd stops the hdd. I am not sure if hdapsd doesn't bring the hdd back, but i think it's a kernel crash because *everything* freezes.

---

### Post by dawm on 2007-04-25
works flawlessly on my R52 w/ feisty

---

### Post by holihue on 2007-06-29
I have the same problem with my R60

---

### Post by lycopenehead on 2008-06-28
i have  a similar problem with x40,but when i typed the command in the console it got nothing


ale@adam:~$ sudo modprobe hdaps
ale@adam:~$ sudo modprobe hdaps
ale@adam:~$


any 1 can help for the rest of the process

---

