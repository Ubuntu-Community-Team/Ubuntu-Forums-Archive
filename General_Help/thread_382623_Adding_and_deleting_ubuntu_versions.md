---
title: "Adding and deleting ubuntu versions"
date: 2007-03-12
forum: General Help
---

### Post by kindafunnylookin on 2007-03-12
My two HDD's are listed below. What I want to do is[LIST]
[*]install Dapper on the 160GB HD (set as primary) where the Edgy is now. For that move the most important thing is getting all my Firefox settings from Edgy into the new Dapper.
[*]Then I want to install Edgy to the 40GB HD (set as secondary) with the same Firefox settings.
[*]The tools I have to work with are:[/LIST][LIST=1]
[*]System Rescue disk
[*]Live CD's for each of the  OS's
[*]An 80GB USB HDD[/LIST]I have no idea of where to start and I'm sure that Grub will throw in a surprise or two for me. Any and all help will be appreciated.
-Peter
```
peter@edgeville:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4858    39021853+  83  Linux
/dev/hdb2            4859        4865       56227+   f  W95 Ext'd (LBA)
peter@edgeville:~$ 
```

---

### Post by denver on 2007-03-12
If youre only concerne are youre personal settings then all you have to do is copy the entire ~/ ( /home/<user>/ ) folder to a safe location. All settings to all apps you ever used are stored in youre home folder. After you saved youre files its safe to do a fresh install of both OS's and copy the personal files back in /home/<user>/. When you install the second OS on youre machine, GRUB will automaticaly locate other OS's and add them to the list. If, on the other hand, you have services installed ( apache, MySQL, etc ) and you wish to move them it gets a bit more complicated.

In order to avoid loosing settings and data in the future you could create a separate partition on one of youre HDD's and mount it as /home. This will spare you from having to backup youre entire data every time you want to reinstall. You can also mount the same partition on both OS's as /home and avoid having to have 2 sets of settings.
One setting made in one OS will reflect in the other as both will be using the same /home.

---

### Post by paparucino on 2007-03-12
> **denver said:**
> 
One setting made in one OS will reflect in the other as both will be using the same /home.
I prefere these situation: a partition dedicated to data, two partitions for OS plus USB key.
/home partitions stay were they are :-)
I've moved all my important data and conficurations in the bigger partition then I use symbolic links to reach that partition from everywhere
The only difference is that I don't touche default installations.

---

### Post by denver on 2007-03-12
That is another way to do it but it requires more work then the first suggestion. You have to create symbolic links for each folder ( .gaim, firefox, mozilla-thunderbird, etc ). Creating one big partition and mounting it when installing the OS's takes minutes and is transparent to the user after the installation. Not to mention that when you save a file to your Desktop, it gets written to the mounted partition so after a clean install of the OS, that file will still be on your Desktop if you choose to mount the same partition in your /home/ folder.  You also get to keep your wallpaper, shortcuts and everything you worked hard to customize.

But in the end, its up to each and every one of us to decide which method is best for him/her.

---

### Post by kindafunnylookin on 2007-03-13
Thank you all, I will set up a separete /home partition and then reinstall dapper using that new partition as part of the install.

---

