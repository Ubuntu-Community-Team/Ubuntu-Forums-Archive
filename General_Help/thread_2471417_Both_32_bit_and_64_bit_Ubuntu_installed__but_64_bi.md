---
title: "Both 32 bit and 64 bit Ubuntu installed  but 64 bit won't boot."
date: 2022-01-29
forum: General Help
---

### Post by rsteinmetz70112 on 2022-01-29
I have a computer which has had 32 bit Ubuntu on it since I believe 06.04, possibly earlier. It has been updated and all of the hardware changed out more than once. Even the case has been swapped. Ubuntu has been updated to successive LTS versions and is currently 18.04.6 32 bit. I know I need to move to 64 bit so I installed 64 bit 18.04 along side the original 32 bit version. I intended to transfer the configuration from 32 bit to 64 bit verify they both worked then remove the 32 bit. I had both versions running at one time, however something happened and the 64 bit install won't start, it says it is unable to mount the root partition and panics.

There are 4 mechanical hard drives set up in 2 RAID 1 arrays named md0 with pv hamlet (the computers name) for 32 bit and md1 with pv system for 64 bit. Each array is an lvg and has three volumes on it root, home and files. They are formatted with an mbr partition table with one partition per drive. There is no UEFI. The motherboard does not support it.

When I boot into the GRUB menu I see a default entry for Ubuntu (the 32 bit default) and two kernels. I also see a listing for Ubuntu 18.04 on dev/mapper/system-root which is the 64 bit install.

[LIST]
[*]I can select any of the items in the grub menu and I can open the settings. 
[*]I can boot into the 32 bit kernel and I have all of the lvs mounted in /etc/fstab. I can go into the files and see everything in them. As far as I can tell they look fine.
[*]But when I try to boot the 64 bit kernel I get an error "unable to mount root fs on unknown-block (0,0)" then a kernel panic. 
[/LIST]
I'm not particularly clear on the boot process and what is happening or how to fix it or more importantly keep it from happening again if I reinstall the 64 bit version.

---

### Post by oldfred on 2022-01-29
I do not know LVM.

But run Boot-Repair so we can review configuration. If encrypted, be sure to manually mount encrypted partition so Boot-Repair can see your entire system.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

With multiple drives & multiple installs, you normally want to run Boot-Repairs advanced mode as defaults usually just fix first install on first drive it finds.

I converted my 32 bit 6.06 install to 64 bit in about 2009. But did not know to export list of installed apps to make it easy to reinstall them. I took screen shots of all apps.

---

### Post by rsteinmetz70112 on 2022-01-29
I tried installing boot-repair from the link in your message and got this:

```
# add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
Cannot add PPA: 'ppa:~yannubuntu/ubuntu/boot-repair'.
ERROR: '~yannubuntu' user or team does not exist.
```

I know I installed it on another computer before.

I also seem to have messed up my sources and now I'm getting this error when I try to update;
```

# apt update
Err:1 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease
  Could not resolve 'us.archive.ubuntu.com'
Err:2 http://security.ubuntu.com/ubuntu bionic-security InRelease
  Could not resolve 'security.ubuntu.com'
Err:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease
  Could not resolve 'us.archive.ubuntu.com'
```

OK I fixed that. Turns out I had changed the NIC and didn't set the DNS correctly.

Got boot-repair installed

---

### Post by rsteinmetz70112 on 2022-01-29
OK Here is the Bootinfo Summary
[http://paste.ubuntu.com/p/MFcR8xsVfv/](http://paste.ubuntu.com/p/MFcR8xsVfv/)

Here is lsblk for the computer:
```
# lsblk
NAME               MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
fd0                  2:0    1     4K  0 disk
sda                  8:0    0   1.8T  0 disk
&#9492;&#9472;sda1               8:1    0   1.8T  0 part  /ntfs-backup
sdb                  8:16   0   3.7T  0 disk
&#9492;&#9472;sdb1               8:17   0   3.7T  0 part  /backup
sdc                  8:32   1 931.5G  0 disk
&#9492;&#9472;sdc1               8:33   1 931.5G  0 part
  &#9492;&#9472;md0              9:0    0 931.4G  0 raid1
    &#9500;&#9472;hamlet-root  252:3    0   140G  0 lvm   /
    &#9500;&#9472;hamlet-home  252:4    0 395.7G  0 lvm   /home
    &#9492;&#9472;hamlet-files 252:5    0 395.7G  0 lvm   /files
sdd                  8:48   1 931.5G  0 disk
&#9492;&#9472;sdd1               8:49   1 931.5G  0 part
  &#9492;&#9472;md0              9:0    0 931.4G  0 raid1
    &#9500;&#9472;hamlet-root  252:3    0   140G  0 lvm   /
    &#9500;&#9472;hamlet-home  252:4    0 395.7G  0 lvm   /home
    &#9492;&#9472;hamlet-files 252:5    0 395.7G  0 lvm   /files
sde                  8:64   1 931.5G  0 disk
&#9492;&#9472;sde1               8:65   1 931.5G  0 part
  &#9492;&#9472;md1              9:1    0 931.4G  0 raid1
    &#9500;&#9472;system-root  252:0    0   150G  0 lvm   /system/root
    &#9500;&#9472;system-home  252:1    0 465.7G  0 lvm   /system/home
    &#9492;&#9472;system-xtra  252:2    0 315.7G  0 lvm   /system/xtra
sdf                  8:80   1 931.5G  0 disk
&#9492;&#9472;sdf1               8:81   1 931.5G  0 part
  &#9492;&#9472;md1              9:1    0 931.4G  0 raid1
    &#9500;&#9472;system-root  252:0    0   150G  0 lvm   /system/root
    &#9500;&#9472;system-home  252:1    0 465.7G  0 lvm   /system/home
    &#9492;&#9472;system-xtra  252:2    0 315.7G  0 lvm   /system/xtra
```

sda and sdb are external USB drives.

---

### Post by oldfred on 2022-01-29
Did Boot-Repair only mount one RAID/LVM?
That may be its default. You show a second RAID/LVM, but it did not show any details.

Do not run the suggested auto-fix as that wants to install grub to sda's MBR. You want each LVM to have its own grub.

Do not know enough about RAID nor LVM to help further.

---

### Post by rsteinmetz70112 on 2022-01-29
Thanks. 

When I ran it all of the volume groups were mounted. I'm not sure how the boot process works and when it mounts what. 

I'm not sure how you would select the one OS your want to run if each lvm has it's own grub. 

How does that work with dual boot? I don't think it would be much different.

---

### Post by oldfred on 2022-01-29
Boot-Repair normally shows each install & its grub entries & fstab.
But defaults to install first one.
With BIOS it normally wants to install to sda as default as most systems only have one drive.
It used to install one grub to every MBR, but Yann just updated it to only install to one drive.
But you want each install to have grub in MBR of the drive(s) with that install. 
Not sure with RAID, if you have to install twice? Once to each part of RAID as MBR is not really part of RAID as I understand it.

In Advanced mode does Boot-Repair let you chose either install and then choose a drive to install grub into.

---

### Post by rsteinmetz70112 on 2022-01-30
I believe you can install grub into every drive with #install-grub, or # update-grub but I'm not sure it's necessary. I'm also not sure mdadm or LVM make much difference once they are activated.

---

