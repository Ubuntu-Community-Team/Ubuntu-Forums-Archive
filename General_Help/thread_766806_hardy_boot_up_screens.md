---
title: "hardy boot up screens"
date: 2008-04-25
forum: General Help
---

### Post by sefs on 2008-04-25
After install

I get 

1) the gauge with the progress bouncing back and forth
2) black screen with the text scrolling up?

This happens all the time...

In gusty it went straight from the gauge screen to the login prompt with out seeing the technical stuff scrolling by.

Is there a way to toggle this on and off? as in some cases it will be useful to see the scrolling stuff.

Thanks.

---

### Post by erginemr on 2008-04-27
BUMP! 

Same story: Knight Rider mode, followed by boot text screen. Any ideas?

---

### Post by danwood76 on 2008-04-27
Seems like usplash has broken on your systems, I just noticed mine does the same.
The text scrolling is what is happening behind the Ubuntu splash screen.

Its nothing to worry about, if it really bugs you I will have a go at fixing mine. :)

---

### Post by erginemr on 2008-04-27
Well, I have some good news! :D

It seems the upgrade process has somehow changed the UUID code for the swap partition and having a wrong code causes usplash to crash.

Following this thread:
[http://ubuntuforums.org/showthread.php?t=746132](http://ubuntuforums.org/showthread.php?t=746132)

1. I could fix usplash screen by first issuing:
```
sudo blkid
```
from a terminal, copying the UUID for "swap".

2. And then, editing the file:
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
and paste the correct UUID for swap, but without the quotes.

3. Finally, to make sure that the changes are reflected in usplash:
```
sudo update-initramfs -u
```
This will take about a minute, but it is crucial that this process is completed. Otherwise, you will have a broken initramfs file and won't be able to boot.

The credit goes to **analystscouch** and **MALEADt** from the a/m thread:
[http://ubuntuforums.org/showpost.php?p=4714344&postcount=16](http://ubuntuforums.org/showpost.php?p=4714344&postcount=16)
[http://ubuntuforums.org/showpost.php?p=4714530&postcount=20](http://ubuntuforums.org/showpost.php?p=4714530&postcount=20)

---

### Post by sefs on 2008-04-28
This works for the -generic kernel but not the -386.

How do I get it functional with the -386 kernel.


UPDATE:

Ok from this page ... [http://www.manpage.org/cgi-bin/man/man2html?8+update-initramfs](http://www.manpage.org/cgi-bin/man/man2html?8+update-initramfs)

for the -386 kernel i am using i had to run the extra command 

```

sudo update-initramfs -u -k 2.6.24-16-386

```

2.6.24-16-386 being the kernel i use that's loaded at boot.

which basically specifies the kernel i wanted update with this initramfs thing.  I do not know why the inital command chose to update only -generic when its not even my default kernel.  but there you have it.

splash screen now works properly though.

---

### Post by cespinal on 2008-05-14
> **erginemr said:**
> Well, I have some good news! :D

It seems the upgrade process has somehow changed the UUID code for the swap partition and having a wrong code causes usplash to crash.

Following this thread:
[http://ubuntuforums.org/showthread.php?t=746132](http://ubuntuforums.org/showthread.php?t=746132)

1. I could fix usplash screen by first issuing:
```
sudo blkid
```
from a terminal, copying the UUID for "swap".

2. And then, editing the file:
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
and paste the correct UUID for swap, but without the quotes.

3. Finally, to make sure that the changes are reflected in usplash:
```
sudo update-initramfs -u
```
This will take about a minute, but it is crucial that this process is completed. Otherwise, you will have a broken initramfs file and won't be able to boot.

The credit goes to **analystscouch** and **MALEADt** from the a/m thread:
[http://ubuntuforums.org/showpost.php?p=4714344&postcount=16](http://ubuntuforums.org/showpost.php?p=4714344&postcount=16)
[http://ubuntuforums.org/showpost.php?p=4714530&postcount=20](http://ubuntuforums.org/showpost.php?p=4714530&postcount=20)



IT WORKED FOR ME!! THANK YOU VERY MUCH

---

### Post by danwood76 on 2008-05-15
> **sefs said:**
> 
for the -386 kernel i am using i had to run the extra command 

```

sudo update-initramfs -u -k 2.6.24-16-386

```


This is a bit of a late reply but it may help some people in the furture.

if you run:
```

sudo update-initramfs -u -k all

```
it will update all of your initramfs for the installed kernels, so you wont get that issue.

---

### Post by BuckroeBill on 2008-05-17
Just a big THANKS. I have seen several solutions posted for the usplash problem. This one works! Thanks for being out there.:)

---

### Post by Umang on 2008-07-28
Thank you! This worked for me. 

I don't if it's OK to bring up such an old thread, but just a small question:

Shouldn't this have been done automatically? I mean, as soon as Ubuntu notices UUID of the swap being different, shouldn't it correct the UUID itself? gParted being pretty easy to use, I can expect a lay person to resize their partitions but doing this (correcting UUIDs) requires a little bit of research. Is this a bug?

---

### Post by warpasylum on 2009-06-20
Thanks. Fixed my splash in Jaunty.

---

### Post by Sigma1 on 2010-07-11
Thanks from me, too. Fixed a mess I'd made trying to get suspend to work with uswsusp and Intrepid (I've uswsusp is probably not worth the trouble!)

---

