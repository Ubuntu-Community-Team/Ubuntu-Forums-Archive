---
title: "Can't access a partition"
date: 2006-12-27
forum: General Help
---

### Post by Katryx on 2006-12-27
Background: reinstalled Ubuntu (from 6.06 Dapper liveCD) twice for fresh starts while trying to set up the latest nvidia driver. I arranged the hard drive so that there is a 106GB partition containing the entire old OS installation and all my personal files (hda1), a 77GB partition for the new OS installation (hda3), and a 4GB of swap (hda5).

The first installation to hda3 went smoothly. It, and hda5, were reformatted. hda1 had a little bit of free space on it, but the partitioner and installer left it untouched, just as I wanted. After installation was complete, there was a shortcut to hda1 automatically placed on the desktop, and there were even options for loading into the OS contained on hda1 in the boot loader.  I could access hda1 without any problem, and the files therein seemed intact.

The second installation is having some issues. Again, I reformatted hda3 and hda5 for the OS reinstall. I set the mount point for hda1 to be /dev/hda1, because the mount point field for it was blank and that didn't seem right(?). During the "copying files" segment of installation, there were a couple of pop-up notices about hda1 being 100% full. This brings up two questions: what happened to the free space on hda1, and why was the installer worrying about a partition it had no instructions to interact with (except for my setting the mount point to /dev/hda1)?

Post-reinstallation, I can't access hda1. Clicking it in Computer causes an "unable to mount the selected volume" error:
> mount: only root can mount /dev/hda1 on /dev/hda1

:-k 

Upon opening Disks Manager from System -> Administration, there is a pop-up notification about "/tmp/disks-conf-hda1" being 100% full. Info about hda1 in Disks Manager:
> Device: /dev/hda1
Filesystem: Extended 3 (ext3)
Access Path: /dev/hda1
Size: 106.01 GiB (Free space not available)
Status: Inaccessible
There is an "Enable" button by the status, but it does nothing except cause the window to flash briefly. "Browse" button is greyed out.

"sudo mount /dev/hda1" produces this:
> mount: mount point /dev/hda1 is not a directory

---

### Post by po0f on 2006-12-27
Katryx,

It looks like it's trying to mount /dev/hda1 onto itself.  Try this:
```
[FONT="Courier New"]$ sudo mkdir /media/hda1
$ sudo mount /dev/hda1 /media/hda1[/FONT]
```

[EDIT]

If that works, can you post the entry for /dev/hda1 from /etc/fstab?

---

### Post by Katryx on 2006-12-27
Thank you, that did work. :)

```
/dev/hda1       /dev/hda1       ext3    defaults        0       2
```

---

### Post by po0f on 2006-12-27
Katryx,

That line should be:
```
[FONT="Courier New"]/dev/hda1       /media/hda1       ext3    defaults        0       2[/FONT]
```

---

