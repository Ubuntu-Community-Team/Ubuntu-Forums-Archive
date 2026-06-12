---
title: "black screen on boot - 8800 gts - usplash - usplash.conf - gutsy"
date: 2007-10-18
forum: General Help
---

### Post by distroman on 2007-10-18
[https://bugs.launchpad.net/ubuntu/+bug/140908](https://bugs.launchpad.net/ubuntu/+bug/140908)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930)

It boots fine with "unsplash" added to /boot/grub/menu.lst which is nice.
However I would like to get the bootsplash working, so fare none of the workarounds have worked for me or I have missed something. 
What do I need to do?

---

### Post by qkslvr221 on 2007-10-18
Same card, same issue. It appears we aren't alone either!

[http://ubuntuforums.org/showthread.php?t=574124&page=2](http://ubuntuforums.org/showthread.php?t=574124&page=2)

---

### Post by distroman on 2007-10-20
Thanks for the link. 

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

Seems I got two bugs mixed up btw.

I wanted to go 64 bit with ubuntu, that did not work out for me.
The above bug is unfortunately not the only one that hit me, I could be more specific but I don't see the need for anymore links to launchpad.

On a side note, the 64 bit install didn't pick up my etx3 backup partition, I had to fstab, chown and chmod it. Something that was not needed with the 32 bit install, might not be related to anything, just noticed it.. 
For me the 64 bit install did not feel more responsive then the 32 bit install in fact it seemed the opposite. Also I had applications crashing on me, including nautilus, something I am not use to. 

I do have other 64 bit distributions installed and I feel that this might be more of an ubuntu/gutsy issue then a 64 bit issue. 

Anyway I am back on 32 bit gutsy and all is good, in fact really good.

Maybe I am just unlucky however this setup failed for me with gutsy 64 bit:
AMD X2 5200+
M2N-SLI Deluxe
8800GTS

---

### Post by SunnyRabbiera on 2007-10-24
I had a simular issue...
but I have a different card

---

### Post by MatthewPlanchard on 2007-10-24
have you tried adjusting the /etc/usplash.conf file to your monitor's default resolution?

most workaround suggest 1024x768, but mine didn't work until I set it to my laptop's native 1280x800

---

### Post by distroman on 2007-10-24
I have been running arch for some time IMO it makes for a better 64 bit option then gutsy. 
Give it a try.

---

