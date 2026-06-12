---
title: "Hardy upgrade - personal file dissapeared"
date: 2008-05-03
forum: General Help
---

### Post by arthurbr on 2008-05-03
Hi,
I have two HD one with win.. the other with Ubuntu and I use GRUB
after upgrading to HH I rebooted. GRUB was there all right but showed only the 7.10 kernel.
I booted on that one, had my logon screen, logged on and got a message that my personal folder /home/myfolder did not exist.
I rebooted on the life CD but the home folder did contain my personal file?
Can anybody help ?
Very much appreciated

---

### Post by warjowuch on 2008-05-03
Hi there,
I guess you had the same trouble as my wife had, so I assume you have got the same situation.
Your home was on the second drive. One of your drives is an IDE-device, while the other is a S-ATA drive.

THe kernel used in Hardy now identifies all HDD's as sdx devices. So while a few weeks ago, the IDE-drive was a hdx device, it now turned into a sdx-device.

So, the solution might be very simple.
Install gparted, and identify your drives.
Note for yourself on which drive is what. Like this:
/home on /dev/sda1
/ (root) on /dev/sdb1
et cetera.

Now, go to a terminal and type sudo gedit /etc/fstab
then, change the entries for your hdd's until they are correct.

Reboot and enjoy.

I know, it sound simple, but be careful, make yourself really sure that the information on each drive, and the configuration in fstab are correct.

If you still have questions, or if I am wrong in my assumption of your computer-config, please post back here with the stuff you DO have. :-) Good luck!

---

### Post by Rainstride on 2008-05-03
your harddrive might be failing, i would sugest backing up your files to the second one just in case thats the problem, cause if it completely fails you won't have a second chance. there are programs to check drive integrity. try this, [http://support.wdc.com/download/index.asp?cxml=n&pid=36&swid=3](http://support.wdc.com/download/index.asp?cxml=n&pid=36&swid=3)  under the selection boxes theres a download button. its for windows.  BACKUP BEFORE TESTING, if your drive is bad it might give out in the middle.

---

### Post by arthurbr on 2008-05-04
Hi,
thx for your answer. We're having a very long week end here so I couldn't answer earlier.
My two HD are IDE, and the funne thing is, while I can see my home/username from the live CD, when I boot normally and use the lind command the home directory is empty

---

### Post by arthurbr on 2008-05-04
Hi,
thx for your answer. We're having a very long week end here so I couldn't answer earlier.
My two HD are IDE, and the funne thing is, while I can see my home/username from the live CD, when I boot normally and use the line command ( cd home then dir)  the home directory is empty

---

### Post by DaddyX3 on 2008-05-04
One of my multi-boot distro's completely lost my /home/username folder all together while "importing settings" durring install of Hardy, so I know how you feel. There is something very wrong with the installer. I have seperate partitions for the /home and /backup (personal preference) and upon importing my settings from my other user (also Ubuntu distro) it left my /home partition but completely deleted my actual users folder!!! What a pain!

---

### Post by arthurbr on 2008-05-05
Thank you for your answers. I'll check it out ASAP.

---

