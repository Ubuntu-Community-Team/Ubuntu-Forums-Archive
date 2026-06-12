---
title: "Boot fails and unable to repair it"
date: 2013-02-09
forum: General Help
---

### Post by FonkyM on 2013-02-09
Hi guys,

I'm hoping that you can help me out with this.

A few days ago I had a problem with some upgrade install which ended up  messing things up quite bad. I ended up having a problem getting a  message telling me that my disk was full while I new I still had some  space. Realized that it was due to having my inodes full. And after  trying to clean up to have some space I must have done something wrong  as after that I have been unable to boot.

Got my hand on a Live USB and after a bit of googling understood that I  had to repair Grub in order to have my system booting normally. Seemed  that I had to options to do that:
- using boot-repair
- chrooting to install Grub 2 (as explained here [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099))

When using boot-repair after trying to repair by just clicking on the  recommended repair, it ends up telling me that the repair failed.

Here is the output:
[http://paste.ubuntu.com/1630064/](http://paste.ubuntu.com/1630064/)

I noticed this which may explain what went wrong:
[PHP] =================== os-prober: /dev/sda6:Ubuntu 12.04.2 LTS (12.04):Ubuntu:linux  =================== blkid: /dev/loop0: TYPE="squashfs" /dev/sda1: UUID="a36bf37c-8f72-4055-92c4-5fd86c4c5c59" TYPE="ext2" /dev/sda5: UUID="1f96528e-03cc-4121-bec1-4cbdb8ac005c" TYPE="swap" /dev/sda6: UUID="3b2e8ea1-18bf-41ad-8417-2652ea656ca7" TYPE="ext4" /dev/sda7: UUID="fe8237ae-f0fe-4c2d-8f64-1e7e88526db8" TYPE="ext4" /dev/sdb1: LABEL="PENDRIVE" UUID="1CF1-2B37" TYPE="vfat"   1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.  Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently. =================== No kernel in /mnt/boot-sav/sda1/boot: grub    =================== sda1recordfail=1/grub/grubenv : recordfail=1 [/PHP]

And the recommended repairs:
[PHP] =================== Recommended repair Recommended-Repair This setting will reinstall the grub2 of sda6 into the MBR of sda, using the following options:        sda1/boot, Additional repair will be performed: unhide-bootmenu-10s   Mount sda1 on /mnt/boot-sav/sda6/boot chroot: failed to run command `grub-install': No such file or directory ,.  Reinstall the GRUB of sda6 into the MBR of sda chroot: failed to run command `grub-install': No such file or directory grub-install /dev/sda: exit code of grub-install /dev/sda:127 Failed to run command grub-install detected. chroot: failed to run command `type': No such file or directory lrwxrwxrwx 1 root root 32 Jan 22 19:19 /mnt/boot-sav/sda6/usr/sbin/grub-install -> ../lib/grub/i386-pc/grub-install lrwxrwxrwx 1 root root 32 Jan 22 19:19 /mnt/boot-sav/sda6/usr/sbin/grub-install -> ../lib/grub/i386-pc/grub-install chroot: failed to run command `grub-install': No such file or directory grub-install /dev/sda: exit code of grub-install /dev/sda:127  chroot /mnt/boot-sav/sda6 update-grub chroot: failed to run command `update-grub': No such file or directory  An error occurred during the repair.  You can now reboot your computer.  pastebinit  packages needed dpkg-preconfigure: unable to re-open stdin: No such file or directory [/PHP]

I have also tried to use boot-repair by using the advanced settings but I always end up getting in a loop telling me:
> Please enable a repository containing the [linux] packages in the software sources of The OS now in use - Ubuntu 12.04 (sda6). Then try again
and
> Please enable a repository containing the [grub2] packages in the software sources of The OS now in use - Ubuntu 12.04 (sda6). Then try again
And it always comes back to these message whatever the repository I choose.


When trying the Chrooting method I manage to mount the partitions and  the Ubuntu installations on /mnt/temp correctly but when I type the  command ```
sudo chroot /mnt/temp
```
I get the following message telling me that it fails.
```
 chroot: failed to run command `/bin/bash': No such file or directory 
```

I'm feeling stuck now and don't know how to resolve my problem. I  already backed up all my files but would really prefer to avoid having  to do an fresh install :-/

---

### Post by dabl on 2013-02-09
Take a look at this and see if you followed all the steps -- it looks like you didn't on the final step:  [http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html](http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html)

---

### Post by FonkyM on 2013-02-09
> **dabl said:**
> Take a look at this and see if you followed all the steps -- it looks like you didn't on the final step:  [http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html](http://basictheprogram.blogspot.com/2011/02/how-to-chroot-simple-and-fast-archive.html)

Tried the command as suggested in the link but even the first one gives me an error

> ubuntu@ubuntu:~$ sudo mkdir /mount/point
mkdir: cannot create directory `/mount/point': No such file or directory

:confused:

---

### Post by dabl on 2013-02-09
Try it like this:

```
sudo mkdir -p /mnt/chroot
```

---

### Post by oldfred on 2013-02-10
I think the link leaves off the extra command to mount your separate /boot and you need to use /mnt not /mount as dabl has already suggested.

Not sure why Boot-Repair did not work? Do you have any settings in BIOS that lock MBR? Virus protection or bit locker built into BIOS?

You might try these before the full chroot. We suggest these first and then if they do not work the full chroot method.
       #If separate /boot
$ sudo mount /dev/sda6 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

OR

#If separate /boot & Natty or later
$ sudo mount /dev/sda6 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ sudo grub-install --boot-directory=/mnt/boot /dev/sda

Newer version of grub2 suggest the --boot-directory but the older --root-directory type still seems to work. 

       Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by FonkyM on 2013-02-10
Ok so I managed to solve my chroot issue and can now chroot from terminal.

But I still have a problem at the next step as running the command apt-get purge grub grub-pc grub-common tells me I have unmet dependencies and can't solve it to purge grub.

Here is the output:

> root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
Package grub-common is not installed, so not removed
Package grub-pc is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apt-utils : Depends: libapt-inst1.4 (>= 0.8.0) but it is not going to be installed
             Depends: libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10.7) but it is not going to be installed
             Depends: libc6 (>= 2.4) but it is not going to be installed
             Depends: libdb5.1 but it is not going to be installed
             Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
             Depends: libstdc++6 (>= 4.4.0) but it is not going to be installed
 debconf-i18n : Depends: debconf but it is not going to be installed
                Depends: liblocale-gettext-perl but it is not going to be installed
 libtext-charwidth-perl : Depends: libc6 (>= 2.1.3) but it is not going to be installed
                          Depends: perl-base (>= 5.14.2-3) but it is not going to be installed
                          Depends: perlapi-5.14.2
 libtext-iconv-perl : Depends: libc6 (>= 2.1.3) but it is not going to be installed
                      Depends: perl-base (>= 5.14.2-6) but it is not going to be installed
                      Depends: perlapi-5.14.2
 multiarch-support : Depends: libc6 (>= 2.13-0ubuntu6) but it is not going to be installed
 tzdata : Depends: debconf (>= 0.5) but it is not going to be installed or
                   debconf-2.0
 xz-utils : Depends: libc6 (>= 2.7) but it is not going to be installed
            Depends: liblzma5 (>= 5.1.1alpha+20110809) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).and when I run apt-get -f install

> root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  coreutils debconf dpkg libacl1 libapt-inst1.4 libapt-pkg4.12 libattr1
  libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1
  libstdc++6 perl-base tar zlib1g
Suggested packages:
  debconf-doc debconf-utils whiptail dialog gnome-utils
  libterm-readline-gnu-perl libgtk2-perl libnet-ldap-perl libqtgui4-perl
  libqtcore4-perl apt bzip2 ncompress
The following NEW packages will be installed:
  coreutils debconf dpkg libacl1 libapt-inst1.4 libapt-pkg4.12 libattr1
  libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1
  libstdc++6 perl-base tar zlib1g
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 3,941 kB/12.2 MB of archives.
After this operation, 25.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise-proposed/main libc6 i386 2.15-0ubuntu10.4 [3,941 kB]
Fetched 3,941 kB in 37s (105 kB/s)                                             
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
Selecting previously unselected package libc6.
(Reading database ... 2338 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.4 (using .../libc6_2.15-0ubuntu10.4_i386.deb) ...

A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/libc-2.15.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
/bin/df: `/run/lock': No such file or directory
                                               /bin/df: `/run/shm': No such file or directory
             /bin/df: `/home/emmanuel/.gvfs': No such file or directory
                                                                       dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_i386.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_i386.deb (--unpack):
 pre-dependency problem - not installing libgcc1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb
 /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oldfred on 2013-02-10
You have a partial upgrade and now it is very confused.

If you do not yet have a good backup I would make sure you do. All your data and all of /home at the minimum.

List sources and are they consistent?
 cat /etc/apt/sources.list

       # If still errors after fixing sources
# Repair sources issues, delete old/obsolete & refresh:
[http://ubuntuforums.org/showthread.php?t=2037992](http://ubuntuforums.org/showthread.php?t=2037992)
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

   # Then this one:
sudo apt-get update && sudo apt-get dist-upgrade

    
[http://ubuntuforums.org/showthread.php?t=1858451](http://ubuntuforums.org/showthread.php?t=1858451)
Update another link
[http://ubuntuforums.org/showthread.php?t=1978554](http://ubuntuforums.org/showthread.php?t=1978554)

---

### Post by FonkyM on 2013-02-10
So this is what I get for the sources list

```
root@ubuntu:/# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://be.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://be.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://be.archive.ubuntu.com/ubuntu/ precise universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://be.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ precise multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

#==================================
# Paissad Repository (pms-linux)  =
#==================================
# deb http://deb.paissad.net/ unstable main contrib non-free # disabled on upgrade to oneiric
# deb-src http://deb.paissad.net/ unstable main contrib # disabled on upgrade to oneiric

#=============
# mediainfo  =
#=============
# deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu oneiric main # disabled on upgrade to oneiric
deb http://be.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe
```

And after the suggested commands to refresh, I get this as the last part after it checks the different sources

```
Fetched 316 B in 6s (47 B/s)                                                                             
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EA8F35793D8809A
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 apt-utils : Depends: libapt-inst1.4 (>= 0.8.0) but it is not installed
             Depends: libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10.7) but it is not installed
             Depends: libdb5.1 but it is not installed
             Depends: libgcc1 (>= 1:4.1.1) but it is not installed
             Depends: libstdc++6 (>= 4.4.0) but it is not installed
 debconf-i18n : Depends: debconf but it is not installed
                Depends: liblocale-gettext-perl but it is not installed
 libc6 : Depends: libgcc1 but it is not installed
 libtext-charwidth-perl : Depends: perl-base (>= 5.14.2-3) but it is not installed
                          Depends: perlapi-5.14.2
 libtext-iconv-perl : Depends: perl-base (>= 5.14.2-6) but it is not installed
                      Depends: perlapi-5.14.2
 tzdata : Depends: debconf (>= 0.5) but it is not installed or
                   debconf-2.0
 xz-utils : Depends: liblzma5 (>= 5.1.1alpha+20110809) but it is not installed
E: Unmet dependencies. Try using -f.
```

I've already made a backup and have all my important files saved on an external drive, that was the first thing I did after having managed to boot via a LiveUSB.

---

### Post by oldfred on 2013-02-10
It looks like everything is precise and ppa's are all commented out.

Another thread with some suggestions.
[http://ubuntuforums.org/showthread.php?t=1983220](http://ubuntuforums.org/showthread.php?t=1983220)

See post #5 also on adding keys
[http://ubuntuforums.org/showthread.php?t=2062472](http://ubuntuforums.org/showthread.php?t=2062472)

---

### Post by FonkyM on 2013-02-10
Managed to add the missing key, thanks ;)

But I'm still stuck with the missing dependencies problem. Basically any other command than apt-get update pretty much comes back with the following:

```
root@funkymaestro-1000H:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 apt-utils : Depends: libapt-inst1.4 (>= 0.8.0) but it is not installed
             Depends: libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10.7) but it is not installed
             Depends: libdb5.1 but it is not installed
             Depends: libgcc1 (>= 1:4.1.1) but it is not installed
             Depends: libstdc++6 (>= 4.4.0) but it is not installed
 debconf-i18n : Depends: debconf but it is not installed
                Depends: liblocale-gettext-perl but it is not installed
 libc6 : Depends: libgcc1 but it is not installed
 libtext-charwidth-perl : Depends: perl-base (>= 5.14.2-3) but it is not installed
                          Depends: perlapi-5.14.2
 libtext-iconv-perl : Depends: perl-base (>= 5.14.2-6) but it is not installed
                      Depends: perlapi-5.14.2
 tzdata : Depends: debconf (>= 0.5) but it is not installed or
                   debconf-2.0
 xz-utils : Depends: liblzma5 (>= 5.1.1alpha+20110809) but it is not installed
E: Unmet dependencies. Try using -f.
```


Btw, instead of having to chroot each time and because the LiveUSB I was using wasn't persistent and didn't have that much memory, I'm now using Suber Grub 2 ([http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) ). Guess it's not changing much.

---

### Post by oldfred on 2013-02-10
Did you rebuild cache as in first link. And then run the:

apt-get -f install

---

### Post by FonkyM on 2013-02-11
> **oldfred said:**
> Did you rebuild cache as in first link. And then run the:

apt-get -f install

Yes, did everything as explained but even after rebuilding the cache I get stuck again.

Forcing install doesn't manage to fix it either.

```
root@funkymaestro-1000H:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  coreutils debconf dpkg libacl1 libapt-inst1.4 libapt-pkg4.12 libattr1
  libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1
  libstdc++6 perl-base tar zlib1g
Suggested packages:
  debconf-doc debconf-utils whiptail dialog gnome-utils
  libterm-readline-gnu-perl libgtk2-perl libnet-ldap-perl libqtgui4-perl
  libqtcore4-perl apt bzip2 ncompress
The following NEW packages will be installed:
  coreutils debconf dpkg libacl1 libapt-inst1.4 libapt-pkg4.12 libattr1
  libbz2-1.0 libdb5.1 libgcc1 liblocale-gettext-perl liblzma5 libselinux1
  libstdc++6 perl-base tar zlib1g
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/12.2 MB of archives.
After this operation, 25.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
(Reading database ... 2338 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.4 (using .../libc6_2.15-0ubuntu10.4_i386.deb) ...

A copy of the C library was found in an unexpected directory:
  '/lib/i386-linux-gnu/libc-2.15.so'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/i386-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_i386.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_i386.deb (--unpack):
 pre-dependency problem - not installing libgcc1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb
 /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by oldfred on 2013-02-11
I do not know what else to suggest. You can try what each of the error reports suggests, but each may not work.

I have always preferred clean installs after years of doing upgrades. I never had this much touble but usually had video issues and some others. Clean install also housecleans system. But good backups are important and separate /data makes a new install while still using old install a good option.

---

