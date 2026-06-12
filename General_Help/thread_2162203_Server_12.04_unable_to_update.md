---
title: "Server 12.04 unable to update"
date: 2013-07-13
forum: General Help
---

### Post by chaosadnd1 on 2013-07-13
Hi all,

Below is the error I am getting when attempting to do any kind of update:


[LIST]
dpkg: dependency problems prevent configuration of linux-image-generic-pae: linux-image-generic-pae depends on linux-image-3.2.0-45-generic-pae; however:  Package linux-image-3.2.0-45-generic-pae is not installed.dpkg: error processing linux-image-generic-pae (--configure): dependency problems - leaving unconfiguredSetting up linux-headers-3.2.0-49 (3.2.0-49.75) ...dpkg: dependency problems prevent configuration of linux-generic-pae: linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.45.54); however:  Package linux-image-generic-pae is not configured yet. linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.45.54); however:  Version of linux-headers-generic-pae on system is 3.2.0.49.59.dpkg: error processing linux-generic-pae (--configure): dependency problems - leaving unconfiguredSetting up linux-headers-3.2.0-49-generic-pae (3.2.0-49.75) ...Setting up linux-headers-generic-pae (3.2.0.49.59) ...Errors were encountered while processing: linux-image-generic-pae linux-generic-paeReading package lists...Building dependency tree...Reading state information...You might want to run 'apt-get -f install' to correct these:The following packages have unmet dependencies: apport : Depends: python-apport (>= 2.0.1-0ubuntu17.3) but 2.0.1-0ubuntu17.2 is to be installed linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.45.54) but 3.2.0.49.59 is to be installed linux-image-generic-pae : Depends: linux-image-3.2.0-45-generic-pae but it is not going to be installedE: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[B].. install failed!

I've tried to sudo-apt-get autoclean and clean but it doesnt seem to remove the weird kernel. I'm kind of at a loss. Any help would be appreciated.[/B]
[/LIST]

---

### Post by TheFu on 2013-07-13
Tried '**apt-get -f install**' with no packages?  What was the result?


Also, thanks very much for copy/pasting everything, but if you used "code" as the format type, all the LF and spacing would have been retained - much easier to read.

---

### Post by uRock on 2013-07-13
> **chaosadnd1 said:**
> Hi all,

Below is the error I am getting when attempting to do any kind of update:


```

dpkg: dependency problems prevent configuration of linux-image-generic-pae: linux-image-generic-pae depends on linux-image-3.2.0-45-generic-pae; however:  Package linux-image-3.2.0-45-generic-pae is not installed.dpkg: error processing linux-image-generic-pae (--configure): dependency problems - leaving unconfiguredSetting up linux-headers-3.2.0-49 (3.2.0-49.75) ...dpkg: dependency problems prevent configuration of linux-generic-pae: linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.45.54); however:  Package linux-image-generic-pae is not configured yet. linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.45.54); however:  Version of linux-headers-generic-pae on system is 3.2.0.49.59.dpkg: error processing linux-generic-pae (--configure): dependency problems - leaving unconfiguredSetting up linux-headers-3.2.0-49-generic-pae (3.2.0-49.75) ...Setting up linux-headers-generic-pae (3.2.0.49.59) ...Errors were encountered while processing: linux-image-generic-pae linux-generic-paeReading package lists...Building dependency tree...Reading state information...You might want to run '**apt-get -f install**' to correct these:The following packages have unmet dependencies: apport : Depends: python-apport (>= 2.0.1-0ubuntu17.3) but 2.0.1-0ubuntu17.2 is to be installed linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.45.54) but 3.2.0.49.59 is to be installed linux-image-generic-pae : Depends: linux-image-3.2.0-45-generic-pae but it is not going to be installedE: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[B].. install failed!

I've tried to sudo-apt-get autoclean and clean but it doesnt seem to remove the weird kernel. I'm kind of at a loss. Any help would be appreciated.[/B]

```

Have you run ```
sudo apt-get -f install
```

PS, Please use code tags, instead of list tags. Highlight the code text then click the # button in the toolbar.

---

### Post by chaosadnd1 on 2013-07-16
Sorry about the formatting. And the late reply. yes I have tried -f install, it still screams unmet dependencies.

---

### Post by Bashing-om on 2013-07-16
chaosadnd1; Hi !

See if this (un)confuses the operating system as to the kernels:
```

sudo dpkg --remove linux-generic-pae
sudo apt-get install linux-generic-pae

```
Removing linux-generic will do no harm at all. It is only a "meta-package" depending on linux-image-generic and linux-headers-generic. Those two are themselves meta-packages depending on the respective latest image/headers packages.

You can see this for yourself by issuing apt-cache show linux-generic, apt-cache show linux-image-generic and apt-cache show linux-headers-generic.

The purpose of meta-packages is to pull-in the packages on which they depend, they have no functionality at all. On the other hand removing one will not remove it's dependencies - so no danger to the system.

After having fixed the original issue you can of course install linux-generic again.

And carry on.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by chaosadnd1 on 2013-07-19
```
nate@winterfell:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
linux-headers-3.2.0-40 linux-headers-3.2.0-40-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
linux-image-3.2.0-49-generic-pae linux-image-generic-pae
Suggested packages:
fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
linux-image-3.2.0-49-generic-pae
The following packages will be upgraded:
linux-image-generic-pae
1 upgraded, 1 newly installed, 0 to remove and 79 not upgraded.
1 not fully installed or removed.
Need to get 0 B/38.3 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 377742 files and directories currently installed.)
Unpacking linux-image-3.2.0-49-generic-pae (from .../linux-image-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb (--unpack):
failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-49-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
Errors were encountered while processing:
/var/cache/apt/archives/linux-image-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Here are the results of -f install.

---

### Post by TheFu on 2013-07-20
Did you read the output above?
[I]No space left on device
[/I]
Tells me everything.  The partition is out of space. Correct that error first.

---

### Post by chaosadnd1 on 2013-07-20
Oh, yes I see that now. Now to figure out how to clean up /boot..

---

### Post by TheFu on 2013-07-20
> **chaosadnd1 said:**
> Oh, yes I see that now. Now to figure out how to clean up /boot..

This is a frustration that I've had the last year.  I don't remember having to clean up old kernels until the 12.04 release. It would be nice if we could set a number of old kernels to retain ... perhaps 4 .... and have all the older ones automatically removed.

I got lazy and wrote a script to generate an apt-get command that includes all the kernels, except the current one. Here's the blog article with the script. I hope it is useful to someone.  I didn't think it was a good idea to remove anything automatically. It wouldn't take much to make that happen, if that was your desire. ;)

---

### Post by JnPson on 2013-08-05
Hi. I use Ubuntu 12.04.2 LTS and I'm having the same problem when I try to update. The problem is that I can't figure out what device it is that is full or have no space left. I
I do 
```
apt-get update && apt-get dist-upgrade -y
``` 

ending with 

```
Hit http://se.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://se.archive.ubuntu.com precise-backports/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.
``` 

So I run *apt-get -f install*
```
root@dc01:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.5.0-37-generic
The following NEW packages will be installed:
  linux-headers-3.5.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
4 not fully installed or removed.
Need to get 0 B/945 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en_US:en",
    LC_ALL = (unset),
    LC_TIME = "sv_SE.UTF-8",
    LC_MONETARY = "sv_SE.UTF-8",
    LC_ADDRESS = "sv_SE.UTF-8",
    LC_TELEPHONE = "sv_SE.UTF-8",
    LC_NAME = "sv_SE.UTF-8",
    LC_MEASUREMENT = "sv_SE.UTF-8",
    LC_IDENTIFICATION = "sv_SE.UTF-8",
    LC_NUMERIC = "sv_SE.UTF-8",
    LC_PAPER = "sv_SE.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 133211 files and directories currently installed.)
Unpacking linux-headers-3.5.0-37-generic (from .../linux-headers-3.5.0-37-generic_3.5.0-37.58~precise1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-37-generic_3.5.0-37.58~precise1_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.5.0-37-generic/include/config/nfs/v4/1/implementation': **No space left on device**
No apport report written because the error message indicates a **disk full error**
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.5.0-37-generic_3.5.0-37.58~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I do a df -h and it shows that the disks are not full. 
```
root@dc01:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  1.9G  581M  1.2G  33% /
udev                  494M  4.0K  494M   1% /dev
tmpfs                 201M  324K  201M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  502M     0  502M   0% /run/shm
/dev/mapper/LVG-tmp   461M   11M  427M   3% /tmp
/dev/mapper/LVG-bak   461M   11M  427M   3% /bak
/dev/sda1             268M   82M  172M  33% /boot
/dev/mapper/LVG-home  183M   19M  155M  11% /home
/dev/mapper/LVG-opt   183M  5.6M  168M   4% /opt
/dev/mapper/LVG-srv   183M  5.6M  168M   4% /srv
/dev/mapper/LVG-usr   1.9G  1.1G  686M  62% /usr
/dev/mapper/LVG-var   1.9G  430M  1.4G  25% /var


```
I'm having the same problem on one of my servers at home and I followed previous advices that ended up with the server not booting. To get it booting again I had to use an older linux-kernel.
I'm greatful for any help

---

### Post by TheFu on 2013-08-05
There is 2 sorts of space on a disk. Sectors and inodes. 
$ df -h ----- shows sectors available/used.
$ **df -i** ----- shows inodes.  Run that to see if you are out of inodes.  On smaller allocations (less than 8G) with lots of tiny files, running out of inodes happens too often.  So, when you run that, are you out of inodes?

---

### Post by JnPson on 2013-08-05
I don't know, I still don't see what disk is full.
```
root@dc01:~# df -i
Filesystem           Inodes  IUsed  IFree IUse% Mounted on
/dev/mapper/LVG-root 121920  21689 100231   18% /
udev                 126317    528 125789    1% /dev
tmpfs                128370    464 127906    1% /run
none                 128370      4 128366    1% /run/lock
none                 128370      1 128369    1% /run/shm
/dev/mapper/LVG-tmp  121920     11 121909    1% /tmp
/dev/mapper/LVG-bak  121920     11 121909    1% /bak
/dev/sda1            146016    244 145772    1% /boot
/dev/mapper/LVG-home  48192   1348  46844    3% /home
/dev/mapper/LVG-opt   48192     11  48181    1% /opt
/dev/mapper/LVG-srv   48192     11  48181    1% /srv
/dev/mapper/LVG-usr  121920 115941   5979   96% /usr
/dev/mapper/LVG-var  121920   2743 119177    3% /var

```

I see /usr is at 96%. But does the root account use /usr for updates?

---

### Post by TheFu on 2013-08-05
Yes, yes it does. Where do you think programs go?

---

### Post by JnPson on 2013-08-05
Oh. What do I do to..., and how do I remove unnecessary programs or files? The server is using LVM so I could add more diskspace.

If I do apt-get autoremove I get the same error
```
(Reading database ... 133211 files and directories currently installed.)
Unpacking linux-headers-3.5.0-37-generic (from .../linux-headers-3.5.0-37-generic_3.5.0-37.58~precise1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-37-generic_3.5.0-37.58~precise1_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.5.0-37-generic/include/config/nfs/v4/1/implementation/id': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.5.0-37-generic_3.5.0-37.58~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by TheFu on 2013-08-05
Let's think about the issue for a second.  /usr is almost out of inodes. We know what I inode is, right?  If not, the wikipedia article will explain.
We need to free up inodes on the /usr partition/volume.  There are lots of ways to accomplish that task, right?
* delete some files
* move the files to a different partition
* make a new partition with more inodes, them migrate everything from the old one to the new one
2 of these are temporary fixes and deleting files outside the package manager is a bad idea.  The package manager is in a "stuck" point, so that really won't work. The last option is a permanent fix, provided the number of inodes allocated is made sufficient for all future needs. There is a default way that inodes are allocated for every partition. That default can be changed as you like - I don't recall exactly how that it done - but I'd look in the mkfs man page for it.  Failing that, google will find the setting necessary. I don't believe that inodes can be added or increased after a file system has been created, but I've been wrong before.  Perhaps LVM has a way to deal with this? I dunno.

---

### Post by Chaosadnd on 2013-08-28
Believe it or not I kind of forgot about this thread due to RL stuff going on, I am still unable to update. I will try and read through the linked stuff today to get it fixed.

Edit: Just looked over the boot repair thread. Too bad there is no command line tool for that. Though their likely is, I'm just an idiot lol

---

### Post by Bashing-om on 2013-08-28
Chaosadnd; Hey ..

Have you taken care of the 1st order of business as TheFu had observed ? You gotta have the disk space.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by TheFu on 2013-08-29
There is, it is part of the grub2 package and requires much more knowledge to use. Getting it wrong ... well, ... that can be really bad.
I'm going to stop following this thread.

---

### Post by JnPson on 2013-09-05
I have solved this on two servers with similar problems updating using **aptitude**. I have provided a solution for this here [http://ubuntuforums.org/showthread.php?t=2169901&page=2](http://ubuntuforums.org/showthread.php?t=2169901&page=2)
When I run df -hi I see that lots of Inodes was removed:
```
root@dc01:~# df -hi
Filesystem           Inodes IUsed IFree IUse% Mounted on
/dev/mapper/LVG-root   120K   34K   86K   28% /
udev                   124K   531  123K    1% /dev
tmpfs                  126K   465  125K    1% /run
none                   126K     5  126K    1% /run/lock
none                   126K     1  126K    1% /run/shm
/dev/mapper/LVG-tmp    120K    11  120K    1% /tmp
/dev/mapper/LVG-bak    120K    11  120K    1% /bak
/dev/sda1              143K   251  143K    1% /boot
/dev/mapper/LVG-home    48K  1.8K   46K    4% /home
/dev/mapper/LVG-opt     48K    11   48K    1% /opt
/dev/mapper/LVG-srv     48K    11   48K    1% /srv
/dev/mapper/LVG-usr    120K   69K   51K   58% /usr
/dev/mapper/LVG-var    120K  2.7K  117K    3% /var

```
```
root@dc01:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root  1.9G  1.1G  682M  62% /
udev                  494M   12K  494M   1% /dev
tmpfs                 201M  332K  201M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  502M     0  502M   0% /run/shm
/dev/mapper/LVG-tmp   461M   11M  427M   3% /tmp
/dev/mapper/LVG-bak   461M   11M  427M   3% /bak
/dev/sda1             268M  123M  131M  49% /boot
/dev/mapper/LVG-home  183M   33M  141M  19% /home
/dev/mapper/LVG-opt   183M  5.6M  168M   4% /opt
/dev/mapper/LVG-srv   183M  5.6M  168M   4% /srv
/dev/mapper/LVG-usr   1.9G  896M  884M  51% /usr
/dev/mapper/LVG-var   1.9G  372M  1.4G  21% /var

```

Regards JnPson

---

### Post by Chaosadnd on 2013-09-05
I have plenty of disk space. My issue that Im having problem with is how to clean out /boot. There is currently 560 GB  free on the drive.

---

### Post by Chaosadnd on 2013-09-05
> **TheFu said:**
> There is, it is part of the grub2 package and requires much more knowledge to use. Getting it wrong ... well, ... that can be really bad.
I'm going to stop following this thread.


Oookay? Take care?

---

### Post by Chaosadnd on 2013-09-05
Your link absolutely worked. You're a lifesaver JnPson!

---

### Post by JnPson on 2013-09-05
Glad I could help. 

Don't forget to mark this thread as solved.

---

### Post by Chaosadnd on 2013-09-05
Almost solved. I am currently now getting Erros were encountered while processing initramfs-tools. Currently looking into how to get that fixed.

---

### Post by JnPson on 2013-09-06
Ok. Sorry to hear that a new problem occurred. If initramfs came after the initial error was fixed it might be better to start a new thread for "Updating initramfs error". 

Btw here's a link to something that might help: [https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/](https://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/)

---

### Post by Chaosadnd on 2013-09-09
Just to update and finish this thread, I ended up wrecking the kernel, and made the excuse to install a clean install :P

---

