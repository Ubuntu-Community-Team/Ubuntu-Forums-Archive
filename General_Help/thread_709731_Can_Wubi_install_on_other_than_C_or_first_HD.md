---
title: "Can Wubi install on other than C: or first HD?"
date: 2008-02-27
forum: General Help
---

### Post by jhlaufer on 2008-02-27
I would like to try Ubunti through a Wubi install, but am a bit confused and quite nervous about messing up my existing XP setup. (Yeah, I know, some here may think "messing up" and "XP" are redundant. But, my work depends on this system, unfortunately.)

I'm running an XP machine with two physical hard drives. Both drives are formatted NTSF. First drive is one primary partition (C:\). Second physcial drive first has one primary partition (X:\) and then an extended partition with two logical partitions (Y:\ and Z:\).

I'd like to install Ubunti through Wubi on the Y: drive. Ubuntu can have the whole logical partition Y: (about 40G). If possible, I would then like to be able to boot between XP and Ubuntu.

Is this doable without having to be a Linux guru? Thanks!

---

### Post by ago on 2008-02-27
You can choose any drive you want in wubi provided you have more than 5GB.

Consider that if you already have a dedicated partition you might opt for a full installtion.

In either case you will be able to dual boot into windows/ubuntu.

---

### Post by jhlaufer on 2008-02-27
Thanks for the quick response. This is good news.

If I do opt for a full installation, can I do this on the first logical partitiion within the extended partition (which is actually the second partition) on the second drive? If so, how do I set up the XP/Ubuntu dual boot? My understanding (extremely limited when it comes to dual boot) is that, at least for Windows, the boot drive has to be a primary partition. Is this not true for Ubuntu? 

Thanks again!

---

### Post by ago on 2008-02-27
> **jhlaufer said:**
> 
If I do opt for a full installation, can I do this on the first logical partitiion within the extended partition (which is actually the second partition) on the second drive?
yes, linux does not care about primary partitions it can boot from anyware (with a few grub exceptions), of course if you want linux bootover to take over (good idea) that would have to go into the MBR of the first drive. I assume that is the case, but do not remember on top of my head. 

> If so, how do I set up the XP/Ubuntu dual boot?
That is done for you (with the above caveat).

---

