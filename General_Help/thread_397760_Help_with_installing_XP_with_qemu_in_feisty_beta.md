---
title: "Help with installing XP with qemu in feisty beta"
date: 2007-03-31
forum: General Help
---

### Post by neogenesis213 on 2007-03-31
I was trying to install windows XP in Feisty beta through qemu following the instructions in [here ]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo"). 
I made a qcow image of 5GB.
Everything seems to work until I put in my CD and hit this command "qemu -localtime -cdrom /dev/cdrom -m 384 -boot d windows.img" for installtion. 
In the terminal it says kqemu not being present even though i installed it like a minute ago.
Despite this the installaiton loads and it gets to a screen asking me to press "C" to create partition. When I press C it takes me to another screen to choose the size of the partition. When I type in a size (and I've tried many) and hit enter I'm back to the first page telling me I have unpartitioned space and hit C to create partitions. And the loop continues indefinately until i get frustrated and give up.

Is there something im doing wrong? plz help!

---

### Post by Adramelech on 2007-03-31
Kqemu is a kernel module to run qemu faster, and is not installed by default, dont worry about that error.

try: 
qemu -localtime -cdrom /dev/cdrom -hda windows.img -m 384 -boot d

---

### Post by neogenesis213 on 2007-03-31
Thx for clearing that up about the kqemu.

OK i reinstalled qemu and this time the install worked. took three times as long as VirtualBox. Not to mention it makes my 3.4GHZ run slower than my old 300Mhz running XP. Looks like virtualbox for now. But I was really hoping i could get XP running in qemu because i prefered the programs to be seamless. also you can't seem to be able to copy and paste between host and guest in virtualbox.

---

