---
title: "start-up script mounting parts requires sudo"
date: 2015-02-09
forum: General Help
---

### Post by keith14 on 2015-02-09
Hi,
Trouble auto mounting partitions on drive at stat-up.
 I open a ticket close to this and closed it, however; I ran into new problem.
 I use gawk script which parses "udisks --dump" and with given options will generate:
sudo mkdir /media/keith/WinXp ; sudo mount /dev/sda1 /media/keith/WinXp
sudo mkdir /media/keith/Win7 ; sudo mount /dev/sda5 /media/keith/Win7
sudo mkdir /media/keith/Vault ; sudo mount /dev/sda3 /media/keith/Vault

The script is good, or works once boot-up occurs but adding this script to Menu-Preferences-System Settings
fails to mount the 3 partitions. script: getdrv -ma -np  (mounts all mountable drives w/o print status, generating the "sudo" lines above

I don't get prompted for sudo password, is this what I need to address?
Is this script being run as a su when placing it in start-up scripts?

want to selectively mount various partitions at start-up.
thanks,
keith

---

### Post by ajgreeny on 2015-02-09
I am not certain exactly what you're trying to do in spite of your description of what you've tried, but I am pretty certain it will be much easier to add a line for each partition you want to mount at boot to /etc/fstab.

Let's have more info about those partitions from the output of commands ```
sudo parted -l
sudo blkid -c /dev/null
```

---

### Post by keith14 on 2015-02-10
Think we got on wrong track; from the bottom: want to selectively mount various partitions at start-up.
How to run: sudo mkdir /media/keith/WinXp ; sudo mount /dev/sda1 /media/keith/WinXp      at start-up?
I've add this to startup menu as required but partition WinXp fails to get mounted at start-up.

if you were heading toward modifying fstab to run mount -a, I would rather have the two commands above
executed at start-up. Should this prove impossible then I may need to re-look at fstab mods.

[COLOR=#000000]

[/COLOR]

---

### Post by ajgreeny on 2015-02-10
You can't run scripts that need root permissions (sudo) in your usual user's startup-applications list, and I still don't fully understand why you want to selectively mount them.

Wwhat is the problem with adding the partitions to fstab and mounting them automatically at boot, or even using the noauto option in the appropriate fstab line which should mean they are no mounted each time.
Do a search of **fstab noauto** to sort out the possibilities.

---

### Post by keith14 on 2015-02-17
Hi,
 I did not want to modify fstab. There are several reasons but Y do this when all partitions on your pc are mounted yet fstab only lists root and swap?
Resolve:
[COLOR=#2E8B57][FONT=Monaco]udisksctl [un]mount -b /dev/disk/by-label/partition_label
[/FONT][/COLOR][COLOR=#2E8B57][FONT=Monaco]udisksctl [un]mount -b /dev/disk/by-uuid/partition_uuid
[/FONT][/COLOR] [COLOR=#2E8B57][FONT=Monaco]
[/FONT][/COLOR]Works,  NO sudo needed and maybe placed in start-up.
[COLOR=#2E8B57][FONT=Monaco]thanks,
keith
[/FONT][/COLOR]

---

