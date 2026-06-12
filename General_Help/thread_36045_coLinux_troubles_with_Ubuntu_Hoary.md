---
title: "coLinux troubles with Ubuntu Hoary"
date: 2005-05-21
forum: General Help
---

### Post by Misogynist on 2005-05-21
I wasn't sure if this really belonged here, but on the off chance that someone here has had similar problems, here goes:

I'm trying to get Ubuntu Hoary running in coLinux, which currently resides on a separate partition from Windows, with which it dual-boots. Ubuntu, booted by itself, functions as one would expect it to. My partition layout is as follows:

/dev/hda1: 79GB Ext3 (root partition)
/dev/hda2: 1GB Swap
/dev/hda3: 80GB NTFS (Windows)

I've pointed coLinux to use both of these partitions, which it begins to boot very nicely. The problem is that during the boot process, around "Starting internet superserver," coLinux just crashes, and breaks the output to the console. I haven't been able to debug this in any kind of meaningful way. I got it to boot once immediately following a reboot of Windows, but I haven't been able to figure out why it worked that one time. It has not booted correctly since.

Here is my colinux.xml configuration:

```
<?xml version="1.0" encoding="UTF-8"?>
<colinux>
    <block_device index="0" path="\Device\Harddisk0\Partition1" alias="hda1" enabled="true" />
    <block_device index="1" path="\Device\Harddisk0\Partition2" alias="hda2" enabled="true" />
    <bootparams>root=/dev/cobd0</bootparams>
    <initrd path="initrd.gz" />
    <image path="vmlinux" />
    <memory size="192" />
    <!--<network index="0" type="bridged" />-->
</colinux>

```

And here are my relevant hardware specs:

[list][*]HP Pavilion a350n
[*]Pentium 4 2.8 GHz w/ HyperThreading
[*]512MB PC2700
[*]Geforce4 MX440 (primary)
[*]Geforce2 MX400 (secondary)[/list]

I am running Windows XP Professional SP2.

Thanks in advance for any help you might be able to give.

---

