---
title: "[XUBUNTU] Do not boot after install"
date: 2013-11-19
forum: General Help
---

### Post by daannifilho on 2013-11-19
Hello!
Im new here, my name is Daniel and im from Brazil. (sorry for my very bad english and if im doing anithyng wrong, please tell me :p)
I always was user of Windows, but a few months ago, i started to develop to Android and I decided do give Linux a try. So I downloaded Kubuntu, i loved, it runned well on tis PC:

Intel Celeron D 2.26Ghz processor
2gb RAM
VIA/S3G Unichrome PRO video card

but my 2GB ram memory stick burned, so mc pc was stopped for a good time. But now, i bought 1gb ram stick, and tried kubuntu again. but it was a bit laggy, so i think that i nedd to use other ditro. downloaded xubuntu 13.10, put it on a pen drive, and booted and installed. installation was good, no problems, but at the time of booting, it dont boot. sometimes stuck at boot logo (the blue one), sometimes on a black screen or on the 4 dots screen.
tried lubuntu too, occours the same. what can i do? i heard that maybe it is some problem with video card, but, wattOS and Kubuntu boots normaly.

thx a lot!

----------------------------------------------------------------- SOLVED -------------------------------------------------------------------------------

---

### Post by QIII on 2013-11-20
[I]Moved to [B]General Help.

[/B][/I]The question relates to an "official" Ubuntu flavor, so need not have been in Other OS/Distro Talk.

---

### Post by ibjsb4 on 2013-11-20
Hi daannifilho, welcome to the forums :)

This is just a guess, but Kubuntu uses "QT" applications.  The other flavors do not depend on this and could be why Kubuntu is working for you.

[http://en.wikipedia.org/wiki/Qt_%28software%29](http://en.wikipedia.org/wiki/Qt_%28software%29)

Your video has a open source driver in the software-center (part of the default install).

xserver-xorg-video-openchrome

The S3G site has a limited selection of linux drivers.  Don't know if they are of any use to you.

[http://www.s3graphics.com/en/drivers/](http://www.s3graphics.com/en/drivers/)

---

### Post by daannifilho on 2013-11-21
Hi ibjsb4, thanks !
So, im trying xubuntu, but it don't boot, so how i can install if it does not boot ? Sorry, im newbie :p
Thanks !

---

### Post by ibjsb4 on 2013-11-21
Have you tried nomodeset?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by daannifilho on 2013-11-21
Hey guy, thnx for help, i downloaded Xubuntu 12.04.3 LTS and intalled on a new pendrive. It booted and installed like a charm - no problems at this moment. Thanks!

---

