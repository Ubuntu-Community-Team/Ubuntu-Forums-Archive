---
title: "gutsy grub boot failures"
date: 2008-02-09
forum: General Help
---

### Post by oxman on 2008-02-09
I have three drives that contain ubuntu. I am unable to access any of them. I have dapper on root on sda1, gutsy root on sdb1 and gutsy on hda1. I have been trying to fix the menu.lst and fstab  and now there is a complete failure in being able to boot into any of the drives.

If I try booting from a cd (boot from 1st hard disk) it will not boot no matter what option is given to me. I get file 15 failure, 21 failure and now an fsck failure due to a drive not being able to able to be identified. 

I do not have an alternate boot disc. I do have my old version of dapper install cd but have not attempted to use it for access.

I am in a serious bind. Please help

---

### Post by rucadulu on 2008-02-09
When you set this three installs up do you create three different boot partitions, a single boot partition, or no boot partition ?t

---

### Post by oxman on 2008-02-09
Thank you for the reply.

I set up / and /home on each drive. I have not set up a boot partition. Judging by this situation I think I should be.

---

### Post by oxman on 2008-02-10
I feel like I have fallen into a self made honey pot.

I am now able to boot into my hda hardrive (gutsy) but I am unable to boot into my dapper ubuntu drive (sda) or my sata gutsy drive (sdb) When I attempt to do this I get an fsck failure saying that says there is a drive with an unresolvable uuid number. 

My main concern is to be able to boot into my dapper (sda) drive without fowling up my system. My "boot from 1st hard disk" doesn't even give me the option to boot from dapper. It is misreading my drive and saying it has gutsy on it (which) is does not.

Please help me get back into my dapper drive.

---

### Post by rucadulu on 2008-02-10
Oxman, could please post your grub config file and menu list file so I can look to see if the paths look like they maybe corrupt. They are located under your /boot directory on the gusty install that you can boot.

---

### Post by oxman on 2008-02-10
rucadulu: Thank you for your interest. I am grateful to have someone to bounce off of for this stuff. I am currently thoroughly immersed in the 31 printed pages of [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm). Interesting stuff but it sure would be great to be reading it from my dapper drive (sba) 

Well, problem solved. i spent forever editing fstab files and and menu.lst to no avail. Kept searching and reading and there really wasn't a clue of evidence that I could find. 

I began by trying to reverse my steps which led me to at least be able to boot both of my gutsy drives. But it is the dapper drive that has my workstation set up the way I need it. But no matter what I did I kept getting  the grub error 15 when seeking to boot to dapper. I tried matching menu.lst for all the drives. Still no joy.

Grub kept screaming that my dapper image didn't exist even though when i did from the grub prompt:
find /vmlinuz
find /sbin/init
root (hd1,0)
kernel /vmlinuz root=/dev/hd1,0
initrd /initrd.img
boot

began scrolling code and finally tells me that drive doesn't exist.

i'm like, "what the heck!!!"

Then a light bulb goes on. I del the bios setup and start flipping hard drive priorities around. 

Alas this is brought to you by dapper drake!

rucadulu: Thank you for giving me the attention you did. Just being there was enough to encourage me to keep going.

---

### Post by rucadulu on 2008-02-15
I am glade you where able to figure out the issue. Just curious why do you need to have three different installs of Ubuntu on one machine. It seems like that is just asking for trouble, don't you think it would be better to either stick with the Ubuntu LTS track or stick with the every six months Ubuntu Release track. Well if you decide or need to keep things the way the are I would recommend creating a single boot partition and then merging your three boot directories in to the new single boot partition. I have noticed on the desktops that I have had multiple installs of Linux (be it different distro's) on them seem to work better with a single point for your grub config files.

---

