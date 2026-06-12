---
title: "looking for apt on usb.."
date: 2016-06-21
forum: General Help
---

### Post by a.dusty.trail on 2016-06-21
I've seen aptoncd. But really who on earth uses cd's for anything any more..
I've googled but no luck..

Has anyone seen something like apt on usb that works simply and automagiclly for 16.04?

---

### Post by yancek on 2016-06-21
Aptoncd is specific to Mint as far as I know.  What exactly do you need to do.  Any Ubuntu Live CD on a DVD or flash drive should have the apt command although a Live CD is read only and everything is lost on reboot.  Do you have an actual install of some Ubuntu version on the flash drive.

---

### Post by ajgreeny on 2016-06-21
I used aptonCD some years ago but stopped doing so when I realised that I could do the same thing with a USB drive by copying the contents of /var/cache/apt/archives to it using command ```
cp -n /var/cache/apt/archives/*.deb */media/USB*
``` then copying those .deb files back to /var/cache/apt/archives in the destination OS with ```
cp -n */media/USB/*.deb* ./var/cache/apt/archives/
```editing the */media/USB* for your own system, of course.

Quick, simple and totally effective, but doing just about the same as aptonCD.

---

### Post by a.dusty.trail on 2016-06-21
> **ajgreeny said:**
> I used aptonCD some years ago but stopped doing so when I realised that I could do the same thing with a USB drive by copying the contents of /var/cache/apt/archives to it using command ```
cp -n /var/cache/apt/archives/*.deb */media/USB*
``` then copying those .deb files back to /var/cache/apt/archives in the destination OS with ```
cp -n */media/USB/*.deb* ./var/cache/apt/archives/
```editing the */media/USB* for your own system, of course.

Quick, simple and totally effective, but doing just about the same as aptonCD.
that is one way to do it, but if you dont want to install every app its not quite as nice, or if you have 32 or 63 gb of data you have collected, a long time to wait to copy.

you can use  the package "local-apt-repository"  in much the same way...
but once again it dose not lend it self to portable usb devices simply

aptoncd will set it up to have a number of app that are install able from a portable device( but a cd and who uses those?), and have it act like a repository so that you don't have to go though dependency hell.
it might work as a cache, but aptoncd acts like a repository so you can have hundreds if not thousands of packages ready to install very simply.

something like aptonusb would be quite useful..

---

### Post by ajgreeny on 2016-06-22
> **a.dusty.trail said:**
> that is one way to do it, but if you dont want to install every app its not quite as nice, [COLOR="#FF0000"]or if you have 32 or 63 gb of data[/COLOR] you have collected, a long time to wait to copy.

you can use  the package "local-apt-repository"  in much the same way...
but once again it dose not lend it self to portable usb devices simply

aptoncd will set it up to have a number of app that are install able from a portable device( but a cd and who uses those?), and have it act like a repository so that you don't have to go though dependency hell.
it might work as a cache, but aptoncd acts like a repository so you can have hundreds if not thousands of packages ready to install very simply.

something like aptonusb would be quite useful..
I suspect you may have misunderstood what I meant, or how I did what I'm suggesting, and I can not believe anyone has ever had as much as 32 or 63GB of data (ie .deb package files) in /var/cache/apt/archives/.

All I'm suggesting is copying the .deb files from one machine to another, then using your package manager choice to install what you want, just as aptonCD used to, if I remember correctly, though also from memory I think I never used a CD when I used aptonCD; I simply asked the application to create an aptonCD archive which I moved from machine to machine, avoiding CD completely.

Sorry, but it is years since I used aptonCD so can not remember exactly how it named the archive production process; look for it and I'm sure you'll find it.

---

### Post by a.dusty.trail on 2016-06-22
i gave aptoncd a bash a while ago...
it looks for the cd in some silly spot that is no longer used by ubuntu for mounting the cd
and it force unmounts the mount point every time after and maybe before..
( it has not been updated to know that ubuntu automagilly mounts things now)
so it is quite a headache to get to function..
(i recall have a two or three stage method to get it to function just with a cd never mind trying with usb or linking a mounted iso)
its basically old software that it built and kept in the repositories but functions horribly with any recent install.

the only point i can see for it any more if to drive the moderately skilled to drink and curse..and the less skilled to go back and use windows..

which is why im looking for something recent for usb....LOL

---

