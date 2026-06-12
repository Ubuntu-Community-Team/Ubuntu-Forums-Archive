---
title: "Ubuntu + Suse + Vista"
date: 2007-12-24
forum: General Help
---

### Post by haymohenry on 2007-12-24
Hi All,
 
It's Christmas Eve and figthing with the machine. Anyway...
 
Problem:
Installed Vista Business on a new machine (OEM legal)
Ran Suse 10.3 Installer. Would not install cleanly and aborted.
Was left with a GRUB booter which wouldn't let me into either OS. Fixed it with bootrec.exe /fixmbr and fixboot from the Vista DVD.
A dual boot ertry remained:
[LIST]
[*]Vista (TM) Business
[*]SUSE 10.3 Installer[/LIST]No way to remove the obsolete Suse (Easy BCD).
 
Got an original CD from Ubuntu (Feisty) and installed that without a hitch. The boot menu changed to "**New Linux**" and it still asks for completion of the Suse installation.
On the menu: "*Boot installed system*" it starts up Ubuntu with a lot of error messages (Suse's).
Ubuntu does not let me access my NTFS hard disks (tried to install something called "ntgr 3" but to no avail).
 
Question(s):
How do I get rid of the old Suse installer?
How do I get a clean install of Ubuntu?
How do I get a simple dual boot menu back?
 
Saludos from Costa Rica and Feliz Navidad!
 
Haymo

---

### Post by LaRoza on 2007-12-24
> **haymohenry said:**
>  
Question(s):
How do I get rid of the old Suse installer?
How do I get a clean install of Ubuntu?
How do I get a simple dual boot menu back?
 
Saludos from Costa Rica and Feliz Navidad!
 
Haymo

0. I am not exactly sure what you did. Use GParted to wipe all the partitions (except the Windows one), and use the Super Grub disk to restore the Windows MBR. That should work

1. You should use the latest version of Ubuntu, which is 7.10. It has NTFS write support, let Ubuntu install GRUB which will also boot Vista.

2. Use Grub.

Merry Christmas!

---

### Post by haymohenry on 2007-12-25
Hi LaRoza,

thank you for the speedy reply!

Here was the course of action, step by step:
[LIST=1]
[*]I rebuilt the Vista MBR via Vista "Repair my computer". That worked, but did not remove the "Suse Installer" on the dual boot menu.
[*]As the Suse would not install (DVD check was OK) I deleted the Linux partition with G-Partition Live.
[*]Reformatted it with NTFS, as I was ready to throw the towel on Linux.
[*]The Dual boot menu would still remain with the "Suse Installer", a minor annoyance.
[*]As the Linux bug was still gnawing, after a few days I tried the Ubuntu (Feisty) install from an original (Canonical) CD.
[*]Gave it all the space on my 3rd HD (80 GB).
[*]Like said, that installation went without a hitch.
[*]A GRUB dual boot menu did NOT appear, but the second instance on Vista's dual boot now changed to "**New Linux**"
[*]Starting - or trying to start - Ubuntu takes me to an "*aborted installation*" menu of Suse.
[*]I have to haggle through those menus until I get to "Boot Linux from Hard Disk".
[*]Ubuntu starts, did all the updates to Gutsy (7.10) OK,  but refused to recognize my other two Vista HDs  (NTFS  / 160 GB each), nor would let me install the NTFS  read option which appeared  in the "Install software" menu, although  the check mark appears saying that it did.
[*]Went back to G-Part and erased / reformatted the Linux HD back to NTFS.[/LIST]I am now ready to start from scratch.

Thanks a lot for all your help in advance!

Haymo

---

### Post by bodhi.zazen on 2007-12-25
That is a lot of steps all at once, we should go one at a time.

Installation should be no problem.  I advise you use GRUB rather then the windows to boot. Grub should boot Vista + Linux with no problem.

Post install configuration should not be too hard. Here is how you mount and access various file systems :

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by haymohenry on 2007-12-25
Hi Bodhi,

thanks for the hints.

Before I plunge into a new installation of Ubuntu, please tell me - or anybody else - how to get rid of the old Suse installation message at boot-up once and for all.
It keeps popping up at every chance and there is no way to erase/delete it. I'm afraid it will conflict with the new GRUB and/or Vista's dual boot loader - as it did before. It remains like a root-kit virus. Where is that info? At "C:\nts"?

Saludos,

Haymo

---

### Post by haymohenry on 2007-12-28
Hi Folks,

after downloading the "Gusty" (7.10) DVD I tried one last time to reinstall Ubuntu.

Cleaned the 80 GB HD and gave it (Ubuntu) all the space. Did the requested updates and followed every step by the letter. Let the installation do GRUB as the boot manager.

Result:[LIST]
[*]Neither Vista nor Ubuntu would boot in all the possibilities available.
[*]The screen was "moved" horizontally by about 1/2" by the Ubuntu installation. Hmmm...
[*]Recovered the original Vista boot loader by "Repair" through the Vista DVD.
[*]Now I have an entry (besides Vista) called ***NeoSmart Linux***, which does nothing, but can't be removed (Easy BCD).[/LIST]I am deeply disappointed since I wanted to use Evolution Mail instead of Outlook.

Will wait until next year to see if something (really) useful and manageable comes up.

Happy New Year / Feliz Año Nuevo!

Haymo

---

