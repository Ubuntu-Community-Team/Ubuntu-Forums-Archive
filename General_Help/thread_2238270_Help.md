---
title: "Help"
date: 2014-08-06
forum: General Help
---

### Post by Crimsonangel on 2014-08-06
I hoenstly dont even know what to title this problem. I installed linux on a spare hard drive in attempt to access some files from another failing hardrive since windows couldnt. It was a success i coppied the files from the failed hard drive to the linux home folder, then shut it down to remove the bad hard drive. The next day i go to boot up the pc to access the files and transfer them to a flash drive, linux no longer boots it goes to a black screen saying to reboot and select proper boot device, when i clcik f8 on startup the only thing that shows up is the hard drive that linux is installed on (the only drive i have in at the moment), I then spend the next 8 hrs trying to figure out a solution, ive used the live cd to try boot repair multiple times but the only thing it manages to do is load me to a black screen with a grub command . I tried accessing the files on the linux hard drive through the live cd but im unable to copy them because i lack the privlages and i cant figure out if there is even a way for me to gain privalges. at this point im about to give up and just accept the files as lost. ive tried repairing and reinstalling grub through multiple methods ive read up, i get absolutely no results.

The hard drive is formated GPT and my computer as a UEFI bios

---

### Post by Impavidus on 2014-08-07
It's easy to get the privileges on a live disk. Open a terminal and run```
gksu nautilus

#OR

sudo -i
#Followed by
nautilus
```
and the file manager will open with root privileges. If it asks for a password, just hit enter.

You could have used the live disk in the first place to copy the files to an external drive, without installing Ubuntu.

Edit: When installing Ubuntu, grub (the boot loader) is installed on the first hard drive. You removed that drive, which gave the  "select proper boot device" message. Boot-repair installed grub on the second drive, then your only drive, but couldn't find the partition with the kernel image. This gave the grub rescue prompt.

---

