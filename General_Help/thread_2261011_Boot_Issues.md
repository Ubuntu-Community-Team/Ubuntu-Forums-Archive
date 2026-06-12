---
title: "Boot Issues"
date: 2015-01-15
forum: General Help
---

### Post by box02-0 on 2015-01-15
Hi.

I have a dual boot WIN8 & Ubuntu 14.04 system, running with dual 512gb SSD drives.

WIN8 was installed, and I did a &#8220;Live CD Restore&#8221; with ubuntu 14.04 in its own ext4 partition. I had Grub installed in SDA (as opposed to the Ubuntu partition).

I spent many hours getting the Ubuntu desktop the way I like it. Then for reasons too long to explain, I booted windows, and used easybcd to give me a dual boot (which I already had). My bad.

That was the end of Ubuntu &#8211; when I booted, I got the BCD windows menu &#8211; if I chose WIN8, worked like a charm. If I chose Ubuntu, I got an unknown file system error and ended up in grub rescue. 

I tried many options, including boot-repair to no avail.

Now we are coming to the punch line:

I decided to do a Live CD restore to fix the boot problem, and then try to reinstate my Desktop:

I did a dd copy of Drive 1 to drive 2 (cloned the 2 drives). I disabled D1. I then did a live  Live CD restore to Drive 2.  Now Drive 2 worked like a charm, booting right into Ubuntu, giving me the Ubuntu or Win8 option.

However, all my hard work to set up the desktop was gone. So I enabled D1, and using Gparted, I copied the Ubuntu partition from D1 to D2. Now if I boot D2 and select Ubuntu from the easybcd menu, yikes I'm back to unknown file system and grub rescue. (Selecting WIN8 works fine.)

I was careful to ensure that the partition where the Live Restore was done to had the same UUID as that of the Ubuntu partition on D1.

This leaves me to believe ubuntu on D1 Is corrupted. (It looks fine in Nautilus.) I don't know what happened  &#8211; it worked before easybcd.


Finally my question: Is my theory correct &#8211; can you do a (14.04) live install, and then copy another 14.04 onto it (assuming uuid's are unchanged.)? 

Any help would be greatly appreciated.

Thanks,

M...

---

### Post by box02-0 on 2015-01-15
Hi again.

Okay after some re-tracing of all the events leading up to why Ubuntu won't boot, I realized that I made the problem. I changed the uuid of the Ubuntu drive. Realizing this, I edited /boot/grub/grub.cfg and /etc/fstab to reflect the new uuid. The problem still persists. 

Is there any other place where the old uuid would be?

I sure made a mess. I do have a remastersys iso from a while ago, so if the uuid idea is a bust, I will try restoring from that.

Thanks,


M...

---

### Post by oldfred on 2015-01-16
With UEFI I think EasyBCD just adds issues. It is another boot manager and you already have UEFI as a boot manager and grub as a boot manager. EasyBCD may be useful to fix BCD issues and I do like to have multiple repair tools for every system I install.

I prefer to have each system installed on its own drive with the boot loader on that drive. But now with UEFI, when I installed Ubuntu to sdb, it over wrote my grub entries in sda's efi partition. I had to manually copy efi files and reintall the grub for install on sda.

Only sure way then is to either disconnect each drive when you install a system to that drive, or fully backup efi partition and copy new install's version back to other drive and restore previous efi files. Boot files in efi partitions so not require install and can be just copies. Of course configuration has to match install.

May be best to see details. Do not Boot-Repair fix until someone has reviewed install. Boot-Repair is primarily a Linux repair tool and can only make minor fixes to Windows.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

