---
title: "Similar installation,"
date: 2005-07-30
forum: General Help
---

### Post by geearf on 2005-07-30
Hello,

I have (k)ubuntu installed on my desktop and i am very happy with it, and i'd like to install it also on my laptop.

But i don't want to install all i need again (well not much, but still tiresome ...).

I was thinking of making a tar of / and another one of /home and then use it on my laptop. But my laptop is a centrino, and my desktop an old athlon, I worry there will be some trouble there.

What is the best to do so please ?

thanks,

---

### Post by jasmuz on 2005-07-30
If i were you i would make a copy of my /var/cache/apt/archives (that is where apt stores all the deb's it has downloaded for installs. And copy your home dir.

Do a normal install on the laptop and copy both directories to the machine, so when you run a install on the programs you need there is no downloading involved, quick as heck!.

Hope this helps.

---

### Post by az on 2005-07-30
When you untar your system to the root partition, you will have to chroot into it to install the bootloader.  Make sure you boot into the 386 kernel by default.  You didn't remove the 386 kernel when you installed the k7 kernel, did you?

---

### Post by geearf on 2005-07-31
Hello,

@jasmuz : I of course did a lot of apt-get clean, so it should not be possible to do so (and also it would not have the config of other stuff like also for exemple).

@azz : Well I was thinking of doing that after installing ubuntu, I mean, it's not that long, and with it i can make new partitions, grub and so on .. (/boot is on anoter partition on my desktop).

But of course I did not keep the 386 :D


Thanks,

---

### Post by geearf on 2005-08-01
\\:d/

---

### Post by geearf on 2005-08-01
up

---

### Post by geearf on 2005-08-05
Hello,

Ubuntu is finaly installed on the desktop, tonight if no other ideas come to my mind, I may do a stage 4 and just tar my / of my desktop, and untar it in my laptop.

Also is there any 'good' way to copy only system files from my /home, cause I have a lot of stuff in there I don't need in my laptop.

Thanks,

---

### Post by geearf on 2005-08-07
Well finally i've use dpkg --get-selection and set and it seems the best I could do

---

