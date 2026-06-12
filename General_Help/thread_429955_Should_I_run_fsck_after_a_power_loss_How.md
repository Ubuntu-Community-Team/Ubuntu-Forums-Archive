---
title: "Should I run fsck after a power loss? How?"
date: 2007-05-01
forum: General Help
---

### Post by benton on 2007-05-01
Hi there,

I want to run fsck on my partitions after a power loss. I am new to this, so I wonder if I really need to download the Ubuntu CD again (I don't have mine handy right now) so I can boot with the "live" part and check the not yet mounted HD partitions. Or is there a way I can boot normally, then unmount the partitions and run fsck on them? Is there is a tutorial for this?

Oh and according to wikipedia: [COLOR="Blue"]Generally, fsck is run automatically at boot time when the system detects that a file system is in an inconsistent state, indicating a non-graceful shutdown, such as a crash or power loss.
[/COLOR]

If that is true with Ubuntu as well, is there a visual clue of this auto fsck? I did not see anything special at the time of the first boot after the power loss.


Thanks in advance for any help,

-Benton

---

### Post by dcstar on 2007-05-01
> **benton said:**
> Hi there,

I want to run fsck on my partitions after a power loss. I am new to this, so I wonder if I really need to download the Ubuntu CD again (I don't have mine handy right now) so I can boot with the "live" part and check the not yet mounted HD partitions. Or is there a way I can boot normally, then unmount the partitions and run fsck on them? Is there is a tutorial for this?

Oh and according to wikipedia: [COLOR="Blue"]Generally, fsck is run automatically at boot time when the system detects that a file system is in an inconsistent state, indicating a non-graceful shutdown, such as a crash or power loss.
[/COLOR]

If that is true with Ubuntu as well, is there a visual clue of this auto fsck? I did not see anything special at the time of the first boot after the power loss.


Thanks in advance for any help,

-Benton

Open a terminal:
```
sudo touch /forcefsck
```
Reboot.

---

