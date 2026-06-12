---
title: "Disk not mounting"
date: 2018-02-07
forum: General Help
---

### Post by QwUo173Hy on 2018-02-07
I SSH'd into a machine and noticed today one of my mount points is now missing. It's entered in fstab as: 

```
/dev/disk/by-uuid/79fb515c-492e-49c9-8fde-0a3ade52bd7f /mnt/storage auto nosuid,nobootwait,nodev,nofail,comment=x-gvfs-show 0 0
```

I have ssh access. How do I trouble shoot this? Trying to mount it from the terminal gives an error:

```
mount: special device /dev/disk/by-uuid/79fb515c-492e-49c9-8fde-0a3ade52bd7f does not exist
```

---

### Post by TheFu on 2018-02-07
Perhaps looking at the system logs and dmesg would have some warnings or errors to help?
Also, the normal way to use UUIDs in an fstab is with the 
UUID=79fb515c-492e-49c9-8fde-0a3ade52bd7f method.

So the line would be:
```
UUID=79fb515c-492e-49c9-8fde-0a3ade52bd7f  /mnt/storage auto nosuid,nobootwait,nodev,nofail  0 0
``` assuming /mnt/storage directory already exists.  BTW, I've never used "auto" as the file system type.  Does that work?  All mine are "ext4" or swap.

---

### Post by QwUo173Hy on 2018-02-07
The syntax is the default for this Ubuntu install so I'll leave it as is, but thanks for the tip with dmesg. I'll remember that one for again.

I got physical access to the machine and checked that the cables were in as firmly as possible and now it works fine. 

But, next time this happens I'll try dmesg and see if there are any indicators that tell me it's not a software issue.

---

### Post by oldrocker99 on 2018-02-07
An external disk once failed while I was writing data to it. I mourned the loss of 4+ TB of stuff, then thought of replacing the USB cable, and voila! the drive mounted.

I don't know if your drive is in or ext, but HD cables can fail for no apparent reason. If in, the SATA cable may well have deep-sixed itself. 

Worth a try.

---

### Post by QwUo173Hy on 2018-02-08
Thanks oldrocker. It's internal but the way the issue was fixed hasn't given me much confidence. The connections seemed fine put giving them all a shove fixed it.

Only thing is, there are around six drives in it and I have no idea which is which :D

---

### Post by TheFu on 2018-02-08
Cable connection issues often show up in the system logs. 
I've had some SATA connection issues caused by tiny vibrations in the box.  Ended up switching out the SATA cables so some with 90 deg angles and snap-on clips. That solved the issues here.

BTW, which release are you running?  I've only seen UUID= in fstabs for about the last 10 yrs.  Pointing to the by-uuid/ directory link should work just fine.  That is how LVM LVs are mounted too.

If the issue is solved, please mark the thread as solved (thread tools).

---

### Post by Morbius1 on 2018-02-08
Could be another argument for never ever using the Disks ( gnome-disk-utility ) utility. It's the only thing that would produce an entry in fstab that looks like this:
> /dev/disk/by-uuid/79fb515c-492e-49c9-8fde-0a3ade52bd7f /mnt/storage auto nosuid,nobootwait,nodev,nofail,comment=x-gvfs-show 0 0

It really likes the /dev/disk/by-uuid descriptor, uses "auto" instead of stating the filesystem used, and it usually defaults to /mnt/XXX mountpoints so that it doesn't show up on the desktop or on the side panel of the file manager then ruins it by adding x-gvfs-show that forces it to do the opposite.

---

