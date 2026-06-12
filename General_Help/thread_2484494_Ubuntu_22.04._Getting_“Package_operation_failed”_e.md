---
title: "Ubuntu 22.04. Getting “Package operation failed” error when trying to update."
date: 2023-02-28
forum: General Help
---

### Post by Advait on 2023-02-28
[COLOR=#000000][FONT=Arial]Newbie here. I’m running Ubuntu 22.04 in VBox. I’m getting “Package operation failed. The installation or removal of a software package failed.” error when running Software Updater. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I ran sudo rm -Rf /var/lib/apt/list/* and then sudo apt clean but didn’t help.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Any ideas how to fix this? Need to see some kind of log file? [/FONT][/COLOR]

---

### Post by Bashing-om on 2023-02-28
Advait Hello

Please post back - between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Such then that we see the errors and in context.

[INDENT]it's in the process, somewhere
[/INDENT]

---

### Post by Advait on 2023-03-01
Here it is. Anything clues to solve issue?

```

advait@advait-VirtualBox:~$ sudo apt update
[sudo] password for advait: 
Hit:1 http://in.archive.ubuntu.com/ubuntu jammy InRelease
Get:2 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease [107 kB]
Get:5 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages [259 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages [448 kB]
Get:7 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [646 kB]
Get:8 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [905 kB]
Get:9 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [135 kB]     
Get:10 http://security.ubuntu.com/ubuntu jammy-security/main amd64 DEP-11 Metadata [41.4 kB]  
Get:11 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [8,524 B]           
Get:12 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [694 kB]                  
Get:13 http://in.archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [199 kB]             
Get:14 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 DEP-11 Metadata [102 kB]     
Get:15 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [13.6 kB]              
Get:16 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages [598 kB]                     
Get:17 http://security.ubuntu.com/ubuntu jammy-security/universe i386 Packages [510 kB]             
Get:18 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [874 kB]                                                            
Get:19 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [110 kB]                                                             
Get:20 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 DEP-11 Metadata [17.1 kB]                                                     
Get:21 http://security.ubuntu.com/ubuntu jammy-security/universe DEP-11 48x48 Icons [15.2 kB]                                                        
Get:22 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [171 kB]                                                            
Get:23 http://security.ubuntu.com/ubuntu jammy-security/universe DEP-11 64x64 Icons [24.3 kB]                                                        
Get:24 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 DEP-11 Metadata [269 kB]                                                     
Get:25 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [13.4 kB]                                                      
Get:26 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 48x48 Icons [173 kB]                                                        
Get:27 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe DEP-11 64x64 Icons [260 kB]                                                        
Get:28 http://in.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [17.8 kB]                                                     
Get:29 http://in.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]                                                    
Get:30 http://in.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [7,992 B]                                                      
Get:31 http://in.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12.5 kB]                                                  
Fetched 6,861 kB in 10s (661 kB/s)                                                                                                                   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
39 packages can be upgraded. Run 'apt list --upgradable' to see them.
advait@advait-VirtualBox:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2 libllvm13
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  evince evince-common fonts-opensymbol gir1.2-pango-1.0 gnome-remote-desktop libevdocument3-4 libevview3-3 libmbim-glib4 libmbim-proxy libmm-glib0
  libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libqmi-glib5 libqmi-proxy libsasl2-2 libsasl2-modules libsasl2-modules-db
  libsasl2-modules-gssapi-mit libsnmp-base libsnmp40 modemmanager python3-macaroonbakery python3-software-properties software-properties-common
  software-properties-gtk
The following packages will be upgraded:
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 intel-microcode isc-dhcp-client isc-dhcp-common libcurl3-gnutls libcurl4 libgnutls30
  libjavascriptcoregtk-4.0-18 libnss3 libwebkit2gtk-4.0-37 tar
12 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
10 standard LTS security updates
Need to get 1,542 kB/35.1 MB of archives.
After this operation, 6,285 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 tar amd64 1.34+dfsg-1ubuntu0.1.22.04.1 [295 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgnutls30 amd64 3.7.3-4ubuntu1.2 [968 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 isc-dhcp-client amd64 4.4.1-2.3ubuntu2.4 [235 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 isc-dhcp-common amd64 4.4.1-2.3ubuntu2.4 [45.0 kB]
Fetched 1,542 kB in 3s (494 kB/s)          
Rsyncing /boot into the filesystem before the call to timeshift.
Rsyncing /boot/efi into the filesystem before the call to timeshift.
Using system disk as snapshot device for creating snapshots in BTRFS mode
Mounted '/dev/sda4' at '/run/timeshift/backup'
Mounted '/dev/sda5' at '/run/timeshift/backup-home'
Creating new backup...(BTRFS)
Saving to device: /dev/sda4, mounted at path: /run/timeshift/backup
Saving to device: /dev/sda5, mounted at path: /run/timeshift/backup-home
Created directory: /run/timeshift/backup/timeshift-btrfs/snapshots/2023-03-01_16-39-12
Created subvolume snapshot: /run/timeshift/backup/timeshift-btrfs/snapshots/2023-03-01_16-39-12/@
Created directory: /run/timeshift/backup-home/timeshift-btrfs/snapshots/2023-03-01_16-39-12
Created subvolume snapshot: /run/timeshift/backup-home/timeshift-btrfs/snapshots/2023-03-01_16-39-12/@home
Created control file: /run/timeshift/backup/timeshift-btrfs/snapshots/2023-03-01_16-39-12/info.json
BTRFS Snapshot saved successfully (0s)
Tagged snapshot '2023-03-01_16-39-12': ondemand
------------------------------------------------------------------------------

/dev/sda4 is mounted at: /run/timeshift/backup, options: rw,relatime,compress=zstd:3,space_cache=v2,subvolid=5,subvol=/


/dev/sda5 is mounted at: /run/timeshift/backup-home, options: rw,relatime,compress=zstd:3,space_cache=v2,subvolid=5,subvol=/

------------------------------------------------------------------------------
Removing snapshot: 2023-02-28_17-20-59
Deleting subvolume: @home (Id:264)
Deleted subvolume: @home (Id:264)

Destroying qgroup: 0/264
Destroyed qgroup: 0/264

Deleting subvolume: @ (Id:264)
Deleted subvolume: @ (Id:264)

Destroying qgroup: 0/264
Destroyed qgroup: 0/264

Deleted directory: /run/timeshift/backup-home/timeshift-btrfs/snapshots/2023-02-28_17-20-59
Deleted directory: /run/timeshift/backup/timeshift-btrfs/snapshots/2023-02-28_17-20-59
Removed snapshot: 2023-02-28_17-20-59
------------------------------------------------------------------------------
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-32-generic
Found initrd image: /boot/initrd.img-5.19.0-32-generic
Found linux image: /boot/vmlinuz-5.15.0-25-generic
Found initrd image: /boot/initrd.img-5.15.0-25-generic
Found memtest86+ image: /@/boot/memtest86+.elf
Found memtest86+ image: /@/boot/memtest86+.bin
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Detecting snapshots ...
Found snapshot: 2023-03-01 16:39:12 | timeshift-btrfs/snapshots/2023-03-01_16-39-12/@ | ondemand | {timeshift-autosnap-apt} {created before call to APT}                       |
Found snapshot: 2023-02-28 18:30:12 | timeshift-btrfs/snapshots/2023-02-28_18-32-03/@ | ondemand | Before restoring '2023-02-28 18:30:12'                                      |
Found snapshot: 2023-02-28 18:18:44 | timeshift-btrfs/snapshots/2023-02-28_18-18-44/@ | ondemand | After update Menu bar.                                                      |
Found snapshot: 2023-02-28 18:14:24 | timeshift-btrfs/snapshots/2023-02-28_18-14-24/@ | ondemand | After create Flameshot fav icon.                                            |
Found snapshot: 2023-02-28 18:12:27 | timeshift-btrfs/snapshots/2023-02-28_18-12-27/@ | ondemand | After install Flameshot.                                                    |
Found snapshot: 2023-02-28 18:10:27 | timeshift-btrfs/snapshots/2023-02-28_18-10-27/@ | ondemand | B4 install Flameshot. {timeshift-autosnap-apt} {created before call to APT} |
Found snapshot: 2023-02-28 17:21:04 | timeshift-btrfs/snapshots/2023-02-28_17-21-04/@ | ondemand | {timeshift-autosnap-apt} {created before call to APT}                       |
Found snapshot: 2023-02-28 17:00:07 | timeshift-btrfs/snapshots/2023-02-28_17-00-07/@ | daily    | N/A                                                                         |
Found snapshot: 2023-02-28 13:07:58 | timeshift-btrfs/snapshots/2023-02-28_13-07-58/@ | ondemand | After system update                                                         |
Found snapshot: 2023-02-28 13:03:18 | timeshift-btrfs/snapshots/2023-02-28_13-03-18/@ | ondemand | B4 system update.                                                           |
Found snapshot: 2023-02-23 20:23:41 | timeshift-btrfs/snapshots/2023-02-23_20-23-41/@ | ondemand | N/A                                                                         |
Found snapshot: 2023-02-23 20:21:32 | timeshift-btrfs/snapshots/2023-02-23_20-21-32/@ | ondemand | N/A                                                                         |
Found 12 snapshot(s)
Unmount /tmp/grub-btrfs.u7ychtlTkB .. Success
done
(Reading database ... 176624 files and directories currently installed.)
Preparing to unpack .../tar_1.34+dfsg-1ubuntu0.1.22.04.1_amd64.deb ...
Unpacking tar (1.34+dfsg-1ubuntu0.1.22.04.1) over (1.34+dfsg-1build3) ...
Setting up tar (1.34+dfsg-1ubuntu0.1.22.04.1) ...
(Reading database ... 176624 files and directories currently installed.)
Preparing to unpack .../libgnutls30_3.7.3-4ubuntu1.2_amd64.deb ...
Unpacking libgnutls30:amd64 (3.7.3-4ubuntu1.2) over (3.7.3-4ubuntu1.1) ...
Setting up libgnutls30:amd64 (3.7.3-4ubuntu1.2) ...
(Reading database ... 176624 files and directories currently installed.)
Preparing to unpack .../0-isc-dhcp-client_4.4.1-2.3ubuntu2.4_amd64.deb ...
Unpacking isc-dhcp-client (4.4.1-2.3ubuntu2.4) over (4.4.1-2.3ubuntu2.3) ...
Preparing to unpack .../1-isc-dhcp-common_4.4.1-2.3ubuntu2.4_amd64.deb ...
Unpacking isc-dhcp-common (4.4.1-2.3ubuntu2.4) over (4.4.1-2.3ubuntu2.3) ...
Preparing to unpack .../2-gir1.2-webkit2-4.0_2.38.5-0ubuntu0.22.04.1_amd64.deb ...
Unpacking gir1.2-webkit2-4.0:amd64 (2.38.5-0ubuntu0.22.04.1) over (2.38.4-0ubuntu0.22.04.1) ...
Preparing to unpack .../3-gir1.2-javascriptcoregtk-4.0_2.38.5-0ubuntu0.22.04.1_amd64.deb ...
Unpacking gir1.2-javascriptcoregtk-4.0:amd64 (2.38.5-0ubuntu0.22.04.1) over (2.38.4-0ubuntu0.22.04.1) ...
Preparing to unpack .../4-libwebkit2gtk-4.0-37_2.38.5-0ubuntu0.22.04.1_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37:amd64 (2.38.5-0ubuntu0.22.04.1) over (2.38.4-0ubuntu0.22.04.1) ...
Preparing to unpack .../5-libjavascriptcoregtk-4.0-18_2.38.5-0ubuntu0.22.04.1_amd64.deb ...
Unpacking libjavascriptcoregtk-4.0-18:amd64 (2.38.5-0ubuntu0.22.04.1) over (2.38.4-0ubuntu0.22.04.1) ...
Preparing to unpack .../6-libcurl3-gnutls_7.81.0-1ubuntu1.8_amd64.deb ...
Unpacking libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.8) over (7.81.0-1ubuntu1.7) ...
Preparing to unpack .../7-libcurl4_7.81.0-1ubuntu1.8_amd64.deb ...
Unpacking libcurl4:amd64 (7.81.0-1ubuntu1.8) over (7.81.0-1ubuntu1.7) ...
Preparing to unpack .../8-libnss3_2%3a3.68.2-0ubuntu1.2_amd64.deb ...
Unpacking libnss3:amd64 (2:3.68.2-0ubuntu1.2) over (2:3.68.2-0ubuntu1.1) ...
Preparing to unpack .../9-intel-microcode_3.20230214.0ubuntu0.22.04.1_amd64.deb ...
Unpacking intel-microcode (3.20230214.0ubuntu0.22.04.1) over (3.20220809.0ubuntu0.22.04.1) ...
Setting up intel-microcode (3.20230214.0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.38.5-0ubuntu0.22.04.1) ...
Setting up isc-dhcp-client (4.4.1-2.3ubuntu2.4) ...
Installing new version of config file /etc/apparmor.d/sbin.dhclient ...
Setting up libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.8) ...
Setting up libnss3:amd64 (2:3.68.2-0ubuntu1.2) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.38.5-0ubuntu0.22.04.1) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.38.5-0ubuntu0.22.04.1) ...
Setting up libcurl4:amd64 (7.81.0-1ubuntu1.8) ...
Setting up isc-dhcp-common (4.4.1-2.3ubuntu2.4) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.38.5-0ubuntu0.22.04.1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Processing triggers for initramfs-tools (0.140ubuntu13.1) ...
update-initramfs: Generating /boot/initrd.img-5.19.0-32-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=9de3b273-b445-4dda-a27c-22638ce1962e)
I: Set the RESUME variable to override this.
advait@advait-VirtualBox:~$ ^C
advait@advait-VirtualBox:~$ 

```

---

### Post by Advait on 2023-03-01
Update, I just clicked on the Software Updater icon and it ran and it said "Your computer is up to date." So looks like the problem is fixed.
I want to compliment Bashing-om for using his/her/their psycho-kinetic telepathic powers to fix my problem from another continent. That is serious next-level tech support. :P You rock! :guitar:

PS: When I tried to edit my previous post it just showed a blank screen. So posts with code tags can't be edited? That's a little odd.

---

### Post by ActionParsnip on 2023-03-01
Mark as solved if there is no more issue

---

### Post by Advait on 2023-03-02
I'm now getting errors with apt update. See here. How to fix?

```

advait@advait-VirtualBox:~$ apt update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
advait@advait-VirtualBox:~$ 

```

---

### Post by Advait on 2023-03-02
Update, I ran these and now it's working.

```
[COLOR=#333333][FONT=Monaco]sudo rm -Rf /var/lib/apt/lists/*
sudo apt clean

[/FONT][/COLOR]

```

---

### Post by ActionParsnip on 2023-03-02
> **Advait said:**
> I'm now getting errors with apt update. See here. How to fix?

```

advait@advait-VirtualBox:~$ apt update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
advait@advait-VirtualBox:~$ 

```

You need to prefix commands with apt in them with "sudo"

---

### Post by Advait on 2023-03-02
> **ActionParsnip said:**
> You need to prefix commands with apt in them with "sudo"

OK, thanks.

---

