---
title: "How can i Have both XP and Ubuntu?"
date: 2007-10-04
forum: General Help
---

### Post by Nirer on 2007-10-04
Well before Ubuntu I had XP and wanted to have them both (on 1 computer) and so on 1 hard disc (C:\) i would have XP and on the other (D:\) I would have XP. I tried to do that but there was an error or something (don't remember exactly), so can anybody give me a some kind of tutorial on how to install them both on 1 computer? (Intel) Thx!

---

### Post by Robin T Cox on 2007-10-04
There's a tutorial here:

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by usif on 2007-10-04
Hey man
Your best bet is to dualboot Ubuntu on Win XP
to do that you need to re-partition your hard drive, i.e partition 1 has win XP and partition 2 Has ubuntu Installed and partition 3 Is used as a swap, etc

Some good Partitioning software to use is Partition Magic 8 by norton 

Alternatively you can boot up the live cd and use the partioner in the installer, but remember to check partition sizes and if for instance drive C: had windows installed and you wanted linux on drive D:, then you would want to backup everything on Drive D first, etc


You can use this guide: [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by notwen on 2007-10-04
I would recommend instaling WinXP first , this will save you from having to repair Windows MBR, if you installed Ubuntu followed by WinXP.  back up any data you wish to keep, install Windows XP formatting the whole drive.  Pop in the Ubuntu LiveCD and use it's built-in partition manager during the installation process to resize your Windows partition(remember to leave enough room on your Windows partition for files you may want to add later) and Ubuntu will also install GRUB which will automatically pick up your WinXP installation and upon rebooting you will be greeted by GRUB giving you the option to boot into Ubuntu or WinXP.  The guide usif linked to should explain everything for you step-by-step.  Good luck and be sure to post back if you run into any issues.  =]

---

### Post by Nirer on 2007-10-04
thx guys ill try this tomorrow :)

---

### Post by Elotero on 2007-10-04
I would recommend instaling WinXP first , this will save you from having to repair Windows MBR, if you installed Ubuntu followed by WinXP.


I did it... Installed Ubuntu over xp..so now all i have is Ubuntu... and i would honestly like a choice. Can you point me in the direction of a tutorial of how to get XP on Ubuntu? I have read in softpedia to use virtual box.. is this the same? or is a dual boot more stable?

---

