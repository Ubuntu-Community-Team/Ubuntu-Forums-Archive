---
title: "Just bought a USB hard drive enclosure.  How makey worky?"
date: 2007-09-10
forum: General Help
---

### Post by mjpatey on 2007-09-10
I just bought a Vantec 3.5" USB 2.0 hard drive enclosure, and installed a Western Digital 500GB 7200 rpm drive.  The drive is installed correctly into the enclosure (in "Master" mode as the enclosure's directions specified), the drive is receiving power (power light is lit), and its USB cable is connected to my computer.

When I power on the drive and connect it to the computer, nothing happens.

I know it's a *little* naive to assume it will just get auto-recognized and mount automatically, but that's what I'm used to with other USB devices, so I was kind of hoping that would be the case.

Is there some config file or something that I need to tweak in order to introduce this portable drive to my system?

Thanks for any insight you may have!

-Mark

---

### Post by Happy_Man on 2007-09-10
First, open a terminal. Then enter ```
sudo fdisk -l
``` to see what Linux recognizes the external as (should be something like /dev/sdb1). Remember that, and then do this: ```
sudo mount /dev/sdb1 <or whatever it was> /media/external
```. The contents should then show up in the folder /media/external.

---

### Post by mjpatey on 2007-09-10
Thank you, that looks like it's going to work!

I just realized my drive is not yet formatted.  Should I install gparted and format it that way?  And, the big question... it's a 500 GB drive, and I'll be plugging it into 2 other computers, both of which run Windows.  Can vFAT handle 500GB, or should I do it in NTFS?  My Feisty install seems to handle read/write of NTFS flawlessly; is this a safe thing to do?

Thanks again.

-Mark

---

### Post by uzybear on 2007-09-12
hello, i just tried to do this, and fdisk shows my external drive but when i try to mount it says:


can't find /dev/sdb in /etc/fstab or /etc/mtab

it also says /dev/sdb doesn't contain a valid partion table when i do the fdisk thing


this is a brand new seagate ide 250gb external usb drive; or rather it is the seagate HDD in my own usb enclosure

---

### Post by uzybear on 2007-09-12
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


it says that when i do fdisk so it's showing up at least

---

### Post by eentonig on 2007-09-12
I recommend to create a few seperate partitions on that 500G drive.

---

### Post by uzybear on 2007-09-12
ok so now i downloaded gparted and how do i use it? what should i do?

---

### Post by uzybear on 2007-09-12
so i downloaded it from add/remove programs and it's supposd to show up in "system tools" i guess but it doesn't

---

### Post by uzybear on 2007-09-12
do i need some "repositories" or something; i'm baffled why such simple things are so complicated on linux

---

### Post by tact on 2007-09-12
> **uzybear said:**
> so i downloaded it from add/remove programs and it's supposd to show up in "system tools" i guess but it doesn't

Gnome Partition editor will show up in System>Administration

---

### Post by uzybear on 2007-09-12
brilliant; thanks very much; not sure how i messed that up;wil try it tomorrow

---

### Post by Frijolie on 2007-09-26
I'm having this same problem... Is there a way that it can "auto mount" when plugged in--like my USB thumb-drive? When "auto-mounted", it is shown as a menu option in "Places > Disk", when I open up a window in Nautilus on the left-hand side, and as an icon on my desktop.

I have a 80GB HDD in a USB external enclosure and would love for it to behave in this manner. I'm trying to use the external drive as extra storage and as a backup for critical files/documents.

---

