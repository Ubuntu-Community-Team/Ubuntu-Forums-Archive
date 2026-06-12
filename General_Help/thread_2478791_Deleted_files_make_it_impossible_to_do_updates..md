---
title: "Deleted files make it impossible to do updates."
date: 2022-09-05
forum: General Help
---

### Post by archimedes1981 on 2022-09-05
Hi, I have a laptop with a 120gb ssd. It was partitioned as 20gb for root and 100gb for home. It worked fine for a number of years but lately I had problems during boot. It would stop booting and I would have to go to recovery and do some cleaning and run init 5 (or 6).last time it kept telling me that I could not do updates no matter what I deleted, so I deleted what I thought were snaps for libreoffice and a couple more. I don't remember exactly what I deleted but I think they were folders. Now when I try doing updates it halts saying that it can't find /var /xxxxx a number of folders in var. I tried mkdir them but it still says the same weather I try removing libreoffice or installing it. I am trying to fix this without re installing. Please help. I'm not very good at this.

---

### Post by yancek on 2022-09-05
Which version of Ubuntu are you using?
Did you get any message indicating why it could not continue with the update?
It's going to be really hard if you don't know what you deleted.  If you have a 20GB / partition and have been using it for some the / partition may be getting full.  Run this command to show how full the / partition is:  df -h  If your / partition is almost full (95%), remove logs from /var/log.
If you have a separate /home partition, you could try a reinstall of the same release/version and select to NOT format the / partition and of course, NOT format /home.

---

### Post by miguel001 on 2022-09-06
I don't like separating root and home for that very reason. 20GB isn't really a whole lot. You have to waste a ton of space to make sure you always have enough even years later.

But, then I don't think you mentioned specifically if it was full or not. There are basic maintenance command line tools you can run to clean up / vacuum various things as well. If it is full then vacuuming the logs and limiting that will ease up the use by some GB. example: [https://unix.stackexchange.com/questions/139513/how-to-clear-journalctl](https://unix.stackexchange.com/questions/139513/how-to-clear-journalctl)

It might be possible to move all the stuff in any partitions elsewhere, delete them, and do a non destructive size change on the root and make it bigger then recreate them and move everything back. But, its difficult to say how that will go. You'd also lose a lot of space from the other partitions. If not buying more space is a limitation here then combining root and home is a way to maximize free space which I'd just do with a clean install since its good to do that anyway.

---

### Post by archimedes1981 on 2022-09-08
I'm running ubuntu 18.04, originally it was saying that there was not enough space, now I enlarged the partition to 30gb and its giving missing folders errors (some in var and some in usr) when I try to update. If I reinstalled without formatting, will it keep any installed software? I have some software that took a while to set up. I'm also inclined to switch to budgie. Can I install it on top of regular ubuntu?

---

### Post by yancek on 2022-09-08
>  If I reinstalled without formatting, will it keep any installed software?

I've only done this twice, once with Ubuntu and once with Slackware and it worked both times.  If you have 18.04 installed, you would need to reinstall using 18.04.  It should keep installed software although I'm not sure.  The reinstall should just install new system files.  Are you referring to modified software that came with Ubuntu or third party software.  Make a backup of that software before reinstalling.

I don't know the differences between Budgie and a standard Ubuntu but I would not do that in the current situation.

---

### Post by archimedes1981 on 2022-09-08
It's third party software.

---

### Post by archimedes1981 on 2022-09-08
This is what |'m getting:
:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-166 linux-headers-4.15.0-166-generic
  linux-image-4.15.0-166-generic linux-modules-4.15.0-166-generic
  linux-modules-extra-4.15.0-166-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-common
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
46 not fully installed or removed.
Need to get 0 B/24.7 MB of archives.
After this operation, 79.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 237706 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.11_all.deb ...
Unpacking libreoffice-common (1:6.0.7-0ubuntu0.18.04.11) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.11_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.7-9800
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.11_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by archimedes1981 on 2022-09-08
So I realised that I had installed all the third party software in /home so I formatted root partition and installed ubuntu budgie 22.hiwever it asked me for an efi system partition and I created one. My laptop is quite dated and probably doesn't support efi. When booting it's beeping like 10 times and then boots normally. Any ideas?

---

