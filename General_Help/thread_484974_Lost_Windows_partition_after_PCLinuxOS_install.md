---
title: "Lost Windows partition after PCLinuxOS install"
date: 2007-06-26
forum: General Help
---

### Post by keithk50 on 2007-06-26
I have installed PCLinuxOS onto my HD after taking space from the Windows partition.   I left the XP partition plenty of free space.   Although the install was, to say the least, much different to Ubuntu I managed to install PCLinux onto a 15GB partition with swap.   This said it was a bit of chore getting PCLinux onto the grub menu in order to boot it.   I id this by adding a script to the menu.lst file in Ubuntu.   
The problem is that now my XP partition will not boot and gives me this message when I try:

"Windows could not start because the following file is missing or corrupt:   <Windows root> \system32\hal.dll
please reinstall a copy of the above file"

The Windows grub recovery entry just hangs when chosen and all options after presing F8 do not respond.
To be honest it is not the end of world as I have all my Windows stuff backed but it would be nice to fix it!   

The other problem (sorry) is that Gparted does not show any of my partitions as it did before.  It just shows the whole drive as 'unallocated'.   Has the windows problem caused this?
What is strange is that the equivelant of Gparted in PCLinux sees all my partitions and mounts them!
Is there anyway to get my Ubuntu (Gparted) to 'see' my partitions, size etc.
I am not so bothered about the XP prblem but would love to hearfrom anyone that can help on the Gparted issue it would be appreciated.   Thanks.

---

### Post by mikewhatever on 2007-06-26
The PCLinux help forum is here [http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26)
I do not want to discourage you, never used pclinux, so do not know how to help, but still, your question is not even remotely connected to Ubuntu, the OS we more or less discuss here.

---

### Post by keithk50 on 2007-06-26
Mikewhatever.   I have been a Ubuntu Forums member for 4 months.   I use Ubuntu every day.   The reason I asked a question on my forum was purely from the Gparted (Ubuntu Gnome Software) problem I have.   So sorry I have offended you!   Dont worry, I know where the PCLInux forums are.   No need for the link.   Have a good day.

---

### Post by mikewhatever on 2007-06-26
I did not say you have offended me, in fact, you did not. Take it easy.;)

---

### Post by encho on 2007-06-27
What you probably did is changing the partition order or inserting another partition before windows one. Same thing happened to me with ubuntu few months back. Just launch the livecd again and try to reverse the partition order.

Also, did you use external tools such as acronis or partmanager? If nothing helps, and the order is correct, try fdisk:
sudo fdisk /dev/sda
Press x for advanced, than f for fix.
It will fix your partition order (just the info, not the real partitions) if corrupted.

What I do when starting from scratch is to create 4 partitions: 1. windows, 2. linux, 3. home partition, 4. swap. It is even ok to add /boot partition before windows, but it shouldn't be too large - 256mb is more than enough.

So first check is your win partition still on the same position (probably /dev/sda1).

Hope this helps.

---

### Post by keithk50 on 2007-06-27
Hi encho. Sorry for the late reply.  Many thanks for your reply, it was welcome advice.   I have not had a chance to try your suggestions but intend to very soon.   My mistake was to use the Partition Editor within the live CD of PCLinux!!   I should have used GParted on the Ubuntu live CD to take the required space from my windows partition and then do the install.   Gparted is a much better application and has worked well for me during my short time with Ubuntu.   You live and learn.
To be honest I was not to bothered about not having windows.   It was due to be 'wiped' anyway.   It will not be missed.   Anyway, I shall try out your suggestions and take it from there.   Thanks again.       Keith.

---

