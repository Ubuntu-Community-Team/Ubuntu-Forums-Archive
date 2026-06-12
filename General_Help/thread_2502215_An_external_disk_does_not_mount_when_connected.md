---
title: "An external disk does not mount when connected"
date: 2024-11-05
forum: General Help
---

### Post by carlos-euphoria on 2024-11-05
Hello everyone!
Ubuntu 24.04.1 LTS and in 24.10 . Who else has problems with auto-mounting external disks? I connect the disk via USB, the signal of the connected device, the nautilus displays this disk, but when I try to click on it, it writes the error &#8220;Unable to access Jet Transcend....Error mounting /dev/sdb1 at /media/user/Jet Transcend: Wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error&#8221;. The disk is NTFS. But when I mount it with my hands in the terminal, everything mounts. I tried different disks and SSDs.

---

### Post by TheFu on 2024-11-05
If you can mount it using terminal commands, then you can setup the /etc/fstab to use the automoutd method of systemd.

Of course, you can also use autofs, but that's more complicated.  Autofs will umount the file system automatically when there aren't any more open files for 1-3 minutes after the last file on that file system is closed.

Something like this:
$ **sudoedit /etc/fstab**```

# add a line to the fstab:
LABEL={whatever the label is}    /media/Jet  ntfs  nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002,x-systemd.automount,x-systemd.idle-timeout=120s,noauto      0     2
```

Lots of options to ensure it works well, better than the way any GUI tool mounts it.  If you don't have a LABEL, set one.  If it has spaces, you'll need to quote it, the label, that is.

# tell systemd's fstab tool to check for changes ....
**sudo systemctl daemon-reload**

Next, if the HDD is USB connected, do anything to access  /media/Jet  and it could be mounted for you automatically.  If the USB HDD isn't plugged in, you'll get an error, eventually.  I've assumed the primary UID and GID are both 1000.  If that isn't to your liking, use the needed uid/gid numbers.

---

### Post by carlos-euphoria on 2024-11-06
Thank you for your help! I solved this issue as follows:

Open **GNOME Disks**. To do this, press **Super** (Windows key), type &#8220;Disks&#8221; and select a program.

Select your USB drive in the left pane.

Click the &#9881; (settings) icon under the partition you want to mount automatically and select **Edit Mount Options**.

Turn off User Session Defaults and set Mount at system startup to on.

Click **OK** and restart the system to activate the changes.

---

### Post by TheFu on 2024-11-06
When you finally decide that access is slow, you'll know where to find the options to speed it up above.
After the system it hacked, you'll find the options to prevent some attacks too - above.

---

