---
title: "cannot boot after moving partition"
date: 2013-05-23
forum: General Help
---

### Post by eeluser on 2013-05-23
Hey guys , nice to meet you all , 

I had ubuntu only installed on my notebook(in sda1) and wanted to install another OS on sda1 to make my notebook dual-booting , 
I made a new partition (sda6) using "gparted" and copied and pasted sda1 in it , formatted sda1 to ntfs, and apply the changes
I then booted from live usb and used boot-repair to try to make my note-book boots from the new partition (sda6)
I rebooted my notebook after removing the live usb, and I always get that prumpt:

unknown filesystem
 grub rescue > 




I also made boot info file using boot-repair. 
please any help will be really appreciated

and thanks in advance 

eeluser

---

### Post by HiImTye on 2013-05-23
what do you mean by 'copied and pasted'?

---

### Post by eeluser on 2013-05-23
Hi HimTye,

using GParted, and following some tutorial instructions 
I made a new partition (sda6) and copied all sda1 (ubuntu root partition) to sda6

---

### Post by HiImTye on 2013-05-23
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
yes, but what tools did you use to copy it? include specific commands if possible.

the more detail you provide, the easier it is to help you

---

### Post by ajgreeny on 2013-05-23
I suspect your /etc/fstab file now points to a root partition that no longer exists.

Let's see the output of ```
sudo blkid -c /dev/null
cat /media/mountpoint/etc/fstab
```where mountpoint is that of your installed/copied but not working ubuntu partition.

---

### Post by CraigPid on 2013-05-24
> **HiImTye said:**
> yes, but what tools did you use to copy it? include specific commands if possible.

the more detail you provide, the easier it is to help you

He said he used GParted. Right click on the partition you want to copy.Click copy.Right click on the partition you want to paste it into and click paste.

---

### Post by CraigPid on 2013-05-24
It probably wasn't a good idea to move the partition that you had grub installled on. If you want to install windows it's usually best to do that first. Probably the most pain free way of fixing this is to back up your home directory and whatever you need with a live cd and reinstall your linux distro. I'm sure there is a way to edit everything to point to the right locations but unless your really tied to your Linux installation doing a fresh install is pretty easy nowadays.
  I have a system that I bought this year and I`ve managed to not put windows on it. If I ever did I`m sure it would disrupt everything. I`ve tried moving installations to different partitions and it`s worked well but the one that has grub installed in the 1st sector of the disc stays put.
   Craig

---

### Post by deadflowr on 2013-05-24
> **CraigPid said:**
> It probably wasn't a good idea to move the partition that you had grub installled on. If you want to install windows it's usually best to do that first. Probably the most pain free way of fixing this is to back up your home directory and whatever you need with a live cd and reinstall your linux distro. I'm sure there is a way to edit everything to point to the right locations but unless your really tied to your Linux installation doing a fresh install is pretty easy nowadays.
  I have a system that I bought this year and I`ve managed to not put windows on it. If I ever did I`m sure it would disrupt everything. I`ve tried moving installations to different partitions and it`s worked well but the one that has grub installed in the 1st sector of the disc stays put.
   Craig

+1 for reinstall.


Edit: I was reading a different thread and switched back and assumed something by mistake so's I remove out of place context.

---

### Post by agillator on 2013-05-24
My guess is your first and major problem is you moved the boot partition and then Grub could not find it. This also happens if you try to delete a partition before (numbered less than) the boot partition. The solution is to reinstall grub. However, do install Windows first or you will be reinstalling grub twice. When you are ready to reinstall Grub, look at [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing), the section on fixing a broken system via live CD terminal. Don't forget to run update-grub as suggested the first time you boot into Ubuntu after reinstalling.

---

