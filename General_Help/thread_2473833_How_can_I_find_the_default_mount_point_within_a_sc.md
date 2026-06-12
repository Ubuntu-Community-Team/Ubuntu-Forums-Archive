---
title: "How can I find the default mount point within a script?"
date: 2022-04-15
forum: General Help
---

### Post by Paddy Landau on 2022-04-15
I believe that the default mount point for most systems is /run/user/$UID, but that in Ubuntu, it's been changed to /media/$USER. Presumably, some systems have yet another default mount point.

For example, in Ubuntu, if I plug in a USB drive and use either Nautilus or Gnome Disks to mount a partition, it is mounted in /media/$USER.

How I tell, in a script, what the default mount point is? Or is it more complicated than that?

---

### Post by TheFu on 2022-04-15
I think ubuntu uses the udisksctl (also called UDisks2) for this.  The manpage simply says:
```
       mount
           Mounts a device. The [B]device will be mounted in a subdirectory in
           the /media hierarchy[/B] - upon successful completion, the mount
           point will be printed to standard output.
```
The manpage claims that *only safe options are allowed* for mount are allowed, but doesn't say what those are.

You can have complete control over any mount point by setting up the manual location desired using the file system LABEL.

Say you have a USB HDD, with 3 partitions on it.  One is ext4, another is exFAT and the last is NTFS.
Go into gparted, select that HDD (upper right corner), then the list of partitions will display in the main window.
Select each in turn, right click and choose "Label".

Say we label them as .... BIG-DATA, EXFAT, and NTFS-Junk, respectively.
No use **sudoedit /etc/fstab** and add 3 lines:
```
LABEL=BIG-DATA  /media/Data  ext4   nofail,noatime,errors=remount-ro                                                                   0  2
LABEL=EXFAT     /media/exfat ntfs   nodev,windows_names,nosuid,noatime,async,big_writes,nofail,uid=1000,gid=1000,fmask=0002,dmask=0002 0  2
LABEL=NTFS-Junk /media/junk  exfat  dirsync,nodev,windows_names,nosuid,noatime,async,nofail,uid=1000,gid=1000,fmask=0002,dmask=0002    0  2
```

Notes:
[LIST]
[*]There are 6 fields. Spaces inside a field are not allowed.  The options field CANNOT have any spaces.  The field separator is a space.  1 or 50 spaces are the same.  I tend to use enough to make the fields line up in the same column in my fstab file.
[*]Each line starts with a LABEL= and that line cannot be wrapped. It must be 1 line.  
[*]The last 2 fields, "0   2" are for dump (an old-school backup method) and fsck stuff. In my examples, no fsck will be run, ever.
[*]For non-native Linux options which force an owner, group and permissions are needed.  I've used uid 1000 and gid 1000, since that will be the first user's uid/gid (the user who installed the system).  
[/LIST]

That's the best answer.  You can use UUID= instead of LABEL= for storage too.  This completely avoids the device name problem.  The requirement is that any LABEL be unique in a system. Don't expect to use the same LABEL for every flash drive and have it work when more than 1 is connected.  It will work fine if you manually ensure only one device with the same LABEL is ever inserted. I just find the label's easier for humans since they convey useful information lacking in UUIDs.
I think there's a way to allow normal users to mount storage spelled out in the /etc/fstab.  The 'user," option allows that. This option allows a normal user to mount and umount storage. The manpage for fstab says this:
```
       The fourth field (fs_mntops).
              This field describes the mount options associated with the filesystem.
...
              user   allow a user to mount
...
```


The fstab can be used with a script to put mounts exactly where you want them too, if the username has sudo rights. If the mount location is in the fstab already, the mount command in a script needs only say the mount location.
```
sudo mount /media/Data
```
tells the mount command to get the options from the fstab file with that mount location specified.  If there is a 'user' in the options, then sudo isn't needed, but I bet that any specific uid/gid options will be ignored or the mount will fail. 

There are some other mount tools that hide the details. I've never used those (actually, they are purged from all my systems if installed) ... but **usbmount** is one.  Usbmount has been abandoned by the author, but mount stuff doesn't change too often, so it probably still works.
fuse / fusermount, gio mount, and gvfs-mount are others. Use at your own risk.

Sorry. Probably not the answer you really wanted. I appears that if udisks2 is used, then /media/ is where the mounts will go unless a manual override is provided in the options.

---

### Post by Paddy Landau on 2022-04-15
Thank you for the detailed explanation. It's not quite what I want, because this is to do with removable disks.

I want to stick to the standard, whatever the standard happens to be on that particular system. That's why I want to know what the standard is.

Knowing Linux, there's a way to find out, but I don't know how :)

---

### Post by TheFu on 2022-04-15
If udisks is used, then it will mount under /media/
I think all the major distros with a GUI use udisks now and have for a few years.
There are many ways to mount stuff ... but in the end, they all actually use 'mount' as the command.

Removable disks can be specified in the fstab.  The nofail option addresses when they are missing so nothing bad happens on the system, but all the mount options are still under your control.

I actually use **autofs**, not the fstab for this, but after being scolded yesterday, thought I'd leave that out. Some people would consider it too complicated, but it works fantastic for USB storage.

---

### Post by vanadium on 2022-04-16
Where these mounts are done is controlled by udev rules. The system default rules are under `/lib/udev/rules.d`. One can override rules and defaults by  creating rules under '/etc/udev/rules.d'. Sorry, however, that I cannot be more specific on where this configuration is exactly to be found. Perhaps you will figure out in combination with this information on Arch wiki: [https://bbs.archlinux.org/viewtopic.php?id=259493](https://bbs.archlinux.org/viewtopic.php?id=259493).

---

### Post by Paddy Landau on 2022-04-16
> **vanadium said:**
> Where these mounts are done is controlled by udev rules. The system default rules are under `/lib/udev/rules.d`
That was interesting, thank you, but didn't take me closer to the answer. None of the 121 files within [FONT=courier new]/lib/udev/rules.d[/FONT] contains the string [FONT=courier new]/media[/FONT].
> **vanadium said:**
> Perhaps you will figure out in combination with this information on Arch wiki: [https://bbs.archlinux.org/viewtopic.php?id=259493](https://bbs.archlinux.org/viewtopic.php?id=259493).
The thread asks the same question as I do — well discovered! — but, unfortunately, it didn't come to a conclusion :(

---

### Post by HermanAB on 2022-04-16
If you want to see the current active mounts, look in /etc/mtab

---

### Post by Paddy Landau on 2022-04-16
> **HermanAB said:**
> If you want to see the current active mounts, look in /etc/mtab
Thanks. That's the same as the [FONT=courier new]mount[/FONT] command. It's not what I'm after, though.

---

### Post by vanadium on 2022-04-16
> **Paddy Landau said:**
> That was interesting, thank you, but didn't take me closer to the answer. None of the 121 files within [FONT=courier new]/lib/udev/rules.d[/FONT] contains the string [FONT=courier new]/media[/FONT].

We do not expect that. It is, according to the Arch post, the setting ENV{UDISKS_FILESYSTEM_SHARED} that controls whether /run or /media is used. However, also no such setting is there.

Found some additional info here: [https://github.com/coldfix/udiskie/issues/51](https://github.com/coldfix/udiskie/issues/51)

> Ok, I finally took the time to look at the UDisks2 source to see if anything can be done about this issue. In the function src/udiskslinuxfilesystem.c:calculate_mount_point one can see that the locations are indeed hard coded. Setting the UDISKS_FILESYSTEM_SHARED environment variable (for the UDisks process, not for udiskie!) will yield the old behaviour, i.e. mount everything in /media.

 Ubuntu uses "1" as default, so the question indeed remains where that is being set. That option may just be compiled in, so then there may be no way to read the default. It depends on why you would need to determine this default - perhaps there is an alternative approach if you would let us know problem X?

---

### Post by Paddy Landau on 2022-04-16
> **vanadium said:**
> It depends on why you would need to determine this default - perhaps there is an alternative approach if you would let us know problem X?
Thanks for all of the details.

I have a set of scripts that mount partitions from various external drives (some encrypted, some not), and some LUKS-encrypted files, according to a number of user-driven parameters.

They work well, but I wanted to tweak the scripts to use whatever the default is rather than just assuming. That's why I wanted to know. It's not vital for me, but it would be cleaner and better programming practice to adhere to standards.

Something that I have learned since I started this thread is that there may be better ways to mount than the way that I'm have been using; specifically [FONT=courier new]udiskctrl[/FONT], which I hadn't known about before.

---

### Post by vanadium on 2022-04-16
Indeed, mounting using `udiskctrl` will do it "the way the desktop does", and mount these drives in the default locations of the system.

---

### Post by Paddy Landau on 2022-04-16
> **vanadium said:**
> Indeed, mounting using `udiskctrl` will do it "the way the desktop does", and mount these drives in the default locations of the system.
Thank you. I'll definitely look into replacing my current method with this!

---

### Post by TheFu on 2022-04-16
> **vanadium said:**
> Where these mounts are done is controlled by udev rules. The system default rules are under `/lib/udev/rules.d`. One can override rules and defaults by  creating rules under '/etc/udev/rules.d'. Sorry, however, that I cannot be more specific on where this configuration is exactly to be found. Perhaps you will figure out in combination with this information on Arch wiki: [https://bbs.archlinux.org/viewtopic.php?id=259493](https://bbs.archlinux.org/viewtopic.php?id=259493).

Good idea, but not the answer.  There are no rules in there that exist which do anything more than pass the storage to udisks2.  **udisks2** only mounts to /media/, unless an override happens.  In every case I've researched, all of those overrides are just as cumbersome as my post above for modifying the fstab, but less standard.  Nobody would look in the udev directories to control mounts.  That just isn't done.  They will look in the **fstab** or in the config files for **autofs**.  Those are the expected locations for mount options.

If someone wanted to change the default location, I think editing the source for udisks2, compiling, linking, then screwing around with apparmor would be necessary to ensure the new target directory would have similar access controls.

---

### Post by Paddy Landau on 2022-04-16
> **TheFu said:**
> If someone wanted to change the default location, I think editing the source for udisks2, compiling, linking, then screwing around with apparmor would be necessary to ensure the new target directory would have similar access controls.
This might be what Canonical has done for Ubuntu, because Ubuntu doesn't use the standard /run/…

---

