---
title: "3 OS in my system"
date: 2008-03-19
forum: General Help
---

### Post by Yappy on 2008-03-19
I have three OS installed.

1. WindowsXP
2. Ubuntu
3. Another Linux..Slakeware?

I wish to keep Windows and Ubuntu. How do I remove the other OS.

Will fdisk do the job and how do I know which OS is in which partitions?

I saw one Fat32 partition and 2 other Linux partitions.. which one is Ubuntu. Ubuntu is the last(latest) OS installed.

Please help.

Thanks

TS Yap
Singapore

---

### Post by Tomatz on 2008-03-19
Aslong as your system does **NOT** boot from that partition it should be safe to format it.

fat32 will be windows

To determine wich of the other 2 is the slackware drive open the "computer" window/folder in nautilus and r click on the slackware drive click properties then just write down the drive letters e.g. sda2 (volume)

Then use gparted its a gui partition editor/format tool:

sudo apt-get install gparted

Then access gparted from system, administration, GNOME partition editor

Find the partition (the one you wrote down)

unmount it if necessary

format ext3 :)

---

