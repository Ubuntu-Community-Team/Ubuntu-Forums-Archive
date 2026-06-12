---
title: "Configure Grub to boot Mac OS X"
date: 2006-11-14
forum: General Help
---

### Post by ribamar on 2006-11-14
Hi.
I have Windows XP installed.
Then I installed Linux Ubuntu 6.10, therefore, I use Grub to boot to the operating systems.
Then I installed JaS Mac OS X 6.4.7, but I can't boot to it. What do I have to configure, modify or edit, how and where, so by Grub boot can also boot to Mac Os X? Right now I have Mac Os X installed and I can't boot to it anyway... ](*,) 
Help please... 

Regards from Portugal ;)

---

### Post by ciscosurfer on 2006-11-14
I don't know, [but you may find this interesting]("http://neosmart.net/blog/archives/273").

Otherwise, [this link is interesting]("http://wiki.osx86project.org/wiki/index.php/Installation_Guides").

Of course, you can also search the forums here under the PPC section.

EDIT:  I've found these threads which you may find useful >>[LIST=1]
[*][GRUB boots macbook]("http://ubuntuforums.org/showthread.php?t=233400&highlight=grub")
[*][Booting Tiger from GRUB]("http://ubuntuforums.org/showthread.php?t=63401&highlight=grub")
[*][Tiger breaks GRUB]("http://ubuntuforums.org/showthread.php?t=32261&highlight=grub")
[*][HOWTO: Install Ubuntu on a Macbook and use GRUB]("http://www.ubuntuforums.org/showthread.php?t=233243")
[*][Insanely Mac Forum]("http://forum.insanelymac.com/lofiversion/index.php/t29745.html")[/LIST]

---

### Post by ribamar on 2006-11-14
I've find out that the problem to my Mac Os don't boot is because the partition where is installed is extended, it should be primary... i've read that ubuntu has fdisk wich can convert extended partitions to primary... i've runned the fdisk in the terminal and i couldn't do anything, there are almost no options, is very limited the program... how can i transform the extended partition where i have the mac os installed to a primary partition?

---

### Post by ciscosurfer on 2006-11-14
This [link will help you out]("http://gparted.sourceforge.net/index.php")...remember, the graphical partition editor that Ubuntu uses from the Live CD, is GParted.  My recommendation is to burn a GParted Live disc from the site I provided, and use the information from that site to tell you how to "convert" it.  In my experience, the best way to do it would be to simply create a primary partition and don't use the extended partition as it's mount point.

---

