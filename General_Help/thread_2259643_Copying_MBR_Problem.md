---
title: "Copying MBR Problem"
date: 2015-01-06
forum: General Help
---

### Post by box02-0 on 2015-01-06
Hi.       Ubuntu 64 bit 14.04

I have twin 512gb Samsung 850 pro ssd drives. I Installed Windows 8 and Ubuntu 14.04 on the 1[SUP]st[/SUP] drive (dual boot). The 2[SUP]nd[/SUP] drive is purely a backup of the first, and except for doing backups, it is I disabled via the ASUS BIOS.

I used Gparted to copy Windows 8 (SDA1) and Ubuntu (SDA4) to the 2[SUP]nd[/SUP] drive. I want to be able to boot the second drive in case the first one fails.
I have been trying unsuccessfully to copy the MBR (boot code) of drive 1 to drive 2. Here is what I tried:

I booted a USB containing an ISO of my desktop (built by remastersys). In Terminal, I entered the following:


  ```
    dd if=/dev/sda of=/dev/sdb bs=446 count=1
```
  

After booting and disabling Drive 1, I was unable to boot from the 2[SUP]nd[/SUP]Drive.
What did I do wrong?
  
Thanks,
  
M....

---

### Post by Bucky Ball on 2015-01-06
Please use default text size. Thanks. I have removed the BIG text and added [code] tags.

For copying partitions/disks, [Clonezilla]("http://clonezilla.org/") may be a better option.

---

### Post by oldfred on 2015-01-06
If you clone systems, you cannot use both. Cloning is more for restoring system to same partition(s).

If you have cloned system you will have duplicate UUIDs. And if gpt duplicate GUIDs. And duplicates are not allowed and you may be sometimes boot one drive and sometimes boot the other drive, eventually getting systems so out of sync neither works.

If MBR, you can edit UUID, edit grub with new UUID, edit fstab with new UUIDs and a few other places. With Ubuntu reinstall is usually easier.

I might suggest using one drive for Windows, and the other drive for Ubuntu. And then backup most essential data from Windows into Ubuntu drive, and Ubuntu data onto Windows drive with separate backup partitions. But full image backup of Windows is usually the best option as it is so difficult to reinstall if major issues. Ubuntu can easily be reinstalled so backup of /home, /etc, list of installed apps and reinstall with restore of those backups can be done very quickly.

---

