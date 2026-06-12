---
title: "Need /usr/sbin"
date: 2007-03-31
forum: General Help
---

### Post by FlyingIsFun1217 on 2007-03-31
Whoops!

Seems I deleted my /usr/sbin! Of course, on accident. How stupid though.

What I am asking is if there is someone out there that wouldn't mind sending it to me somehow. It's kinda imperative that I have it, because without, I can't install anything (among other things I am sure).

I would most definitely appreciate it if you could send that over to me :) And if possible, on a newly installed system.

Thanks again!
FlyingIsFun1217

---

### Post by kellemes on 2007-03-31
There will be a lot more you can't do anymore.. especially in administering of the system.
I really don't know how you can fix this.. except for reinstall obviously.

Root is dangerous right? ;-)

---

### Post by kerry_s on 2007-03-31
Use the live cd, just boot the live cd and copy the /sbin over to your hard drive.

---

### Post by FlyingIsFun1217 on 2007-03-31
> **kellemes said:**
> 
Root is dangerous right? ;-)


To say the least :P
Ill try reinstalling it off of the cd, or something...

FlyingIsFun1217

---

### Post by thelinuxguy on 2007-03-31
> **FlyingIsFun1217 said:**
> 
What I am asking is if there is someone out there that wouldn't mind sending it to me somehow. 

I don't know how much trouble this can save you but here it is: [http://rapidshare.com/files/23713698/sbin.zip.html](http://rapidshare.com/files/23713698/sbin.zip.html)

---

### Post by FlyingIsFun1217 on 2007-03-31
I just wanna cry...

I restarted using the liveCD thinking that I could just save /usr/sbin to my flash drive, and then boot back into ubuntu and transfer the files over.

Now when I try and boot back into Ubuntu, I just get recovery mode!

How can I get the normal gnome desktop back? And if I can't, how can I just wipe out all of Ubuntu so that I can reinstall it?

Thanks again!
FlyingIsFun1217

---

### Post by dreadlord_chris on 2007-03-31
> **FlyingIsFun1217 said:**
> I just wanna cry...

I restarted using the liveCD thinking that I could just save /usr/sbin to my flash drive, and then boot back into ubuntu and transfer the files over.

Now when I try and boot back into Ubuntu, I just get recovery mode!

How can I get the normal gnome desktop back? And if I can't, how can I just wipe out all of Ubuntu so that I can reinstall it?

Thanks again!
FlyingIsFun1217

1. boot into recovery mode
2. stick the LiveCD in and mount it
3. copy /usr/sbin from the CD to your installation
4. reboot

---

### Post by kellemes on 2007-03-31
su
md /mnt/cdrom
mount -t iso9660 /dev/hdc /mnt/cdrom
start the copy..

---

### Post by FlyingIsFun1217 on 2007-03-31
> **dreadlord_chris said:**
> 1. boot into recovery mode
2. stick the LiveCD in and mount it
3. copy /usr/sbin from the CD to your installation
4. reboot

1) Ok, can do that
2) How would I mount it?
3) what command is used for copy? I just used mv to move the stuff to my flash drive.
4) easy enough

FlyingIsFun1217 :)

---

### Post by kellemes on 2007-03-31
use cp for copy

---

### Post by FlyingIsFun1217 on 2007-03-31
But how would I mount the LiveCD?

Thanks again!
FlyingIsFun1217

---

### Post by kellemes on 2007-03-31
use ls to find /usr/sbin on liveCD

then "cp /mnt/cdrom/SomewhereonLiveCD/usr/sbin /usr/sbin"

---

### Post by kellemes on 2007-03-31
su
md /mnt/cdrom
mount -t iso9660 /dev/hdc /mnt/cdrom
start the copy..

---

### Post by kellemes on 2007-03-31
Sorry cp needs the -R option
so.. "cp -R dirtocopy/ newdir/"

good luck.

---

### Post by FlyingIsFun1217 on 2007-03-31
K, I'll try...

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-03-31
Ok, that didn't work, so I just booted the LiveCD.

Now how do I mound the HDD so that I can copy the files from the cd to the normal /usr/sbin?

Thanks again!
FlyingIsFun1217

---

### Post by Ramses de Norre on 2007-03-31
On live disc:
```
sudo mkdir /media/tmp
sudo mount -t ext3 /dev/??? /media/tmp
sudo cp -a /usr/sbin /media/tmp/usr/sbin
sudo reboot
```

---

### Post by FlyingIsFun1217 on 2007-03-31
SADFSGSDGSGDSDGFAEGVSBHSETHSEGA!!!!!!!!!

Fed up with his stupidity, the computer user decided to do the unthinkable...
He...
reinstalled...
UBUNTU!

Thanks for the help you guys gave me. I decided to just start over clean. I used gparted to delete the Ubuntu partition, and from there I just did a reinstall. Everything's back to normal again (except for all of my wasted time).

FlyingIsFun1217 :)

---

