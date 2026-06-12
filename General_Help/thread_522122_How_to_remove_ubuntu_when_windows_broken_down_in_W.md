---
title: "How to remove ubuntu when windows broken down in Wubi"
date: 2007-08-10
forum: General Help
---

### Post by Futureking on 2007-08-10
Dear Friends,

I have not yet installed Wubi on my system because I have some questions about it.
Everyone knows that Windows is an Unstable Operating System. I also believe it because I face some trouble in about after 30 days after installing windows. So then I reinstall windows. 

My question is... 
If I reinstall windows or just remove the Wubi Virtual Disk file from my computer then what would happen. Will I see two names of OS i.e. Windows and Ubuntu or ubuntu automatically will be removed. Remember I am not removing wubi I am just removing its ubuntu file.

Another thing is that 
I have  a windows with wubi ubuntu installed on it. I face some problems in windows and I made a fresh install in it without formatting. Will ubuntu option will automatically removed from Boot time.

my last question is ...
Can I share files between ubuntu installed on wubi and files of physical harddisk having NTFS file system.

So Please reply so that I will install wubi and ubuntu.

---

### Post by clive_pearce on 2007-08-10
You can uninstall Ubuntu via the add/remove programs in Windows.

It will give you the option of saving the iso file you downloaded & something else. I can't remember what, but you can untick them to completely remove Ubuntu. 

Wubi.exe if you saved to disk will still be there. Only Ubuntu will be uninstalled & will be removed from the boot.ini file at startup.

If you do not delete the iso file when you uninstall, it will be there if you decide to re-install Ubuntu. 

If you reinstall Windows, unless you save the files, Ubuntu & Wubi will be gone.

While in Ubuntu, you can share files. It will see any other partitions.  In windows, Ubuntu is a series of folders on the C: drive. 
Try it.

:)

---

### Post by numbah_one's on 2008-01-09
help ubuntu crashed i think..

i installed wubi on my windows xp,ive used ubuntu on my laptop but couldnt get the 3d effects running..after i found out about wubi i tried it,iwas great, i decided to increase my disk space but using lvpm, i followed every step shown in the graphical guide,but after i reboot back to ubuntu i got 5 different options that i couldnt make any sense of..there was a recovery mode and also there was an original kernel, i tride using the original kernel but it crashed,

my xp machine has two partitions,C: & E:(these is where i installed wubi) and now i can't see drive E: when i boot to windows..

is there anything i could do to reverse the process? would removing wubi remove the ubuntu partition on my E: drive?how can i remove ubuntu from my machine?

---

### Post by ago on 2008-01-10
> **Futureking said:**
> If I reinstall windows or just remove the Wubi Virtual Disk file from my computer then what would happen. Will I see two names of OS i.e. Windows and Ubuntu or ubuntu automatically will be removed. Remember I am not removing wubi I am just removing its ubuntu file.
If you install wubi on C:\ and reformat C:\ there will be no trace left of Wubi. 
If you install wubi on D:\ and reformat C:\ there will no longer be a dual boot option, but you will have to manually delete the D:\ubuntu folder
If you want to keep wubi when installing windows, copy the \ubuntu folder somewhere else together with any C:\wubildr* file, then after installing windows put them back, finally add a boot entry to launch wubildr.mbr

> I have  a windows with wubi ubuntu installed on it. I face some problems in windows and I made a fresh install in it without formatting. Will ubuntu option will automatically removed from Boot time.
Possibly but in this case you only need to add 1 line to C:\boot.ini

> my last question is ...
Can I share files between ubuntu installed on wubi and files of physical harddisk having NTFS file system.
The windows drives can be accessed r/w within wubi, any file in there can obviously also be accessed by windows.

---

