---
title: "Boot Problem with separate /boot"
date: 2013-12-21
forum: General Help
---

### Post by wd5gnr2 on 2013-12-21
I have a long time Kubuntu 13.10 installation that has / as an lvm2 volume over a mdadm RAID array. It has worked fine for a long time.

In preparation for some changes, I wanted to split out /boot to another volume (I have a 1TB drive that has swap and some misc storage for non-RAID). 

I used the Boot Repair utility available and it seemed to go OK ([http://paste.ubuntu.com/6608575](http://paste.ubuntu.com/6608575)). 

The problem is now I can't boot the system unless I edit the kernel command line to use rw instead of ro. With ro the system hangs as if it is trying to check some disk that is never ready. When you interrupt that you get put out to a maintenance shell (even through root is apparently mounted ro). If you boot with rw, everything is fine. I have booted off CDROM and fsck'd all the drives in the system and they show clean.

Any idea what the trick is to getting it to boot normally? And yes, I can modify grub to just pass rw, but I'm sure that's a bad idea for some reason.

Thanks!

Solved. I guess when I was booting from / the data=writeback line was applying to /. Now it is applying to /boot. Then somewhere inside initramfs, the mount to / was occuring without data=writeback. Since that was set in fstab, the volume refused to remount. The answer (or at least an answer) was to do tune2fs /dev/xxx -o jounral_data_writeback

Whew.

---

