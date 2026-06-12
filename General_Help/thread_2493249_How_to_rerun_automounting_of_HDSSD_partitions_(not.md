---
title: "How to rerun automounting of HD/SSD partitions? (not using fstab/mount)"
date: 2023-12-07
forum: General Help
---

### Post by edwingate8 on 2023-12-07
I'm  using Ubuntu 22.04 and on start-up, HD/SSD partitions are automatically  detected and directories are created/mounted under  /media/<username>.  If I unmount these, the corresponding  directory actually goes away.  How can I get the partition to mount again in this same manner without  restarting?  These partitions are not listed in /etc/fstab.  Some other mechanism is detecting partitions and mounting them on start-up.

I know I could manually create a directory and run mount  myself or list the partitions  into /etc/fstab and do "mount -a", but is there a way I can just  rerun the magic that occurs on start-up?  I think it has something to do  with udevd or systemd, but haven't been able to figure out how/if I can  invoke this automount process after start-up.

---

### Post by TheFu on 2023-12-08
I don't think they aren't mounted at boot. It is the file manager that does it, after you login.  Login and boot are very, very, different.  Depending on the DE you use, there could be a few different programs doing it.  The specific file systems would matter, since they each have different mount types.  Assuming you have all the needed helper programs installed, to get a list of possible devices to mount, use:
**gio mount -l**

There is an option to get more details.

Then you can look over the list (programmatically), create mount directories where ever you like (say /media/username/label) and lastly, you can mount them using a few different versions of the **gio mount** command.

The **gio** manpage explains.  I think gio is part of Gnome, so Qt-based installs would need to find the Qt-version of that tool.

I just use **autofs**, but that requires pre-configuration.  If you setup unique labels for each file system, mounting will be much easier.

Another possible option is to use the **udisksctl** tool.  It appears to need all the detailed information that an fstab or autofs entry would need. Guess TANSTAFFL applies.  ref: [https://en.wikipedia.org/wiki/TANSTAAFL](https://en.wikipedia.org/wiki/TANSTAAFL)

---

### Post by MAFoElffen on 2023-12-08
> **TheFu said:**
> Another possible option is to use the **udisksctl** tool.  It appears to need all the detailed information that an fstab or autofs entry would need. Guess TANSTAFFL applies.  ref: [https://en.wikipedia.org/wiki/TANSTAAFL](https://en.wikipedia.org/wiki/TANSTAAFL)
udisk2 & udiskctl -- That is what I was thinking, when I first read that... which is either doing eject > unplug > Plug back in... or manually via udiskctl.

There is also another hack, where you can create systemd unit files, where, if a uniquely identified drive is seen, then to mount it in a specific mountpoint with specific options... I don't think he is asking for something like that.

Somehow, I feel like we are missing a few details of the limits and conditions of what they are trying to do...

---

### Post by TheFu on 2023-12-08
> **MAFoElffen said:**
> udisk2 & udiskctl -- That is what I was thinking, when I first read that... which is either doing eject > unplug > Plug back in... or manually via udiskctl.

There is also another hack, where you can create systemd unit files, where, if a uniquely identified drive is seen, then to mount it in a specific mountpoint with specific options... I don't think he is asking for something like that.

Somehow, I feel like we are missing a few details of the limits and conditions of what they are trying to do...

There's a difference between what he wants and what we believe exists today.  We are both trying to bridge that gap with our experience.

Of course, I have the added problem ... 
```

$ udisk2
udisk2: command not found

$ udisksctl status
Command 'udisksctl' not found 
```

Don't know why the errors are different. Probably related to the package each is contained inside ... one is in repos that I have enabled. The other is in some outside repo I don't have enabled.  I find the automatic mounts and GUI mount tools undermine performance, so I purge them from all my systems to prevent the issues they cause me. Instead, I use **autofs**, where complete control over the mount options is possible.

---

### Post by edwingate8 on 2023-12-08
[FONT=courier new]udisksctl mount -b /dev/sde1[/FONT] is what I was looking for.

---

### Post by TheFu on 2023-12-08
> **edwingate8 said:**
> [FONT=courier new]udisksctl mount -b /dev/sde1[/FONT] is what I was looking for.

The problem is that /dev/sde1 isn't guaranteed.  That can change at every boot, which is why we use LABEL and UUID in the fstab.  The manpage says that the block device filename needs to be used, so you'll want to find it under /dev/disk/by-label/ or /dev/disk/by-uuid/.  Those are symbolic links to the real device files, but guaranteed to be updated and correct.

---

### Post by edwingate8 on 2023-12-10
> **TheFu said:**
> The problem is that /dev/sde1 isn't guaranteed.  That can change at every boot, which is why we use LABEL and UUID in the fstab.  The manpage says that the block device filename needs to be used, so you'll want to find it under /dev/disk/by-label/ or /dev/disk/by-uuid/.  Those are symbolic links to the real device files, but guaranteed to be updated and correct.

They've all stayed constant  on my system since I've had it.  I guess I'll deal with it if/when they change.

---

### Post by TheFu on 2023-12-10
> **edwingate8 said:**
> They've all stayed constant  on my system since I've had it.  I guess I'll deal with it if/when they change.

The kernel "finds" devices as they respond.  It is a timing thing, so any system changes, especially a new kernel, can swap the device names around when there are multiple devices connected using the same sorts of connections.  When things change and mounts are specified using the /dev/sdXYZ in the fstab, it can cause a system not to boot at all.  When that happens, it will probably be the last thing you remember after hours of trying to fix the issue.  OTOH, if you use LABELs or UUIDS now to mitigate the problem, it will never happen.

So, in my fstab, I have these mounts:
```
UUID=853e3c83-1b07-4c59-8ee0-4edc0911bd85 /boot            ext4 defaults 0 1
UUID=DAB8-8DEE                            /boot/efi        vfat defaults 0 1
LABEL=[COLOR="#008000"]R2-Array[/COLOR]                 /raid2          ext4 noatime,nofail,errors=remount-ro  0  2

```

Looking at the first column, we have 2 UUIDs and 1 LABEL.  To translate directly to symbolic links under /dev/disk/ .... let me see if I can find the LABEL one ...the command is:
```
$ find /dev/disk -iname \*[COLOR="#008000"]R2-Array[/COLOR]\*
/dev/disk/by-label/[COLOR="#008000"]R2-Array[/COLOR]
```

So the device file I can use instead of the LABEL would be **/dev/disk/by-label/[COLOR="#008000"]R2-Array[/COLOR]**.
Simple enough and completely mitigates the problem.  

I've shown the horse the safe water to drink, but it is up to you to actually drink it.

---

### Post by edwingate8 on 2023-12-11
> **TheFu said:**
> 
I've shown the horse the safe water to drink, but it is up to you to actually drink it.

I thank you.  *Neigh!!!!!!*

---

