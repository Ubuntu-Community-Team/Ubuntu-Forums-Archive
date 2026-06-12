---
title: "Help... Ubuntu 7.10 stopped booting properly"
date: 2007-12-17
forum: General Help
---

### Post by trueblue55 on 2007-12-17
I'm a relative newbie to Linux, so please forgive me in advance.  

I have been using Ubuntu for about 2 months now on my laptop, using KDM as my GUI (i added that the day after first installing Ubuntu).

Yesterday i turn the laptop on as usual and it wont boot :(

It goes through the initial Kubuntu screen but before it gets to the login screen where i select my name/password etc it goes to a black screen with text and just stops there.

The screen says:

> [I]Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/b480c435-e2f7-4ca4-b49f-0e0542466994) = sda4(8,4)
kinit: trying to resume from /dev/disk/by-uuid/b480c435-e2f7-4ca4-b49f-0e0542466994
kinit: no resume image, doing normal boot...

ubuntu 7.10 selene2 ttyl

selene2 login:[/I]

If i type in my username and password and hit enter, it just logs me into what looks like a terminal interface

*> ie. sam@selene2:~$*

I want my laptop back :(  

Is there a way to fix this, whatever it might be?

---

### Post by napoleon3665 on 2007-12-17
hmmmm, i hav the same problem but slightly different, i dual booted vista and linux and i select linux from the grub loader and it says starting.... then next line says please wait.... then the screen stays black for a good 10 min and finally it boots up, but then i cant connect to my router. i dont no if these problems have nething to do with each other but when i got to connect to my router, it freezes solid. i havent got an answer to my posts yet but if i do ill let ya no.

---

### Post by trueblue55 on 2007-12-17
My laptop is a dual boot XP and ubuntu.  It was working perfect, so there's no reason that i can think of that it would crap out like this.

---

### Post by trueblue55 on 2007-12-18
Nobody?

---

### Post by shae on 2007-12-18
Try typing this after logging on:

```
sudo /etc/init.d/kdm start
```

---

### Post by shae on 2007-12-18
The rest of the instructions to fix it are rather tough but here it goes:

```
sudo fdisk -l | grep swap
```
Tells you where the swap partition is

```
sudo vol_id -u /dev/???
```
Where ??? is what your swap partition is.

```
sudo gedit /etc/initramfs-tools/conf.d/resume
```
and make sure the UUID is the same as what the previous command gave you.

```
sudo update-initramfs -u
```

I hope this helps.

---

### Post by eapache on 2007-12-18
Or as an alternative:```
startx
```or if that gives a permissions error then```
sudo startx
```

---

### Post by trueblue55 on 2007-12-19
I tried all that and still no luck.  I get a message saying "KDM is already running".

I'm going to download the latest live CD install and re-install the lot.  Might be less stressful that way.

---

### Post by diwas on 2007-12-20
May be this is because of the boot screen...well i dont know..iam not sure, but check usplash.conf. Set ur screen resolution to 1 step down of which you normally use ur PC in. Tell me if it helps.

---

### Post by jlh on 2007-12-31
I just posted this in another thread:

I am getting the same boot into the terminal described at the beginning of this post. I never installed a second monitor. This is a very recent development, suggesting to me that it may be linked to an update.

When I get the login prompt in the shell, if I wait, usually the login gui splash screen appears. Sometimes it takes my user name and password normally. Sometimes, it responds very sluggishly, and autocomplets a whole bunch of non-inputed characters (in the form of black dots) that fill the password screen. Then, of course, the log in fails. A second try usually works.

However, when I get past the login screens, half the time the computer hangs at the desktop. Nothing loads, and I see a beige screen. Control-Alt-Backspace sends me back to the login screens, and after one or two tries, the desktop boots the way it should.

All this is very recent - the past week or so.

---

