---
title: "Filesystem settings/results I am not understanding"
date: 2016-08-16
forum: General Help
---

### Post by yoshii on 2016-08-16
```

FSTAB contains:  UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx    /    ext4    auto_da_alloc,noatime,lazytime,errors=remount-ro    0    1

DMESG output:

[    time] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   later] systemd[1]: Starting Journal Service...
[   later] systemd[1]: Started Journal Service.
[   later] EXT4-fs (sda3): re-mounted. Opts: auto_da_alloc,errors=remount-ro

```

Of course, that's not literally what my I/O's contain, but it's enough to get some support.  

I am noticing a discrepancy between my fstab settings and my dmesg output right after boot.  
Booting usually goes by too quick for me to see all the results of the filesystem mounting and/or fscking.  
I am going to have to resort to taking photos with my camera just to get a screensave.  

One thing I will say about MS Windows... they did at one point allow a person to pause the boot process to take a look.  
Is there any such command in Linux?  (a command to pause the boot process?)

And does anybody know why the filesystem seems to be ignoring the mounting options at first, and then cherrypicking just a few later on after re-mounting?  
Every time I do a filesystem scan from external sources I get no errors.  And after I tried to fix some "operational" errors (8, see the man pages for ext), the boot process sped up so I couldn't see the screen text.  

This is more of an academic issue, because I understand that ext4 is still in the development stage.  But it would be helpful if anybody cares to share some insights of any sort related to this.  
Thanks.

---

### Post by gordintoronto on 2016-08-17
Ctrl-s should pause booting. Ext4 is a mature filesystem.

---

### Post by yoshii on 2016-08-18
Thanks very much gordy, I am grateful.  
The Ext4 release notes imply that Ext4 is maturely still in development in terms of complete implementation of all it's features and quashed bugs.  
Of course it can take many years for any software to fully stabilize so I'm not critical.  

Any insights on the fstab, etc discrepancies?

---

### Post by yoshii on 2016-08-30
> **gordintoronto said:**
> Ctrl-s should pause booting. Ext4 is a mature filesystem.

I am skeptical that "Ctrl-s should pause booting", even on a fully working system.

---

