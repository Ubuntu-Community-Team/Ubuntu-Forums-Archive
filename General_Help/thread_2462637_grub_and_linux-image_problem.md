---
title: "grub and linux-image problem?"
date: 2021-05-24
forum: General Help
---

### Post by grasshopper94 on 2021-05-24
This is what happens whenever I try to install something through the terminal:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wget is already the newest version (1.20.3-1ubuntu1).
wget set to manually installed.
build-essential is already the newest version (12.8ubuntu1.1).
build-essential set to manually installed.
libssl-dev is already the newest version (1.1.1f-1ubuntu2.4).
libssl-dev set to manually installed.
The following package was automatically installed and is no longer required:
  linux-modules-5.8.0-49-generic
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libncurses-dev libnspr4-dev
Suggested packages:
  ncurses-doc readline-doc
The following packages will be REMOVED:
  linux-image-5.8.0-49-generic
The following NEW packages will be installed:
  libffi-dev libgdbm-dev libncurses-dev libncurses5-dev libnspr4-dev libnss3-dev libreadline-dev zlib1g-dev
0 upgraded, 8 newly installed, 1 to remove and 7 not upgraded.
3 not fully installed or removed.
Need to get 1.214 kB of archives.
After this operation, 2.901 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 libgdbm-dev amd64 1.18.1-5 [83,4 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal/main amd64 libncurses-dev amd64 6.2-0ubuntu2 [339 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal/main amd64 libncurses5-dev amd64 6.2-0ubuntu2 [976 B]
Get:4 http://archive.ubuntu.com/ubuntu focal/main amd64 libnspr4-dev amd64 2:4.25-1 [206 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libnss3-dev amd64 2:3.49.1-1ubuntu1.5 [231 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal/main amd64 libreadline-dev amd64 8.0-4 [141 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 zlib1g-dev amd64 1:1.2.11.dfsg-2ubuntu1.2 [155 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal/main amd64 libffi-dev amd64 3.3-4 [57,0 kB]
Fetched 1.214 kB in 0s (2.750 kB/s)   
(Reading database ... 290766 files and directories currently installed.)
Removing linux-image-5.8.0-49-generic (5.8.0-49.55~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.8.0-49-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.8.0-49-generic (--remove):
 installed linux-image-5.8.0-49-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.8.0-49-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Unfortunately it won't tell me the error line number, so I don't know what to even look for.

 This is the content of my /etc/default/grub:


```
GNU nano 4.8                                                                                 /etc/default/grub                                                                                           
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if GNU nano 4.8                                                                                 /etc/default/grub                                                                                           
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I don't know if this helps but just in case... When I run:
 sudo nano /etc/grub.d/* 
nano opens up and gives this message at the bottom:

 ```
[ Directory '/etc/grub.d' does not exist ]

```

And dpkg -C:
```
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 grub-pc              GRand Unified Bootloader, version 2 (PC/BIOS version)
 linux-image-5.8.0-53-generic Signed kernel image generic

The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-5.8.0-49-generic Signed kernel image generic
```

Running the commands dpkg --configure for grub-pc and linux-image, as suggested in the above output, gives:

```
$ sudo dpkg --configure grub-pc
[sudo] password for reagan: 
Setting up grub-pc (2.04-1ubuntu26.11) ...
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 grub-pc
```

```
$ sudo dpkg --configure linux-image-5.8.0-53-generic
    Setting up linux-image-5.8.0-53-generic (5.8.0-53.60~20.04.1) ...
    Processing triggers for linux-image-5.8.0-53-generic (5.8.0-53.60~20.04.1) ...
    /etc/kernel/postinst.d/dkms:
     * dkms: running auto installation service for kernel 5.8.0-53-generic
       ...done.
    /etc/kernel/postinst.d/initramfs-tools:
    update-initramfs: Generating /boot/initrd.img-5.8.0-53-generic
    /etc/kernel/postinst.d/zz-update-grub:
    Sourcing file `/etc/default/grub'
    Sourcing file `/etc/default/grub.d/init-select.cfg'
    Generating grub configuration file ...
    Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
    Syntax errors are detected in generated GRUB config file.
    Ensure that there are no errors in /etc/default/grub
    and /etc/grub.d/* files or please file a bug report with
    /boot/grub/grub.cfg.new file attached.
    run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
    dpkg: error processing package linux-image-5.8.0-53-generic (--configure):
     installed linux-image-5.8.0-53-generic package post-installation script subprocess returned error exit status 1
    Errors were encountered while processing:
     linux-image-5.8.0-53-generic
```

When running nano /boot/grub/grub.cfg.new:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#








             [ File '/boot/grub/grub.cfg.new' is unwritable ]
```

Running nano /boot/grub/grub.cfg is the same thing plus a big list of if...else statements.

---

### Post by grahammechanical on 2021-05-24
I would like to make a few points that may or may not help.

1) When a new kernel is installed and/or an old kernel is removed the grub.cfg file is regenerated. The standard update/upgrade commands when run in a terminal do not remove old kernels unless we are running update/upgrade/autoremove as a series of linked commands. 

2) It am certain that it is not standard to have a /boot/grub/grub.cfg.new file. Unless the regeneration process first creates grub.cfg.new, then populates it with information, then deletes grub.cfg and finally renames grub.cfg.new as grub.cfg. I do not know if I am guessing correctly but clearly something has gone wrong with the update-grub process.

3) My /etc/default/grub file contains one example of this

> GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Your /etc/default/grub contains two examples. I am guessing that is part of the problem. This is my unmodified /etc/default/grub. It may help when you compare it with your version.

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Edit: Here is an afterthought. Use the file manager to examine /etc/grub.d. You will find that it contains eleven files. All but one of them are shell scripts. Perhaps that is why your attempt to open the grub.d folder in nano failed. If indeed /etc/grub.d does not exist then your system is missing those ten shell scripts and that could be the problem.

Regards

---

### Post by Impavidus on 2021-05-25
> **grasshopper94 said:**
> 

I don't know if this helps but just in case... When I run:
 sudo nano /etc/grub.d/* 
nano opens up and gives this message at the bottom:

 ```
[ Directory '/etc/grub.d' does not exist ]

```


Your /etc/grub.d doesn't exist. When update-grub tries to generate a new grub.cfg, it runs the scripts in grub.d to create a grub.cfg.new, then checks it to see if there are any obvious errors, then it replaces the old grub.cfg with the new. If it first deleted the old grub.cfg and then created a new one, any error would leave your computer in a non-bootable state. As you have no scripts in /etc/grub.d, your grub.cfg.new is empty. update-grub detects this and gives an error message.

/etc/grub.d is part of the grub-common package. Try reinstalling is. With a bit of luck apt is willing to reinstall grub-common before attempting to use it:```
sudo apt-get install --reinstall grub-common
```If not, we have to ask dpkg.

---

