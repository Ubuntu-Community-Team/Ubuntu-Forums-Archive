---
title: "Failed Update"
date: 2017-03-30
forum: General Help
---

### Post by DeadlyOats on 2017-03-30
I'm trying to install the latest Kubuntu/Ubuntu security updates.  Like I always do, I opened Update Manager, and searched for updates.  Currently, it's showing me several packages for Firefox, and the Linux kernel updates, plus a whole bunch of other packages.

I put in my password, hit enter.  The first time, it spent time downloading the packages, then when it tried to install the packages, it failed.  Subsequently, it doesn't try to download anything, it just insta-fails.

I get a dialog box with "Failed to Apply Changes -- Update Manager ?"  In the dialog box is a red box with a white "X", and the message, "An error occurred while applying changes:

When I click on the Details button, nothing opens.  No details are given.

I tried rebooting Kubuntu, to see if that would do anything.  No progress is achieved, same problem persists.

How do I fix this?  I'm using Kubuntu 16.04.

---

### Post by Bucky Ball on 2017-03-30
Open a terminal and:

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

The last command will not upgrade your release to a newer one, just what needs to be upgraded in your current release. Please post any and all error messages you receive from any of the above three commands. Please use code tags (see instructions for using in my signature link at bottom of this post).

---

### Post by DeadlyOats on 2017-03-31
> **Bucky Ball said:**
> Open a terminal and:

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

The last command will not upgrade your release to a newer one, just what needs to be upgraded in your current release. Please post any and all error messages you receive from any of the above three commands. Please use code tags (see instructions for using in my signature link at bottom of this post).

```
myusername@MYMACHINE:~$ sudo apt autoremove
[sudo] password for myusername: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-70-generic : Depends: linux-image-4.4.0-70-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-70-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

```
myusername@MYMACHINE:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-70-generic : Depends: linux-image-4.4.0-70-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-70-generic but it is not installed
E: Unmet dependencies. Try using -f.
myusername@MYMACHINE:~$
```

Here's what I got.

---

### Post by Impavidus on 2017-03-31
Next try```
sudo apt -f install
```as the error message suggests.

---

### Post by DeadlyOats on 2017-03-31
> **Impavidus said:**
> Next try```
sudo apt -f install
```as the error message suggests.

So, I ran this.  I got a choice Y/N.  I chose Y.

It ran, and at the end gave me this:

```
myname@MYMACHINE:~$ sudo apt -f install
[sudo] password for myname: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-65
  linux-headers-4.4.0-65-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic
  linux-image-4.4.0-64-generic linux-image-4.4.0-65-generic
  linux-image-4.4.0-70-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-65-generic
  linux-image-extra-4.4.0-70-generic snap-confine
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-generic linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic
  linux-headers-generic linux-image-4.4.0-70-generic
  linux-image-4.4.0-71-generic linux-image-extra-4.4.0-71-generic
  linux-image-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic
  linux-image-4.4.0-70-generic linux-image-4.4.0-71-generic
  linux-image-extra-4.4.0-71-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 5 newly installed, 0 to remove and 15 not upgraded.
15 not fully installed or removed.
Need to get 0 B/90.4 MB of archives.
After this operation, 363 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package linux-image-4.4.0-71-generic.
(Reading database ... 452040 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-71-generic (4.4.0-71.92) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-71-generic' to '/boot/vmlinuz-4.4.0-71-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
Selecting previously unselected package linux-image-extra-4.4.0-71-generic.
Preparing to unpack .../linux-image-extra-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Unpacking linux-image-extra-4.4.0-71-generic (4.4.0-71.92) ...
Preparing to unpack .../linux-generic_4.4.0.71.77_amd64.deb ...
Unpacking linux-generic (4.4.0.71.77) over (4.4.0.70.76) ...
Preparing to unpack .../linux-image-generic_4.4.0.71.77_amd64.deb ...
Unpacking linux-image-generic (4.4.0.71.77) over (4.4.0.70.76) ...
Selecting previously unselected package linux-headers-4.4.0-71.
Preparing to unpack .../linux-headers-4.4.0-71_4.4.0-71.92_all.deb ...
Unpacking linux-headers-4.4.0-71 (4.4.0-71.92) ...
Selecting previously unselected package linux-headers-4.4.0-71-generic.
Preparing to unpack .../linux-headers-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Unpacking linux-headers-4.4.0-71-generic (4.4.0-71.92) ...
Preparing to unpack .../linux-headers-generic_4.4.0.71.77_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.71.77) over (4.4.0.70.76) ...
Preparing to unpack .../linux-image-4.4.0-70-generic_4.4.0-70.91_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-70-generic (4.4.0-70.91) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-70-generic_4.4.0-70.91_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-70-generic' to '/boot/vmlinuz-4.4.0-70-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-70-generic_4.4.0-70.91_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
myname@MYMACHINE:~$
```

---

### Post by westie457 on 2017-03-31
This is most of your problem. > [COLOR=#000000][FONT=&quot]dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb (--unpack):
[/FONT][/COLOR][COLOR=#000000][FONT=&quot] cannot copy extracted data for './boot/vmlinuz-4.4.0-71-generic' to '/boot/vmlinuz-4.4.0-71-generic.dpkg-new': failed to write (No space left on device)[/FONT][/COLOR]

Post the terminal output, please for ```
df -h
df -i
sudo parted -l
```

---

### Post by DeadlyOats on 2017-03-31
> **westie457 said:**
> This is most of your problem. 

Post the terminal output, please for ```
df -h
df -i
sudo parted -l
```

Here you go.

```
myname@MYMACHINE:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           795M  9.6M  786M   2% /run
/dev/sda6        14G  8.7G  4.3G  68% /
tmpfs           3.9G  3.8M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda5       454M  442M     0 100% /boot
/dev/sda7       330G   77G  237G  25% /home
tmpfs           795M     0  795M   0% /run/user/118
tmpfs           795M   16K  795M   1% /run/user/1000
/dev/sdb1       1.8T  1.6T  140G  92% /media/myname/Takius

```

```
myname@MYMACHINE:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             1011923    644   1011279    1% /dev
tmpfs            1016977    874   1016103    1% /run
/dev/sda6         915712 510188    405524   56% /
tmpfs            1016977      6   1016971    1% /dev/shm
tmpfs            1016977      5   1016972    1% /run/lock
tmpfs            1016977     16   1016961    1% /sys/fs/cgroup
/dev/sda5         122400    343    122057    1% /boot
/dev/sda7       21946368   9452  21936916    1% /home
tmpfs            1016977      4   1016973    1% /run/user/118
tmpfs            1016977     13   1016964    1% /run/user/1000
/dev/sdb1      122101760  26259 122075501    1% /media/myname/Takius

```

```
myname@MYMACHINE:~$ sudo parted -l
[sudo] password for myname: 
Model: ATA JMicron H/W RAID (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   374GB  374GB   primary   ntfs
 3      374GB   749GB  375GB   extended
 5      374GB   375GB  500MB   logical   ext4
 6      375GB   390GB  15.0GB  logical   ext4
 7      390GB   749GB  359GB   logical   ext4
 4      749GB   750GB  1041MB  primary   linux-swap(v1)


Model: Seagate FA GoFlex Desk (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary  ext4



```

---

### Post by westie457 on 2017-04-01
Hello
There are a few approaches to resolve this. They range from safe to very dangerous to the system being fixed.
Being cautious with another person's system I will stick to safe. You will be informed at the time if this is going to get dangerous.,

First, please run```
sudo apt purge [COLOR=#000000][FONT=&quot]linux-headers-4.4.0-31 [/FONT][/COLOR][COLOR=#000000][FONT=&quot]linux-headers-4.4.0-31-generic [/FONT][/COLOR][COLOR=#000000][FONT=&quot]linux-headers-4.4.0-57 [/FONT][/COLOR][COLOR=#000000][FONT=&quot]linux-headers-4.4.0-57-generic
```

If no errors run ```
sudo update-grub
sudo dpkg --configure -a
sudo apt autoremove
sudo apt update-grub #this is a safety belt command, grub should be updated as part of the autoremove operation
```

If there are errors on the first command post them please.[/FONT][/COLOR]

---

### Post by DeadlyOats on 2017-04-01
> **westie457 said:**
> Hello
There are a few approaches to resolve this. They range from safe to very dangerous to the system being fixed.
Being cautious with another person's system I will stick to safe. You will be informed at the time if this is going to get dangerous.,

First, please run```
sudo apt purge [COLOR=#000000][FONT=&quot]linux-headers-4.4.0-31 [/FONT][/COLOR][COLOR=#000000][FONT=&quot]linux-headers-4.4.0-31-generic [/FONT][/COLOR][COLOR=#000000][FONT=&quot]linux-headers-4.4.0-57 [/FONT][/COLOR][COLOR=#000000][FONT=&quot]linux-headers-4.4.0-57-generic
```

If no errors run ```
sudo update-grub
sudo dpkg --configure -a
sudo apt autoremove
sudo apt update-grub #this is a safety belt command, grub should be updated as part of the autoremove operation
```

If there are errors on the first command post them please.[/FONT][/COLOR]

This is what I got.  I don't know if those are errors, but it seems it wants me to do something else.

```
myname@MYMACHINE:~$ sudo apt purge linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic
[sudo] password for myname: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-70-generic : Depends: linux-image-4.4.0-70-generic but it is not going to be installed
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-71-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Impavidus on 2017-04-01
apt often refuses to do anything once it's broken. Try a lower-level approach:```
sudo dpkg -P linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
```That should give some headroom.

---

### Post by westie457 on 2017-04-01
@impavidus Thanks for joining in. 
I was expecting the apt command to fail and was not sure of the syntax for the dpkg command.

---

### Post by DeadlyOats on 2017-04-01
> **Impavidus said:**
> apt often refuses to do anything once it's broken. Try a lower-level approach:```
sudo dpkg -P linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
```That should give some headroom.

This is what I got. It looks like "errors were encountered" according to that last line. Hmmm....

```
myname@MYMACHINE:~$ sudo dpkg -P linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
[sudo] password for myname: 
(Reading database ... 483391 files and directories currently installed.)
Removing linux-headers-4.4.0-31-generic (4.4.0-31.50) ...
Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-31-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-31-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-headers-4.4.0-31 (4.4.0-31.50) ...
Removing linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Purging configuration files for linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-31-generic
```

---

### Post by DeadlyOats on 2017-04-03
So, reviewing what I'd done up to yesterday, I noticed that I did not run the third command in Bucky Ball's first post.  I misunderstood, and thought Bucky Ball wanted me to stop doing the commands as soon as I saw any errors. So, I decided to start from the beginning.  Here's what I got:

```
myname@MYMACHINE:~$ [COLOR="#FF0000"]sudo apt autoremove[/COLOR]
[sudo] password for myname: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-31-generic : Depends: linux-image-4.4.0-31-generic but it is not installed
 linux-image-extra-4.4.0-70-generic : Depends: linux-image-4.4.0-70-generic but it is not installed
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

```
myname@MYMACHINE:~$ [COLOR="#FF0000"]sudo apt update[/COLOR]
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [501 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.2 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [46.9 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [106 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [491 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [94.2 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [54.7 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.2 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [187 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [451 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [437 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [172 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [183 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Fetched 3,608 kB in 3s (975 kB/s)                                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
16 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

```
myname@MYMACHINE:~$ [COLOR="#FF0000"]sudo apt full-upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-31-generic : Depends: linux-image-4.4.0-31-generic but it is not installed
 linux-image-extra-4.4.0-70-generic : Depends: linux-image-4.4.0-70-generic but it is not installed
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

Then I did the command Impavidus suggested.

```
myname@MYMACHINE:~$ [COLOR="#FF0000"]sudo apt -f install[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-65
  linux-headers-4.4.0-65-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-image-4.4.0-57-generic
  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic
  linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic
  linux-image-4.4.0-65-generic linux-image-4.4.0-70-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-65-generic
  linux-image-extra-4.4.0-70-generic snap-confine
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-31-generic linux-image-4.4.0-70-generic
  linux-image-4.4.0-71-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
  linux-headers-4.4.0-31-generic
The following NEW packages will be installed:
  linux-image-4.4.0-31-generic linux-image-4.4.0-70-generic
  linux-image-4.4.0-71-generic
0 upgraded, 3 newly installed, 0 to remove and 16 not upgraded.
19 not fully installed or removed.
Need to get 57.6 MB/101 MB of archives.
After this operation, 188 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-31-generic amd64 4.4.0-31.50 [18.7 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-31-generic amd64 4.4.0-31.50 [38.9 MB]
Fetched 57.6 MB in 43s (1,339 kB/s)                                            
(Reading database ... 451182 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-71-generic (4.4.0-71.92) ...
Selecting previously unselected package linux-image-4.4.0-31-generic.
Preparing to unpack .../linux-image-4.4.0-31-generic_4.4.0-31.50_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Preparing to unpack .../linux-image-4.4.0-70-generic_4.4.0-70.91_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-70-generic (4.4.0-70.91) ...
Setting up eject (2.1.5+deb1+cvs20081104-13.1ubuntu0.16.04.1) ...
Setting up libgstreamer-plugins-base1.0-0:amd64 (1.8.3-1ubuntu0.2) ...
Setting up gstreamer1.0-plugins-base:amd64 (1.8.3-1ubuntu0.2) ...
Setting up libgstreamer-plugins-good1.0-0:amd64 (1.8.3-1ubuntu0.4) ...
Setting up gstreamer1.0-plugins-good:amd64 (1.8.3-1ubuntu0.4) ...
Setting up gstreamer1.0-pulseaudio:amd64 (1.8.3-1ubuntu0.4) ...
Setting up gstreamer1.0-x:amd64 (1.8.3-1ubuntu0.2) ...
Setting up linux-image-4.4.0-71-generic (4.4.0-71.92) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-71-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-71-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-71-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-71-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-71-generic:
 linux-image-extra-4.4.0-71-generic depends on linux-image-4.4.0-71-generic; however:
  Package linux-image-4.4.0-71-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-71-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-71-generic; however:
  Package linux-image-4.4.0-71-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-71-generic; however:
  Package linux-image-extra-4.4.0-71-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-4.4.0-71 (4.4.0-71.92) ...
Setting up linux-headers-4.4.0-71-generic (4.4.0-71.92) ...
Setting up linux-headers-generic (4.4.0.71.77) ...
dpkg: dependency problNo apport report written because the error message indicates its a followup error from a previous failure.
                                                No apport report written because the error message indicates its a followup error from a previous failure.
                                                                          No apport report written because MaxReports is reached already
                                                        ems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.71.77); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-4.4.0-70 (4.4.0-70.91) ...
Setting up linux-headers-4.4.0-70-generic (4.4.0-70.91) ...
Setting up linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-71-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
dpkg: error processing package linux-image-extra-4.4.0-31-generic (--configure):
 package linux-image-extra-4.4.0-31-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up linux-image-extra-4.4.0-67-generic (4.4.0-67.88) ...
No apport report written because MaxReports is reached already
                                                              run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-67-generic /boot/vmlinuz-4.4.0-67-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-67-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-67-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-67-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-4.4.0-70-generic (4.4.0-70.91) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-70-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-70-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-70-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-70-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-70-generic:
 linux-image-extra-4.4.0-70-generic depends on linux-image-4.4.0-70-generic; however:
  Package linux-image-4.4.0-70-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-70-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-libc-dev:amd64 (4.4.0-70.91) ...
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu7) ...
Errors were encountered while processing:
 linux-image-4.4.0-71-generic
 linux-image-extra-4.4.0-71-generic
 linux-image-generic
 linux-generic
 linux-image-extra-4.4.0-31-generic
 linux-image-extra-4.4.0-67-generic
 linux-image-4.4.0-70-generic
 linux-image-extra-4.4.0-70-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I got a message that "A Restart Is Needed."  So, now I'm going to "Restart" and see what happens.

---

### Post by DeadlyOats on 2017-04-03
Results...  I completely broke it.  Grub still works.  I'm logged in Win7 now, to make this post.

I'm getting a kernel panic and it says that it can't mount fs on block something or other 0,0 and a whole lot more stuff....  I'm just gonna do a complete re-install.  *sigh*

Thanks, everyone, for taking the time to help me with my issue.  I guess, I should have just waited until Monday to see what one of you's would have said next.  Oh, well.  At least I didn't lose any important files.... yet....

UPDATE:

So, I re-installed Kubuntu 16.04.01 (successfully preserved my /home directory, so my files and settings were preserved.  Next, I went about running Update Manager, to install all of the updates...  I'm back where I started from.....  The updates won't install, same error message as before.

This is nuts....  So, what exactly is the problem that I'm running into, here?

---

### Post by Bucky Ball on 2017-04-03
I think I see what *might* be causing a problem, or at least a way of getting around the issue you're having. Try this. 

[Download 16.04.**2** from here]("https://kubuntu.org/getkubuntu/") (underneath 16.10). You are installing 16.04.**1** and perhaps that is causing an issue. Perhaps it's not, but that's what I'd be trying.

If you go directly for 16.04.2 then you are as recent with 16.04 as you can get so you would already have the kernel 16.04.1 is trying to upgrade itself to, if you follow my thinking. :-k

Suggest you leave 'Third-party drivers' and 'update while installing' unticked if Kubuntu has those options during install.

---

### Post by Impavidus on 2017-04-03
Yesterday I was wondering why update-initramfs tried to regenerate /boot/initrd.img-4.4.0-31-generic when you were uninstalling kernel 4.4.0-31. It should just remove that file. But now I see there was only a problem uninstalling linux-image-extra-4.4.0-31-generic. linux-image-4.4.0-31-generic was uninstalled succesfully and that removed /boot/initrd.img-4.4.0-31-generic. Next it should be possible to uninstall linux-image-extra-4.4.0-31-generic and get enough headroom to uninstall the other old kernels.

What is your current status?

---

### Post by DeadlyOats on 2017-04-03
> **Impavidus said:**
> Yesterday I was wondering why update-initramfs tried to regenerate /boot/initrd.img-4.4.0-31-generic when you were uninstalling kernel 4.4.0-31. It should just remove that file. But now I see there was only a problem uninstalling linux-image-extra-4.4.0-31-generic. linux-image-4.4.0-31-generic was uninstalled succesfully and that removed /boot/initrd.img-4.4.0-31-generic. Next it should be possible to uninstall linux-image-extra-4.4.0-31-generic and get enough headroom to uninstall the other old kernels.

What is your current status?

I re-installed using Kubuntu 16.04.1 (64 bit) DVD.  I downloaded 16.04.2, and am about to burn it onto a DVD.  The reinstall of 16.04.1 has put me right back at the beginning. I'm unable to install updates and am getting the same error message as I described in the beginning.

Do you want me to run some code to see what it looks like? (If so, what code do I need to run to display what's happening?)

---

### Post by mus1cfreak on 2017-04-03
> **DeadlyOats said:**
> I re-installed using Kubuntu 16.04.1 (64 bit) DVD.  I downloaded 16.04.2, and am about to burn it onto a DVD.  The reinstall of 16.04.1 has put me right back at the beginning. I'm unable to install updates and am getting the same error message as I described in the beginning.

Do you want me to run some code to see what it looks like? (If so, what code do I need to run to display what's happening?)

It looks like you are using a incorrect sources.list

A you are living in Western US, i have created a sources.list from: [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

login as root
gedit /etc/apt/sources.list
remove all text
copy and paste the text below into the file and save it.

perform a apt-get update && apt-get dist-upgrade in aterminal, as user root.

```
#------------------------------------------------------------------------------##                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#




###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse 


###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse 


#------------------------------------------------------------------------------#
#                           UNOFFICIAL UBUNTU REPOS                            #
#------------------------------------------------------------------------------#




###### 3rd Party Binary Repos



```

---

### Post by DeadlyOats on 2017-04-03
Well!  The problem was solved with Bucky Ball's solution to re-install using version 16.04.2.  After the installation, the updates downloaded and installed without issue.  I'm really grateful for the advice, everyone.  Thanks for looking at my issue and giving me advice.

The only thing I guess I'm kind of dissatisfied with, is that I don't know what caused the problem in the first place.  This is how I used to solve Win95/2000/XP problems, fresh installs...  Based on all of the data, posted above, can anyone say what the problem was?

---

### Post by westie457 on 2017-04-03
The main part of the problem was caused by the very small (by today's standards) /boot partition. A separate boot partition is a default component of setting up a system with LVM and or encryption of the root partition.
A contributing factor to the issue is the way the size of the kernel has grown over time to cope with the increase in the amount of available hardware that need driver support built-in and the security updates to help protect your system and data.
Don't take this personally, you are not the first person and definitely not the last to suffer with this issue of a full partition.
Please in future after an update to a new kernel run 'sudo apt autoremove' to keep free space available for the next kernel update, also if you use a /boot partition make it a bit bigger.

By doing the reinstall when you did you stopped me from using the terminal equivalent of a sledge-hammer (read dangerous) to create the necessary space for a clean resolution of the problem.
We were about to break package-management of the system then force package-management to repair itself. One mistake here would mean a clean fresh installation and an instruction to back-up your personal data before continuing.

Personal note from me. I have no qualms about using the dangerous approach on my own computer however I am more cautious when helping others.

Regards Westie457

---

### Post by DeadlyOats on 2017-04-03
> **westie457 said:**
> The main part of the problem was caused by the very small (by today's standards) /boot partition. A separate boot partition is a default component of setting up a system with LVM and or encryption of the root partition.
A contributing factor to the issue is the way the size of the kernel has grown over time to cope with the increase in the amount of available hardware that need driver support built-in and the security updates to help protect your system and data.
Don't take this personally, you are not the first person and definitely not the last to suffer with this issue of a full partition.
[COLOR="#FF0000"]Please in future after an update to a new kernel run 'sudo apt autoremove' to keep free space available for the next kernel update, also if you use a /boot partition make it a bit bigger.[/COLOR]

By doing the reinstall when you did you stopped me from using the terminal equivalent of a sledge-hammer (read dangerous) to create the necessary space for a clean resolution of the problem.
We were about to break package-management of the system then force package-management to repair itself. One mistake here would mean a clean fresh installation and an instruction to back-up your personal data before continuing.

Personal note from me. I have no qualms about using the dangerous approach on my own computer however I am more cautious when helping others.

Regards Westie457

Increase the size of /boot and from time to time, run 'sudo apt autoremove' *_after_* an update that includes a kernel update.

Thanks for the info.  At least now understand why I started to have trouble.

Thanks again to everyone who chipped in to help, and to Bucky Ball, for the "easy work around fix."

---

### Post by Bucky Ball on 2017-04-03
Glad it all worked out. Good luck and enjoy. :)

---

### Post by Impavidus on 2017-04-04
Glad you solved it.

You're not the first and definitely not the last to have this problem. This is one of the cases where preventing a problem is much better than solving it. So make sure you uninstall those old kernels before you run out of space.

---

