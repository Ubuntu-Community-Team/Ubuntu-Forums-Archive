---
title: "Ubuntu 22.04. How to get all btrfs snapshots to appear in grub menu snapshot list?"
date: 2023-02-28
forum: General Help
---

### Post by Advait on 2023-02-28
[COLOR=#000000][FONT=Arial]Newbie here. I got a tech support person to install Ubuntu 22.04 in VBox with Btrfs on my root and home directories. He also installed timeshift-autosnap-apt and grub-btrfs and they’re working. So the timeshift-autosnap Btrfs snapshots are now appearing in my grub menu (nice!). But my manual Timeshift snapshots are not. &#9785;&#65039;[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]How can I get all my Btrfs snapshots to appear in the grub menu snapshot list?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I can hack around this by doing an apt update whenever I need a snapshot done, but I prefer a real solution.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]PS: Does Snapper work on Ubuntu 22.04? If not, is there something like Snapper for Ubuntu?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-02-28
Maybe someone that is more familiar with BTRFS than me can help answer you. I personally use mostly ZFS.

IDK about adding manual snapshots to the Grub Menu. I know with ZFS, with ZSys, only the pools setup through ZSys get added to the boot menu... All manual, you have to locate and work with manually. Even with setting up BTRFS and ZFS through the installer, that is only about less than 10% of the capabilities of those two Filesystem/Volume Managers capabilities and options that are being utilized. Most are managed manually through the CLI, though there are some GUI tools.
> **Advait said:**
> [COLOR=#000000][FONT=Arial]PS: Does Snapper work on Ubuntu 22.04? If not, is there something like Snapper for Ubuntu?[/FONT][/COLOR]
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache show snapper
Package: snapper
Architecture: amd64
Version: 0.9.0-1
Priority: optional
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Hideki Yamane <henrich@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1862
Depends: libboost-thread1.74.0 (>= 1.74.0), libc6 (>= 2.34), libdbus-1-3 (>= 1.9.14), libgcc-s1 (>= 3.3.1), libjson-c5 (>= 0.15), libmount1 (>= 2.24.2), libsnapper5 (>= 0.9.0), libstdc++6 (>= 11), libtinfo6 (>= 6)
Enhances: btrfs-progs
Filename: pool/universe/s/snapper/snapper_0.9.0-1_amd64.deb
Size: 415418
MD5sum: a4611a41f781eaf3e6b029d3466aa379
SHA1: 4bb2bd6babe22b81db1542b10e7e71b3e442cf4e
SHA256: a7d8f90d9bf006af68309ddf3fff055d8b6c78a9834fd467a79971559a093bec
SHA512: 6dc63cb4dfb8063991f387143845e01725e09e35d31ec29b0fc2e6aad8ffa8686f80040a9227522e629d87c364d83e5106491ffa4536d6bb6bc3281312a3b344
Homepage: http://snapper.io/
Description-en: Linux filesystem snapshot management tool
 Snapper is a tool for Linux filesystem snapshot management. Apart from the
 obvious creation and deletion of snapshots, it can compare snapshots and revert
 differences between snapshots. In simple terms, this allows root and non-root
 users to view older versions of files and revert changes.
 .
 The features include:
   * Manually create snapshots
   * Automatically create snapshots, e.g. when using a package manager
   * Automatically create timeline of snapshots
   * Show and revert changes between snapshots
   * Works with btrfs and thin-provisioned LVM volumes
   * Supports Access Control Lists and Extended Attributes
   * Automatic cleanup of old snapshots
   * Command line interface
   * D-Bus interface
   * PAM module to create snapshots during login and logout (libpam-snapper)
Description-md5: 24bd8c205566cf532c10f95f37e5ae33

```
[https://installati.one/install-snapper-ubuntu-22-04/](https://installati.one/install-snapper-ubuntu-22-04/)

---

### Post by #&amp;thj^% on 2023-02-28
+1 to the above:
```
sudo snapper list
   # | Type   | Pre # | Date                            | User | Cleanup | Description | Userdata
-----+--------+-------+---------------------------------+------+---------+-------------+---------
  0  | single |       |                                 | root |         | current     |         
140  | pre    |       | Tue 28 Feb 2023 07:56:31 AM MST | root | number  | apt         |         
141  | post   |   140 | Tue 28 Feb 2023 07:56:36 AM MST | root | number  | apt         |         
142  | pre    |       | Tue 28 Feb 2023 07:59:17 AM MST | root | number  | apt         |         
143  | pre    |       | Tue 28 Feb 2023 07:59:17 AM MST | root | number  | apt         |         
144  | post   |   143 | Tue 28 Feb 2023 08:00:10 AM MST | root | number  | apt         |         
145  | pre    |       | Tue 28 Feb 2023 08:27:08 AM MST | root | number  | apt         |         
146  | post   |   145 | Tue 28 Feb 2023 08:27:10 AM MST | root | number  | apt         |         
147  | pre    |       | Tue 28 Feb 2023 11:01:11 AM MST | root | number  | apt         |         
148  | post   |   147 | Tue 28 Feb 2023 11:01:16 AM MST | root | number  | apt         |         
149  | pre    |       | Tue 28 Feb 2023 02:40:24 PM MST | root | number  | apt         |         
150  | post   |   149 | Tue 28 Feb 2023 02:40:27 PM MST | root | number  | apt         |         
151  | pre    |       | Tue 28 Feb 2023 02:53:47 PM MST | root | number  | apt         |         
152  | post   |   151 | Tue 28 Feb 2023 02:53:54 PM MST | root | number  | apt         |         
153  | pre    |       | Tue 28 Feb 2023 03:11:39 PM MST | root | number  | apt         |         
154  | post   |   153 | Tue 28 Feb 2023 03:11:44 PM MST | root | number  | apt         |         
155  | pre    |       | Tue 28 Feb 2023 03:15:36 PM MST | root | number  | apt         |         
156  | post   |   155 | Tue 28 Feb 2023 03:15:36 PM MST | root | number  | apt         |         
157  | pre    |       | Tue 28 Feb 2023 03:21:21 PM MST | root | number  | apt         |         
158  | post   |   157 | Tue 28 Feb 2023 03:21:27 PM MST | root | number  | apt         |         
159  | pre    |       | Tue 28 Feb 2023 03:30:02 PM MST | root | number  | apt         |         
160  | pre    |       | Tue 28 Feb 2023 03:30:02 PM MST | root | number  | apt         |         
161  | post   |   160 | Tue 28 Feb 2023 03:30:08 PM MST | root | number  | apt         |         
162  | pre    |       | Tue 28 Feb 2023 03:30:42 PM MST | root | number  | apt         |         
163  | post   |   162 | Tue 28 Feb 2023 03:30:46 PM MST | root | number  | apt         |         
164  | pre    |       | Tue 28 Feb 2023 03:36:37 PM MST | root | number  | apt         |         
165  | post   |   164 | Tue 28 Feb 2023 03:36:40 PM MST | root | number  | apt         |         
166  | pre    |       | Tue 28 Feb 2023 03:38:12 PM MST | root | number  | apt         |         
167  | post   |   166 | Tue 28 Feb 2023 03:38:13 PM MST | root | number  | apt         |         


```
will help to keep only what you need as well IE:
```
 sudo snapper delete 153-167
## no return shown
```
check with:
```
sudo snapper list
   # | Type   | Pre # | Date                            | User | Cleanup | Description | Userdata
-----+--------+-------+---------------------------------+------+---------+-------------+---------
  0  | single |       |                                 | root |         | current     |         
140  | pre    |       | Tue 28 Feb 2023 07:56:31 AM MST | root | number  | apt         |         
141  | post   |   140 | Tue 28 Feb 2023 07:56:36 AM MST | root | number  | apt         |         
142  | pre    |       | Tue 28 Feb 2023 07:59:17 AM MST | root | number  | apt         |         
143  | pre    |       | Tue 28 Feb 2023 07:59:17 AM MST | root | number  | apt         |         
144  | post   |   143 | Tue 28 Feb 2023 08:00:10 AM MST | root | number  | apt         |         
145  | pre    |       | Tue 28 Feb 2023 08:27:08 AM MST | root | number  | apt         |         
146  | post   |   145 | Tue 28 Feb 2023 08:27:10 AM MST | root | number  | apt         |         
147  | pre    |       | Tue 28 Feb 2023 11:01:11 AM MST | root | number  | apt         |         
148  | post   |   147 | Tue 28 Feb 2023 11:01:16 AM MST | root | number  | apt         |         
149  | pre    |       | Tue 28 Feb 2023 02:40:24 PM MST | root | number  | apt         |         
150  | post   |   149 | Tue 28 Feb 2023 02:40:27 PM MST | root | number  | apt         |         
151  | pre    |       | Tue 28 Feb 2023 02:53:47 PM MST | root | number  | apt         |         
152  | post   |   151 | Tue 28 Feb 2023 02:53:54 PM MST | root | number  | apt         |         

```
```
apt policy snapper
snapper:
  Installed: 0.10.4-1
  Candidate: 0.10.4-1
  Version table:
 *** 0.10.4-1 500
        500 https://deb.debian.org/debian unstable/main amd64 Packages
        500 https://deb.debian.org/debian bookworm/main amd64 Packages
        100 /var/lib/dpkg/status

```
To be fair there is also " Btrbk" and Timeshift which I don't use so no help there.
```
man btrbk
```
All good reads to help an informed decision.

---

### Post by Advait on 2023-03-02
Thanks. I'll research Snapper more and Btrbk.

Regarding my original post: I'm still wondering if there's a way to get all my latest snapshots to appear in the grub menu. Is that possible?

---

### Post by #&amp;thj^% on 2023-03-02
> **Advait said:**
> Thanks. I'll research Snapper more and Btrbk.

Regarding my original post: I'm still wondering if there's a way to get all my latest snapshots to appear in the grub menu. Is that possible?
This has always been about that>>>adding to grub-menu-options...Yes!
EDIT: You should link your two threads: [https://ubuntuforums.org/showthread.php?t=2483668#top](https://ubuntuforums.org/showthread.php?t=2483668#top)

---

### Post by grahammechanical on 2023-03-02
A program called Whiptail puts the recovery menu on the screen and responds to the actions selected. Whiptail reads a script called recovery-menu which lists the options. When an option is selected Whiptail will then read and action the related script. Places to look.

/lib/recovery-mode/recovery-menu
/lib/recovery-mode/options/apt-snapshots
/lib/recovery-mode/options/clean
/lib/recovery-mode/options/dpkg
/lib/recovery-mode/options/failsafeX
/lib/recovery-mode/options/fsck
/lib/recovery-mode/options/grub
/lib/recovery-mode/options/network
/lib/recovery-mode/options/root
/lib/recovery-mode/options/system-summary

After studying how the scripts work it is possible to copy one of these scripts, modify it appropriately and in this way create additional recovery menu options. Years ago I was able to create a special snapshot menu with the following options:

Exit - Exit utility - return to terminal
apt-snapshot - Revert to old snapshot and reboot
delete older than - Delete apt-snapshots older than 2 days. [the length of time can be set when writing the new script]
list-older-than - list apt-snapshots older than 2 days
list-snapshots - Lists of apt-snapshots
take-apt-snapshot - Create a new apt-snapshot + date + time

The new script must have permission to run. And /lib/recovery-menu/l10n.sh is an important file. Scripts will not run without it. Another location that you might need to know is:

/lib/systemd/system/friendly-recovery-service
/lib/systemd/system/friendly-recovery-target

I have no idea what those two files do but I guess they are important. I no longer have the new scripts I created. So, I cannot help you there.

Regards

---

### Post by #&amp;thj^% on 2023-03-02
+1 ^^^^^^^
Good grief that was a long time ago, I just counted back...I'll remain silent. :D
```
whiptail/testing,kaisen-rolling,now 0.52.23-1+b1 amd64 [installed]
  Displays user-friendly dialog boxes from shell scripts


```

---

### Post by MAFoElffen on 2023-03-02
I just looked for info on Whiptail scripting and using it with the Grub Menu: [https://askubuntu.com/questions/1019213/display-grub-menu-and-options-without-rebooting](https://askubuntu.com/questions/1019213/display-grub-menu-and-options-without-rebooting)

---

### Post by Advait on 2023-03-03
OP here. I put Whiptail on my research list. Thanks for the links.

---

