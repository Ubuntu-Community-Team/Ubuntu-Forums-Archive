---
title: "Problem With Updating"
date: 2007-03-05
forum: General Help
---

### Post by Aikon- on 2007-03-05
Okay.. Here's where we stand: I had gotten rather lax in keeping my system up to date, mainly because for me, a kernel upgrade means having to do some finicky stuff (grub recognizes my hard drives differently than linux does). I finally decided to do it, so I started with all the non-kernel upgrades first. Samba failed. I don't have the original error message anymore, but I think the message I'll include below has the necessary information.

After fiddling with it for a while, I decided it might have something to do with the kernel, so I decided to upgrade that too. I was 2 or 3 releases behind on the kernel. When I ```
sudo apt-get upgrade
```, it says I should try ```
sudo apt-get -f install
``` to fix dependencies; if I do, this is what resutls:

```
sarmitage@OPHELIA:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.15-28-386: Depends: linux-image-2.6.15-28-386 but it is not installed
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.
sarmitage@OPHELIA:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.15-28-386 samba
Suggested packages:
  linux-doc-2.6.15 linux-source-2.6.15
Recommended packages:
  lilo smbldap-tools
The following NEW packages will be installed:
  linux-image-2.6.15-28-386
The following packages will be upgraded:
  samba
1 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 0B/24.5MB of archives.
After unpacking, 62.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 107556 files and directories currently installed.)
Unpacking linux-image-2.6.15-28-386 (from .../linux-image-2.6.15-28-386_2.6.15-28.51_i386.deb) ...
The directory /lib/modules/2.6.15-28-386 still exists. Continuing as directed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-28-386_2.6.15-28.51_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Cannot delete /boot/initrd.img-2.6.15-28-386, doesn't exist.
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.15-28-386_2.6.15-28.51_i386.deb
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
sarmitage@OPHELIA:~$

```

Its late here, and my brain is mostly made of putty after futsing with Crystal Reports and SQL Server all day =/ Any help would be greatly appreciated; let me know if you want me to run any commands to view the output or whatever.

p.s. Its not critical, because I don't use Samba, and my install is currently working fine with the (I believe) current version of the Linux kernel, but until I get this fixed I won't be able to install any more updates.

-Scott

---

### Post by Aikon- on 2007-03-06
=D

/bump

---

### Post by Aikon- on 2007-03-06
Okay I tried some of the ideas from [http://www.ubuntuforums.org/showthread.php?t=372744](http://www.ubuntuforums.org/showthread.php?t=372744) :

After stopping samba (using $sudo /etc/init.d/samba stop), i ran the command below and got something about read-only file system (though I don't think ANY of my ext3 volumes are set to read-only..)

```
sarmitage@OPHELIA:~$ sudo aptitude clean && sudo aptitude autoclean && sudo aptitude install samba
E: /root/.aptitude/config - Unable to open %s for writing (30 Read-only file system)
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: /root/.aptitude/config - Unable to open %s for writing (30 Read-only file system)
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Freed 0B of disk space
E: /root/.aptitude/config - Unable to open %s for writing (30 Read-only file system)
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  linux-restricted-modules-2.6.15-28-386
The following packages have been kept back:
  build-essential dpkg-dev fakeroot g++ libc6-dev linux-386
  linux-image-2.6.15-27-386 linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
The following packages will be upgraded:
  samba
1 packages upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
Need to get 2845kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.15-28-386: Depends: linux-image-2.6.15-28-386 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
linux-image-2.6.15-28-386 [2.6.15-28.51 (dapper-security)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  linux-image-2.6.15-28-386
The following packages have been kept back:
  build-essential dpkg-dev fakeroot g++ libc6-dev linux-386
  linux-image-2.6.15-27-386 linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
The following NEW packages will be installed:
  linux-image-2.6.15-28-386
The following packages will be upgraded:
  samba
1 packages upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 24.5MB of archives. After unpacking 62.3MB will be used.
Do you want to continue? [Y/n/?] y
Err http://security.ubuntu.com dapper-security/main linux-image-2.6.15-28-386 2.6.15-28.51
  Could not open file /var/cache/apt/archives/partial/linux-image-2.6.15-28-386_2.6.15-28.51_i386.deb - open (30 Read-only file system)
Err http://security.ubuntu.com dapper-security/main samba 3.0.22-1ubuntu3.2
  Could not open file /var/cache/apt/archives/partial/samba_3.0.22-1ubuntu3.2_i386.deb - open (30 Read-only file system)
W: Not using locking for read only lock file /var/lib/apt/lists/lock
E: Unable to correct for unavailable packages

```

---

### Post by Aikon- on 2007-03-06
Update: it seems I had some issues with my disk.. I ran fsck in recover-mode on my system volume and it found a whole slew of problems (which I dutifully hit "Y" to for each to have it fixed). When I booted up after that and ran $sudo aptitude install samba, it started downloading the packaged instead of using some saved one.

So it looks like my debs may have been corrupt.. after I fix this samba thing I will try to fix the kernel thing and hopefull all will be good now.

---

### Post by Aikon- on 2007-03-06
Well my kernel install went well, so now all that's left is Samba, which is still causing issues. I think the important line in the error message is as follows:

[/code]invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba[/code]

Can I just delete the symlink do you think? I'm not too sure I understand what a "dangling symlink" is, or what this particular one is used for..

---

