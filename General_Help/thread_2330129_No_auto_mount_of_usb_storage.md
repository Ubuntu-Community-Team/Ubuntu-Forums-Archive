---
title: "No auto mount of usb storage"
date: 2016-07-08
forum: General Help
---

### Post by Tanarotte on 2016-07-08
Heya. 
I've been working to revitalise my clients laptop, i tested Kubuntu, lubuntu, xubuntu and ubuntu mate, manjaro but i decided to stick with Xubuntu because in my eyes it offers the best performance per unit of *looking_shiny*and is relatively hassle free for new users.
However just now i realised . . . .except for manjaro not a single ubuntu 16.04 flavor did mount my pendrive which i thought could be u know . . . multiboot pendrive sort of configuration that stops it from happening. 

Imagine my surprise when I tested it today, and on currently running Xubuntu 16.04 none of my 3 pendrives work. None of them display as an icon on desktop, none of them display as an entry in "filesystems". 
Pendrives are 2x Kingstons and 1x Pdp Patriot.   1x kingston with Fat32 and multiboot, 1x Kingston with ntfs, 1x pdp patriot with exFAT. 
With exception to the "multiboot" pendrive, i have reformated these again in Windows 10 and in gparted for testing if it will work. NOPE. (and by reformated i mean removed partition, recreated primary one and reformated it)

All 3 pendrives report correctly in [I]lsusb
[/I]All 3 pendrives can be manually mounted using *sudo mount /dev/sdd1*(or sdc1 etc etc) [I]-t auto /mnt/somefoldername

[/I]Now the issue is, this laptop is for 10 year old kids to safely play browser games and stuff, while I could be manually mounting every single piece of crap with usb port on the end in command line or giving everything specific labels and automounting it by specific labels, I can not expect the same of my client or his kids. 
I need that basic system functionality back up and running, mounting everything to desktop and "filesystems" thing in a proper plug and play fashion like it should be working.

. . . . but i am out of ideas and google doesnt seem to help much ;-/

---

### Post by Hans Verschoor on 2016-07-09
Forget about mounting USB mass storage devices in Ubuntu from now on. I experience the same problems with my Nikon camera, a flash card, a flash card reader. The sh.. started after a kernel upgrade, I don't remember exactly when, because before that everything worked fine. I think the Linux kernel, at least in Ubuntu, is in deep trouble relating to mounting USB devices. Just Google on this subject..... For the time being, and I'm afraid for a long time to follow, I just gave up. I use a Windows machine to transfer the data from my camera and flash cards to my Ubuntu server.

---

### Post by chagara on 2016-07-09
You should be able to have everything plug and play. I have USB drives, phones, tables and everything automounts without doing anything. What version are you using?

---

### Post by Tanarotte on 2016-07-12
Its not kernel. I accidently fixed the issue by . . . . .installing cinnamon on xubuntu and restarting. After doing so, not only i now have a system trey icon that is telling me that theres some stuff connected to usb ports, it auto mounts everything like it should (On both cinnamon and XFCE). Meaning for some stupid reason default installation of system didnt have all required components to begin with. ive also installed some automount app but that didnt seem to have any effect until i got cinnamon with all its dependencies. 

Speaking of which, good job xubuntu team.

---

