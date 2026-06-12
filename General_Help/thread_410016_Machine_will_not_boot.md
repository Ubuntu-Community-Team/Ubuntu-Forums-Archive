---
title: "Machine will not boot"
date: 2007-04-15
forum: General Help
---

### Post by Loonux on 2007-04-15
I was happily updating my kubuntu system earlier this evening when it just hung (my GF was browsing the web while it was updating and she claims the machine just froze). Upon trying to reboot, the machine now will not load.
It gets as far as "SETTING UP CONSOLE FONT AND KEYMAP" and just sits there. All I can do then is hard-reset the machine.

All im getting in the boot process is;

```
Checking root filesystem
fsck 1.40

/dev/sda4: superblock last mount time is in the future. FIXED
/dev/sda4: superblock last writetime is in the future. FIXED
/dev/sda4: clean, <some numbers etc> [ok]

Checking file systems... [ok]

Mounting local filesystems...
[17179587.668000] FAT: utf8 is not a recommended IO charset for FAT filesystems will be case sensitive!
*configuring network interfaces...
*setting up console font and keymap...
```

I have run a file system check on the partition, which didn&#8217;t report any problems, so I don&#8217;t really know what to do. I can boot a LiveCD so I don&#8217;t think its hardware related.

Thanks for any ideas.

---

