---
title: "4 restarts before successful boot, every time"
date: 2023-11-04
forum: General Help
---

### Post by dakspyker on 2023-11-04
So every time I turn on my Lenovo Ideapad with new installed Kubuntu 23.10, the laptop starts and reboots 4 times before finally loading the grub menu. Any idea how I can fix that?

I previously had Ubuntu on the HDD, and then I installed Kububtu on the SSD. I reformatted the HDD and use it for a Backup data drive. Can I change grub to boot directly into Kubuntu without showing the grub menu?

I think the two issues might be related, but I don't know.

Thanks!

/etc/fstab:
[FONT=monospace]```
[COLOR=#000000]UUID=53b002cd-053a-43fe-9e73-9db8c9d545cf /               ext4    errors=remount-ro 0       1 [/COLOR]
# /boot/efi was on /dev/nvme0n1p1 during installation 
UUID=9A55-24AD  /boot/efi       vfat    umask=0077      0       1 
/swapfile 

```   

[/FONT]```
[FONT=monospace][COLOR=#000000]Filesystem      Size  Used Avail Use% Mounted on [/COLOR]
tmpfs           2.0G  1.8M  2.0G   1% /run 
/dev/nvme0n1p2  916G  180G  690G  21% / 
tmpfs           9.7G     0  9.7G   0% /dev/shm 
tmpfs           5.0M  8.0K  5.0M   1% /run/lock 
efivarfs        184K   70K  110K  39% /sys/firmware/efi/efivars 
/dev/nvme0n1p1  511M  6.1M  505M   2% /boot/efi 
/dev/sda1       916G  167G  703G  20% /media/johann/Backup 
tmpfs           2.0G   68K  2.0G   1% /run/user/1000
[/FONT]
```

---

### Post by VMC on 2023-11-04
[LIST]
[*]Open the /etc/default/grub file using from terminal entering: gksu gedit /etc/default/grub.
[*]Change GRUB_TIMEOUT=10 to GRUB_TIMEOUT=0.
[/LIST]

---

### Post by VMC on 2023-11-04
to check boots, use as example:
```
$ journalctl --list-boots
 [COLOR=#ff0000]0[/COLOR] a920561a3d3048e49dc24abd179e3d42 Sat 2023-11-04 06:51:08 PDT&#8212;Sat 2023-11-04 >
 
$ journalctl -b -[COLOR=#ff0000]0[/COLOR] -n
Nov 04 07:21:22 vmc-TC-885 systemd[685]: Starting GNOME Terminal Server...
Nov 04 07:21:22 vmc-TC-885 dbus-daemon[745]: [session uid=1000 pid=745] Successfully activated service 'o>
Nov 04 07:21:22 vmc-TC-885 systemd[685]: Started GNOME Terminal Server.
Nov 04 07:21:23 vmc-TC-885 systemd[685]: Started VTE child process 4452 launched by gnome-terminal-server>
Nov 04 07:21:52 vmc-TC-885 systemd[685]: Started Application launched by gnome-shell.
Nov 04 07:21:52 vmc-TC-885 dbus-daemon[745]: [session uid=1000 pid=745] Activating via systemd: service n>
Nov 04 07:21:52 vmc-TC-885 systemd[685]: Starting GNOME Terminal Server...
Nov 04 07:21:52 vmc-TC-885 dbus-daemon[745]: [session uid=1000 pid=745] Successfully activated service 'o>
Nov 04 07:21:52 vmc-TC-885 systemd[685]: Started GNOME Terminal Server.
Nov 04 07:21:52 vmc-TC-885 systemd[685]: Started VTE child process 4499 launched by gnome-terminal-server>
```Use any of your reboots to check for errors. Also 'journalctl' can be helpful.

---

### Post by dakspyker on 2023-11-04
Hi!

```
[FONT=monospace][COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ journalctl --list-boots [/COLOR]
[COLOR=#000000]IDX BOOT ID                          FIRST ENTRY                  LAST ENTRY                  [/COLOR][COLOR=#000000] [/COLOR]
-10 e1a03c069b224c5a99a6ea299f1a788d Thu 2023-11-02 17:16:56 SAST Thu 2023-11-02 19:19:23 SAST 
 -9 f14b0daf5a364a9499b67a813f9397ec Thu 2023-11-02 19:20:13 SAST Thu 2023-11-02 21:35:16 SAST 
 -8 d04878aa5a194b939f82d633f699dc44 Fri 2023-11-03 16:26:56 SAST Fri 2023-11-03 16:54:52 SAST 
 -7 5e9f351ad8d541cd944ca7d761b91953 Fri 2023-11-03 16:55:41 SAST Fri 2023-11-03 20:56:00 SAST 
 -6 a35e0bfef13e4c4892956a209e61b62d Sat 2023-11-04 08:01:01 SAST Sat 2023-11-04 08:41:43 SAST 
 -5 fbf59700ccfe442b814d1b93cfc7d07e Sat 2023-11-04 09:53:39 SAST Sat 2023-11-04 10:09:14 SAST 
 -4 3e32a122a9d84fc2b7fce01555543a45 Sat 2023-11-04 10:16:43 SAST Sat 2023-11-04 10:32:58 SAST 
 -3 f49bc160c39a492f9b290a43107bd62c Sat 2023-11-04 14:01:27 SAST Sat 2023-11-04 16:28:07 SAST 
 -2 f00a174b686a438a8e6fb03cbce4a9af Sat 2023-11-04 16:35:14 SAST Sat 2023-11-04 16:36:22 SAST 
 -1 002a22240d5948d58d08d227687068ce Sat 2023-11-04 18:38:53 SAST Sat 2023-11-04 17:23:21 SAST 
  0 9d0657c4b7e64793ab3c71ba46920db7 Sat 2023-11-04 17:27:13 SAST Sat 2023-11-04 17:33:42 SAST
[/FONT]
```

and 

```
[FONT=monospace][COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ journalctl -b -0 -n [/COLOR]
Nov 04 20:41:10 sny systemd[1]: Starting NetworkManager-dispatcher.service - Network Manager Script Dispatcher Service... 
Nov 04 20:41:11 sny dbus-daemon[700]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher' 
Nov 04 20:41:11 sny systemd[1]: Started NetworkManager-dispatcher.service - Network Manager Script Dispatcher Service. 
Nov 04 20:41:21 sny systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully. 
Nov 04 20:41:58 sny PackageKit[1830]: [COLOR=#8a8a8a]daemon quit[/COLOR][COLOR=#000000] [/COLOR]
Nov 04 20:41:58 sny systemd[1]: packagekit.service: Deactivated successfully. 
Nov 04 20:41:58 sny systemd[1]: packagekit.service: Consumed 24.235s CPU time. 
Nov 04 20:42:02 sny wpa_supplicant[770]: [COLOR=#000000]**wlp0s20f3: WPA: Group rekeying completed with 18:fd:74:5c:e8:04 [GTK=CCMP]**[/COLOR][COLOR=#000000] [/COLOR]
Nov 04 20:42:36 sny rtkit-daemon[1055]: [COLOR=#8a8a8a]Supervising 8 threads of 5 processes of 1 users.[/COLOR][COLOR=#000000] [/COLOR]
Nov 04 20:42:36 sny rtkit-daemon[1055]: [COLOR=#8a8a8a]Supervising 8 threads of 5 processes of 1 users.[/COLOR]
[/FONT]
```

I'm not sure what I am looking at. Is the problem happening BEFORE the linux system starts, eg. in the BIOS?

It didn't do this from the beginning, seems like something changed before this started happening.

I can hear the HDD start up, and then the laptop switches off, starts up again, HDD goes, switch off, etc.. Exactly four times and then it boots normally.

Thanks!!

---

### Post by MAFoElffen on 2023-11-04
I noticed something in your post above... Look at your contents for your /etc/fstab file...  Was that output cut-off by coincidence?

> **dakspyker said:**
> 
/etc/fstab:
[FONT=monospace]```
[COLOR=#000000]UUID=53b002cd-053a-43fe-9e73-9db8c9d545cf /               ext4    [/COLOR][COLOR=#ff0000]errors=remount-ro[/COLOR][COLOR=#000000] 0       1 [/COLOR]
# /boot/efi was on /dev/nvme0n1p1 during installation 
UUID=9A55-24AD  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1 
/swapfile [COLOR=#ff0000]## <-- ??? This is not the whole line that should be here ???[/COLOR]

```   
[/FONT]
Look at some of mine as examples:
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep -v '#' /etc/fstab
/dev/disk/by-uuid/281F-B438 /boot/efi vfat defaults,umask=0077 0 1
/boot/efi/grub /boot/grub none defaults,bind 0 0
/dev/mapper/swap none swap defaults 0 0

## This is from a default install of DEV Noble 24.04 Server...
mafoelffen@noble-s03:~$ grep . /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-dCOMjmLaoo08uAJDw4NGPLtSvfdlw81beeTNowsXHu13tUobeM5wxfnfLtIOje5i / ext4 defaults 0 1
# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/1fb98061-6482-49ea-8db7-714224ec7138 /boot ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
/dev/disk/by-uuid/ABD5-CD38 /boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0

## Here is the swap.img info...
mafoelffen@noble-s03:~$ ls -lah /swap.img
-rw------- 1 root root 2.9G Nov  4 01:14 /swap.img

```
First, with a mount involving the EFI and the root drive (/) partitions, the first option i both should be "defaults"... Second, if that is the whole contents of that fstab file, then the swap mount line is incomplete and would throw a error...

Could you please change your /etc/fstab accordingly, and repost it's contents?

Let me spin up one of my DEV test-case templates for Kubuntu to see if it was different on the default fstab options during installation. (I believe they are like what I posted also, but to confirm that.)

---

### Post by MAFoElffen on 2023-11-04
Hmmm... This seems to be something in Kubuntu:
```

mafoelffen@kubuntu-2310-0:~$ grep . /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vgkubuntu-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/vda1 during installation
UUID=EE67-4C6E  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vgkubuntu-swap_1 none            swap    sw              0       0

```
So is probably fine, without the defaults option(?)...

---

### Post by dakspyker on 2023-11-05
Hi,
All this is a bit over my head, but I'll try to keep up. So first the fstab file is like that:

```
[FONT=monospace][COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  grep -v '#' /etc/fstab [/COLOR]
UUID=53b002cd-053a-43fe-9e73-9db8c9d545cf /               ext4    errors=remount-ro 0       1 
UUID=9A55-24AD  /boot/efi       vfat    umask=0077      0       1 
/swapfile                                 none            swap    sw              0       0 
[COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

Am I understanding correctly, I should change it to look like this?

```
[FONT=monospace][COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  grep -v '#' /etc/fstab [/COLOR]
UUID=53b002cd-053a-43fe-9e73-9db8c9d545cf /               ext4    errors=remount-ro 0       1 
UUID=9A55-24AD  /boot/efi       vfat    umask=0077      0       1 /swapfile                                 none            swap    sw              0       0 
[COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

Why it is like that I do not know, I did not make any manual changes in /etc/ except for adding a line to crontab.

I found a discussion about "defaults" here:
[https://unix.stackexchange.com/questions/191405/do-you-need-to-specify-the-defaults-option-in-fstab](https://unix.stackexchange.com/questions/191405/do-you-need-to-specify-the-defaults-option-in-fstab)

But I'm not sure if I understand it. Looks like mine is OK without defaults, because there are some other options already?  (the "umask" part.) Do you think I should add it to look like this:

```
[FONT=monospace]UUID=53b002cd-053a-43fe-9e73-9db8c9d545cf /               ext4    defaults,errors=remount-ro 0       1 
UUID=9A55-24AD  /boot/efi       vfat    defaults,umask=0077      0       1  /swapfile                                 none            swap    sw               0       0 [/FONT]
```

You were very helpful to me in my last post, [https://ubuntuforums.org/showthread.php?t=2492110](https://ubuntuforums.org/showthread.php?t=2492110)

I decided on KUbuntu, and the install went very easy, only took me a few hours to add all the software and things back, and I am very happy! Now only to solve this reboot/startup issue, and I'll be golden.

Thanks again!

---

### Post by MAFoElffen on 2023-11-05
> **dakspyker said:**
> Hi,
All this is a bit over my head, but I'll try to keep up. So first the fstab file is like that:

```
[FONT=monospace][COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  grep -v '#' /etc/fstab [/COLOR]
UUID=53b002cd-053a-43fe-9e73-9db8c9d545cf /               ext4    errors=remount-ro 0       1 
UUID=9A55-24AD  /boot/efi       vfat    umask=0077      0       1 
/swapfile                                 none            swap    sw              0       0 
[COLOR=#54ff54]**johann@sny**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

This is fine. Your first post with it must have been without all of what was there.

---

### Post by dakspyker on 2023-11-05
> **MAFoElffen said:**
> This is fine. Your first post with it must have been without all of what was there.

Thanks!

So this means fstab and/or grub is not the problem with the rebooting, right? Any idea where else I can look?

Thanks!!

---

### Post by tea for one on 2023-11-05
Power off PC.
Remove all peripheral devices (inc. your reformatted backup HDD).
Power on.

I'm expecting a wonderful result ;)

---

### Post by dakspyker on 2023-11-06
Hi!
The reformatted backup HDD is an internal drive. :o(

Is there something wrong with the partition tables or something like that with that drive?

---

