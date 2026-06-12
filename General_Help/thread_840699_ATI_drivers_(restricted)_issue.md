---
title: "ATI drivers (restricted) issue"
date: 2008-06-25
forum: General Help
---

### Post by tmh177 on 2008-06-25
I have posted this here, did google search and found out a lot of ATI issues are in this forum, sorry for double posts.
Other post can be removed in hardware section, if it can be?

I have come across to links from Ubuntu:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Card I have is ATI Radeon X700 series and do not know how to get solution for inquiry below. Can someone look at the links anf let this newbie know, how to proceed?

TMH177

Post from Hardware Forum

When I enabled the restricted ATI driver and apply, Ubuntu asks for re-boot, which I do, I then get the dual boot screen (Vista/Ubuntu)on 
re-boot.

I then enter Ubuntu as choice and it starts to lunch ,as far as the bars go across, then all goes blank on monitor, so I have no idea what is on screen as nothing is visable, only thing it that screen is blank and monitor power button is yellow intead of green, so having blank screen I can not get to login or terminal.

As stated before only thing I can to is power of computer, then when I boot up again into Ubuntu , error messages come about unclean unmount, which it tries to fix, but it can not.

As a result I have to delete partion through LiveCD, then re-install, thsat is why I am leary of trying the other method.

Card I have is ATI Radeon X700 series. I just do not want to do another install if the EnvyNG driver install does same thing.

TMH177

---

### Post by boballen55 on 2008-06-25
I don't have any solutions for you but I have had a similar experience with an ati card, a X1300 though.  The default driver just works but I can't do anything with effects so I tried the proprietary one and it just created a lot of problems.  I could only use safe graphics mode even after trying to fix it/reinstalling and such.  eventually I got it back to the way it was and it basically works.  Somehow permanently lost the ability to suspend/restart and I still can't do effects.  So I'm going to get some sort of Nvidia card because there seems to be better results in Ubuntu (at least with the older ones).  So I would say if it didn't work the first time it is probably not worth trying the ati driver again.  Seems to have quite a low success rate.  But I am no guru maybe someone could help you.  Good luck.

---

### Post by earthmeLon on 2008-06-25
I had to edit my /boot/grub/menu.lst and remove the splash screen for example:

```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=adsfasdfasd-asdfasdf-sdfdsfd ro
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

```

And I always suggest using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install gfx drivers.

---

