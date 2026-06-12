---
title: "Why can't I make this Ubuntu Live USB persistent?"
date: 2014-07-09
forum: General Help
---

### Post by shaansweb on 2014-07-09
Hello,

I am attempting to make an Ubuntu persistent USB but I am unable to do so. I am trying to use the startup disk creator but the persistent section is grayed out. Does anyone know why the persistent option is grayed out and how I can fix it? Thanks

[IMG]http://i.imgur.com/K1Q7Eqi.png[/IMG]

---

### Post by grahammechanical on 2014-07-09
My guess is that the flash drive is not large enough  hold the Ubuntu ISO image and have sufficient space left over to be used as reserved extra space.

Regards.

---

### Post by nerdtron on 2014-07-09
Have you tried clicking the "Erase Disk" button?

Also, you can try downloading unetbootin linux version [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by yancek on 2014-07-10
Your iso is 960MB and the flash is only 2GB so you won't have much space for persistence.  I would also suggest you do the Erase Disk before proceeding.  If you don't get the option to create persistence create the flash drive anyway.  When it is finished, if you have an installed system or a CD/DVD with GParted, you can use that to resize (shrink) the partition on which you put Ubuntu, then create another partition with the remaining free space and format it ext2 and give it a Label:  casper-rw

---

### Post by shaansweb on 2014-07-10
there should be over 1000 mb left over, right? Even 50 mb will work for my purposes

---

### Post by shaansweb on 2014-07-10
Yes, I trieed the erase disk button, but it didn't help. I tried installing unetbootin, but can't get it to run. It prompts me for my password, I enter it, and nothing happens

---

### Post by shaansweb on 2014-07-10
> **yancek said:**
> Your iso is 960MB and the flash is only 2GB so you won't have much space for persistence.  I would also suggest you do the Erase Disk before proceeding.  If you don't get the option to create persistence create the flash drive anyway.  When it is finished, if you have an installed system or a CD/DVD with GParted, you can use that to resize (shrink) the partition on which you put Ubuntu, then create another partition with the remaining free space and format it ext2 and give it a Label:  casper-rw

Erasing didn't help. And the reason I'm making the flash drive is to be able to make a live usb with GParted so I can fix the partitions on my laptop

---

### Post by monkeybrain20122 on 2014-07-10
gparted is in the live iso, you don't need to make it persistent.

(anyway you don't need persistence unless whatever you install in the usb needs reboooting to work)

---

