---
title: "Removing other OS !"
date: 2007-12-01
forum: General Help
---

### Post by Ciwan on 2007-12-01
Hi Guys

When I power up my PC, I get the screen where I have to choose which OS to start up. I want to remove XP professional from that list.

so that the PC will boot straight into Ubuntu.

I didn't even install XP (I started but didn't finish). When I installed Ubuntu I told it to use the whole space on the HDD and it said it was formatting it !! But Still, I get that screen where I have to choose an OS

Someone please help

---

### Post by Ciwan on 2007-12-01
basically I want uninstall XP. Can someone tell me how I can do this with Ubuntu ?

---

### Post by LaRoza on 2007-12-01
Reformat XP's partitions, and remove XP from the grub.

```

gksudo gedit /boot/grub/menu.lst

```

Windows will be at the bottom, comment it out, or delete it.

---

### Post by Ciwan on 2007-12-01
How do I Re-Format Windows XP's partition ???

Sorry I'm a newbie !

---

### Post by sethvath on 2007-12-01
Did you read the ubuntu guide link I gave you in another thread? Its mentioned there. 

Look for gparted to reformat your xp partition and grub boot menu for the grub screen to choose which OS to boot into

---

### Post by Ciwan on 2007-12-01
Hi

Do you mean this link

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

I looked in all the list and couldn't find "gparted" !!

Can you tell me the article number to read, pleaseee

e.g. 1.5.12

thanks

---

### Post by sethvath on 2007-12-01
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Ciwan on 2007-12-01
Thanks a million man :) I know I'm a pain atm, but that will change when I get my head around Ubuntu. promise :)

---

### Post by sethvath on 2007-12-01
No worries, we all started as a newb. Welcome to Ubuntu

---

