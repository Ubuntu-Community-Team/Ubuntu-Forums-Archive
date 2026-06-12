---
title: "Wubi/Ubuntu Partitioning Problem!"
date: 2008-07-05
forum: General Help
---

### Post by YouSmeg118 on 2008-07-05
Hi,

I couldnt install Ubuntu because it failed whenever i tried to create partitions. So i installed XP and downloaded Wubi. 

It installed Ubuntu fine, and then when i tried to boot up into Ubuntu it goes through the install process, and it locks up.

There is a box that says 'Checking the Installation' as the title, with a Subtitle of 'Partition Formatting'. There is a blue bar, stuck on 5% and under that it says 'Creationg ext3 File System / i...' then it runs out of space (edge of the window). You can move the mouse, but if you click anything it freezes. Please help me, i want Ubuntu so badly!

---

### Post by ago on 2008-07-06
Boot in verbose mode (press esc at start), when you have problems press ctrl + alt + f4 and see if you can see any interesting msg

---

### Post by YouSmeg118 on 2008-07-06
> **ago said:**
> Boot in verbose mode (press esc at start), when you have problems press ctrl + alt + f4

Yeah i did this, but me pressing the buttoins didnt do anything as it was frozen. I rebooted, and waited up until the message that it locks up on and pressed ctrl + alt + f4 and it brought up a screen like this (i found this on another topic somewhere) [IMG]http://ubuntuforums.org/attachment.php?attachmentid=75318&d=1214423351[/IMG]

It says something about 'exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen'

If i leave it for a while soon messages start coming up very fast about failing to read blocks and unable to read the block cache... :( :confused:

---

### Post by ago on 2008-07-06
[http://ubuntuforums.org/showthread.php?t=841236&highlight=emask](http://ubuntuforums.org/showthread.php?t=841236&highlight=emask)

---

### Post by bbryant on 2008-07-06
> **YouSmeg118 said:**
> Hi,

I couldnt install Ubuntu because it failed whenever i tried to create partitions. So i installed XP and downloaded Wubi. 

It installed Ubuntu fine, and then when i tried to boot up into Ubuntu it goes through the install process, and it locks up.

There is a box that says 'Checking the Installation' as the title, with a Subtitle of 'Partition Formatting'. There is a blue bar, stuck on 5% and under that it says 'Creationg ext3 File System / i...' then it runs out of space (edge of the window). You can move the mouse, but if you click anything it freezes. Please help me, i want Ubuntu so badly!

Hi - OK... have similar problem... may not have enough memory... wubi said needed 256meg...have 255. two hang ups... 10 gig of hard drive used up. XP works OK.

Does anyone know how to uninstall the partial install ? Am buying more memory to try again.

---

### Post by YouSmeg118 on 2008-07-08
@BBRYANT
> **bbryant said:**
> may not have enough memory...[QUOTE]
I had a 40 gig Hard drive... but i have now discovered the problem is bad. So im buying a 60 gig, and putting Ubuntu on that. Maybe dual booting with XP. There was 38 gig free, i had XP in a 2 gig partition.

> **bbryant said:**
> XP works OK.
Mine worked fine too. Then again its a very stable and fast (sometimes) OS so its quite flexible.


@AGO
> **ago said:**
> [http://ubuntuforums.org/showthread.php?t=841236&highlight=emask](http://ubuntuforums.org/showthread.php?t=841236&highlight=emask)
Thanks. I had a look at this, and shortly after decided i would get a 60gig HD. Thanks.


When i get my new hard drive i will post back here to tell you how its going, Thankyou people!

---

### Post by ago on 2008-07-08
> **bbryant said:**
> Hi - OK... have similar problem... may not have enough memory... wubi said needed 256meg...have 255. two hang ups... 10 gig of hard drive used up. XP works OK.

Does anyone know how to uninstall the partial install ? Am buying more memory to try again.

Use the uninstaller in C:\ubuntu. If you used rev 505 AND you installed in a drive <> C: then you have to use [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe)

---

### Post by Iskaros on 2008-09-08
i tried to install ubuntu using wubi, but when i booted to ubuntu and it started to install it said no root file system defined go to partition menu
help plz

---

