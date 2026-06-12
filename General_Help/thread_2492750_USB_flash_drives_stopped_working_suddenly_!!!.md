---
title: "USB flash drives stopped working suddenly !!!"
date: 2023-11-21
forum: General Help
---

### Post by asabhish on 2023-11-21
[SIZE=4]Hi All! I was able to use all my flash drives in my Ubuntu desktop, when one fine day, I found them NOT working/mounting. The drives work just fine in my windows desktop and other Ubuntu desktops as well. Based on my google search to try and troubleshoot the issue, I gather that the following information will be imporatnt for you to make any further comments:

1) The lsblk command doesn't show my pen drives.

[/SIZE]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293101&stc=1[/IMG]


[SIZE=4]2) The lsusb command shows my pen drive (Sony flash drive):
[/SIZE]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293102&stc=1[/IMG]


[SIZE=4]3) The dmesg command also shows my pen drive (Manufacturer: Sony)

[/SIZE]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293103&stc=1[/IMG]


[SIZE=4]4) The disks utility doesn't show my pen drive at all.

My OS is Ubuntu 22.04 and the kernel version is 6.2.0-36-generic (not sure if this is pertinent to the issue at hand). I am not an expert in Ubuntu (far from it) but am comfortable with basic usage on it. Any insights from your side (before I go about formatting my desktop) is required please.[/SIZE]

---

### Post by MAFoElffen on 2023-11-21
Have you tried powering down, then booting from cold (yet)? Then retest it.

---

### Post by asabhish on 2023-11-22
Yes I have. Many a times actually.

---

### Post by oldfred on 2023-11-22
What format are flash drives, NTFS, FAT or ext4?
If either of Windows formats, did you have Windows fast start up on? Note that Windows may turn fast startup back on with updates.
Fast start up sets hibernation flag, and then the Linux NTFS driver will not mount NTFS partitions to prevent damage & loss of files.

---

### Post by TheFu on 2023-11-22
In addition to what both oldfred and MAFoElffen suggested above, be certain the file system support packages are installed on the system for the file systems involved.  NTFS and exFAT and FAT32 would have different packages.  For some releases, those were installed by default. Perhaps, for your ubuntu flavor, that isn't the situation anymore or some other package manager issue cause them to be removed from the system.

If I knew the exact names, I'd post them. Sorry.  They are usually something like ntfs3g-tools or ntfs3g-utils ... so try those for exfat and fat32 as well.

Of course, if you went with a native Linux file system for flash storage, like f2fs, then you'd need the f2fs-utils package (or is it f2fs-tools?).

And if you have issues accessing the files using some GUI file manager, verify that the helper and other dependencies for your specific file manager for the exact file system to be mounted are installed.  I think gvfs-something and gio-something are needed with 2+ packages, but don't quote me. IDK.  I'm a command line mount person.

---

