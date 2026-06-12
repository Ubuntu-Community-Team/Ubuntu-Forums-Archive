---
title: "grub error 15"
date: 2008-06-09
forum: General Help
---

### Post by ripin1 on 2008-06-09
ok. this is bigger than every problem ive had with my computer so far. i admit, i am ashamed of myself. ok, so i tried installing fedora 9 to replace ubuntu, not that i dont like ubuntu, its just i needed a change. so anyway, i put the live cd in and click the install to disk button on the desk top. i clicked the option to delete all other linux partitions and make default setup(or something like that) and when it was done, i rebooted and it said 

           loading grub 1.5 
           please wait...
           grub error 15
 or some thing of that sort. now, i am 11 years old, so i am going to need step by step instructions to try to fix it. i dont even know how to get a command line. my ubuntu live cd is gone, and this crappy computer im using now has no burner. HELP ME! my computer is all ive got.

        thanks in advance,

                          peter

---

### Post by RedPandaFox on 2008-06-09
Hey, I had a similar problem althow I was trying to install multiple OS's to use for different things.
Have you got a USB you can install it from? 
Try [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Then install it back onto your PC using the install function. ( i would suggest using hardy ubuntu) then install fedora on a different partition if you can. There are plenty of walk through for that. The grub maker for fedora should make an entry for Ubuntu and Fedora to duel boot.

---

### Post by ripin1 on 2008-06-09
i have a usb drive, but it only has 512 mb. another question is how to get a comand line in my state?

---

### Post by shawnhath on 2008-06-09
If you still hae the live CD for Ubuntu reinstall that deleting all other partitions. Then redownload the Fedora one and do an md5check on it to check the integrity of the iso image. If it comes out okay then try reinstalling Fedora

---

### Post by miss.magenta on 2008-06-09
Since you said you don't have the livecd anymore, you can fix this from a grub prompt, which you should be able to get after the error 15 happens.

There is a good post on this, with instructions on how to fix grub from the grub command line, here:

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

---

### Post by ripin1 on 2008-06-10
> **miss.magenta said:**
> Since you said you don't have the livecd anymore, you can fix this from a grub prompt, which you should be able to get after the error 15 happens.

There is a good post on this, with instructions on how to fix grub from the grub command line, here:

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)
if by grub prompt, you mean command line, then i cant. after it says error 15, it just sits there.
 
  p.s. guess what? i got my live cd for ubuntu back, but i did the error cheking feature, and it has 11 errors.  is xubuntu small enough for a 512mb usb drive?

---

### Post by RedPandaFox on 2008-06-11
Yes, it should be, you can get slimed down versions of all Ubuntus to fit very small devices. I run a 2 GB EeePC surf with ubuntu 8.04 and the install was about 500mb

---

### Post by ripin1 on 2008-06-27
its as if im not meant to have a computer. i went to go look for my usb drive and i found it on top of one of those super powerfull magnets. isnt that just dandy?
but thee is good news!(i hope) i mught get a copy of windows xp tomarrow. will that fix the problem right there? if not, will re-installing ubuntu fix it?

---

### Post by VMC on 2008-06-27
> **ripin1 said:**
> its as if im not meant to have a computer. i went to go look for my usb drive and i found it on top of one of those super powerfull magnets. isnt that just dandy?
but thee is good news!(i hope) i mught get a copy of windows xp tomarrow. will that fix the problem right there? if not, will re-installing ubuntu fix it?

Download Puppy mini disk here: [http://www.puppylinux.com/flash-puppy.htm](http://www.puppylinux.com/flash-puppy.htm), look for the section  "How to obtain and install flash-Puppy" and read that section. Puppy is very small and will work. Then come back here afterwards and we can help you.

---

