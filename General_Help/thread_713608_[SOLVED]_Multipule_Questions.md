---
title: "[SOLVED] Multipule Questions"
date: 2008-03-02
forum: General Help
---

### Post by Plasma_NZ on 2008-03-02
**_ Ok first up..._**

Ok i have 4 HDD's

x2 SATA2 
x2 IDE
 
Windows Boot-loader is located on sda1 and it seems grub is located on hda1
... How can i remove the windows Boot-loader and put grub on there, so i can select the OS i choose to use....??

**_Second up_**

I have 2 Sound-cards

Onboard realtek  and a PCI sound-blacster 5.1
How can i make the PCI card the default sound-card...


**_Third up_**

I have 4 screens across 2 video-cards...

x2 Nvidia 8500GT 256MB 

On Card one, i have a DVI screen attached and a SVHS screen attached
On Card two, i have a CRT screen attached and a SVHS screen attached

Can someone give me a link to a "simple to follow" guide on howto configure them all as seperate xsessions..??

Cheers..

If one finds it easier to help via MSN, pm me for my email..  (i will repost my solutions found from MSN chat to here as a follow-up thread to this one)

---

### Post by arimaniac on 2008-03-03
Hi there

About your 2nd issue:

I have written a **complete HOW TO **on this.

Check it out...

[http://ubuntuforums.org/showthread.php?t=712908]("http://ubuntuforums.org/showthread.php?t=712908")

[B]PLEASE post a reply of your experience on this so 
I can make the HOW TO better.[/B]


Hope this helps...

---

### Post by Woody1987 on 2008-03-03
Answer 1

If you go into the bios and change the boot order for the hard disks you can make it look at hda1 first thus allowing you to choose. If you remove the windows bootloader you wont be able to boot windows at all. Grub essentially loads the windows bootloader when you select the windows option in grub. If you change the boot order in the bios you will probably need to change some of the grub settings to make sure it checks the correct drives.

Answer 2

previous post

Answer 3

Open a terminal type: sudo nvidia-settings. From there you can configure two separate xsessions.

---

### Post by Plasma_NZ on 2008-03-03
Cheers for the responses

Ok regarding the soundcard issue.... i have 2 sound cards and will be installing a third soon... reason being...  I have 4 screens basically, 2 in my office and te other 2 in different rooms for media....  Basically screen 3 will have its own soundcard for dedicated sound, and screen 4 another dedicated soundcard... what im trying to achive is to set a certian cards as a default (hopefully not the onboard soundcard) ... hope u follow what i mean..

As for problem 3, have made a new post, and nvidia-settings messes it all up

[http://ubuntuforums.org/showthread.php?t=713736](http://ubuntuforums.org/showthread.php?t=713736)

---

### Post by Plasma_NZ on 2008-03-04
SOLVED

1. Changed BIOS HDD boot order

2. Kinda Solved   Doesnt matter anymore, and the devices i use i can select which card to use

3. Refer to Thread  [http://ubuntuforums.org/showthread.php?t=714427](http://ubuntuforums.org/showthread.php?t=714427)

---

