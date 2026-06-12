---
title: "zulucrypt GUI: how to navigate to another harddrive?"
date: 2018-01-12
forum: General Help
---

### Post by k28 on 2018-01-12
i want to navigate to another harddrive so i can create a encrypted  container on it. how do i do it? when i go to "create container in a file" i can just navigate to "my computer"> after that there is just one harddrive selectable and that is he one where ubuntu is installed.  the harddrive i want to navigate to is sda3. i thought maybe i have to look in the dev folder but there is no sda3 folder in it. propaply im wrong with this anyways.

thx!

---

### Post by Holger_Gehrke on 2018-01-12
In Unix-like operating systems file systems on devices get mounted into directories. One filesystem (the "root drive") contains the main directory "/" of the whole tree, all other drives get mounted in subdirectories of that system. Where drives go is partially predefined (but adjustable ...) and partially the system administrator's (that would be you, in this case) choice. In Ubuntu if it's a hot-plugged external device it will automatically get mounted to /media/"YourUsernameHere"/"FileSystemLabelOrUniversallyUniqueID". If it's a partition on an internal drive that existed at the time of installation, then the installer probably set up some mount point for it and the drive will be visible in the side bar in the file manager and have an item "mount device" in it's context menu. If it's a new drive (or a new partition) you might want to take a look at the page "[InstallingANewHardDrive"]("https://help.ubuntu.com/community/InstallingANewHardDrive?action=fullsearch&value=linkto%3A%22InstallingANewHardDrive%22&context=180") in the wiki, especially parts 5ff of that page about creating mount points and mounting.

Holger

---

### Post by k28 on 2018-01-15
thx for the reply. its an internal drive with windows on it which was present while i installed ubuntu to another harddrive.

when i go to "other palces" with the explorer i can see the drive and have RW. i think this means that its mounted? unfortunatly when i go to **[COLOR=#000000]/media/"YourUsernameHere"/ [/COLOR]**there are no drives present. same with the explorer of zulucrypt.

---

