---
title: "Kernel update problems"
date: 2013-05-19
forum: General Help
---

### Post by sunblock on 2013-05-19
After upgrading to 12.04, I am getting dependency errors that I cant seem to resolve. here is the output of my apt-get -f install, any ideas ?
 
root@mike-laptop-ub:/home/mike# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libswscale0 gir1.2-gconf-2.0 libavutil49 appmenu-gtk linux-headers-2.6.32-21
  linux-headers-2.6.32-22 ttf-dejavu-extra wine1.2 libpostproc51
  libaccess-bridge-java-jni libaccess-bridge-java openoffice.org-l10n-common
  libavformat52 libdvbpsi5 appmenu-qt libx264-85 libiso9660-7 cups-pk-helper
  libavcodec52 openoffice.org-l10n-en-gb libid3tag0 libmodplug0c2
  linux-headers-2.6.32-22-generic-pae ca-certificates-java libebml0 libmpcdec3
  appmenu-gtk3 libmatroska0 gir1.2-panelapplet-4.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-pc
The following packages will be upgraded:
  grub-pc
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
11 not fully installed or removed.
Need to get 0 B/140 kB of archives.
After this operation, 1,806 kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.32-35-generic-pae (2.6.32-35.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-43-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-36-generic-pae (2.6.32-36.79) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-36-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-37-generic-pae (2.6.32-37.81) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-37-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-3.2.0-43-generic-pae (3.2.0-43.68) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-3.2.0-43-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Setting up friendly-recovery (0.2.25) ...
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
dpkg: error processing friendly-recovery (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Setting up memtest86+ (4.20-1.1ubuntu1) ...
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 1.98-1ubuntu12); however:
  Version of grub-common on system is 1.99-21ubuntu3.9.
dpkg: error processing grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-gfxpayload-lists:
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2); however:
  Version of grub-pc on system is 1.98-1ubuntu12.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: error processing grub-gfxpayload-lists (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-36-generic-pae; however:
  Package linux-image-2.6.32-36-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.36.42); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.32-35-generic-pae
 linux-image-2.6.32-36-generic-pae
 linux-image-2.6.32-37-generic-pae
 linux-image-3.2.0-43-generic-pae
 friendly-recovery
 memtest86+
 ubuntu-standard
 grub-pc
 grub-gfxpayload-lists
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mike-laptop-ub:/home/mike#

---

### Post by claracc on 2013-05-19
Have you edit the file /etc/default/grub ?, as I can see in your post, you have an error in the line 

GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp: not found

I think you have to close with semicolons: i.e.:

GRUB_CMDLINE_LINUX="i8042.nopnp"

Note also the kind of semicollons used, the straightforward ones.

---

### Post by fantab on 2013-05-19
> **claracc said:**
> Have you edit the file /etc/default/grub ?, as I can see in your post, you have an error in the line 

GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp: not found

I think you have to close with semicolons: i.e.:

GRUB_CMDLINE_LINUX="i8042.nopnp"

Note also the kind of semicollons used, the straightforward ones.

Those marks are called "Quotation" marks. ; is semicolon.

@**sunblock**:
As suggested by claracc, edit your /etc/default/grub SAVe the file and run from terminal:
```
sudo update-grub
```

Then run:
```
sudo apt-get update && sudo apt-get upgrade
```

If you still get the errors then:
```
uname -r
```
this will show you the current kernel in use. We will not remove that. so if I have listed the kernel below, do remove it.

```
sudo dpkg --purge linux-image-2.6.32-35-generic-pae linux-image-2.6.32-36-generic-pae linux-image-2.6.32-37-generic-pae linux-image-3.2.0-43-generic-pae
sudo apt-get remove --purge linux-image-2.6.32-35-generic-pae linux-image-2.6.32-36-generic-pae  linux-image-2.6.32-37-generic-pae linux-image-3.2.0-43-generic-pae
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get clean 
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install linux
```

---

### Post by sunblock on 2013-05-19
interesting, the line in grub is already in quotes :

GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp"

running update-grub produces :

/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp: not found



I tried to change both quotes to " but that made an error, then I cleared the entire line from grub, but when I run update-grub I get

/usr/sbin/grub-mkconfig: 27: /etc/default/grub: Syntax error: EOF in backquote substitution

My entire edited grub file is below, not sure where the syntax issue is, but I do not see any open quotes or anything like that :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



Is there someway to simply install [COLOR=#000000]*i8042.nopnp again, I can not seem to locate much info on the web about it. *[/COLOR]

---

### Post by fantab on 2013-05-19
> **fantab said:**
> 
```
sudo apt-get update && sudo apt-get upgrade
```

If you still get the errors then:
```
uname -r
```
this will show you the current kernel in use. We will not remove that. so if I have listed the kernel below, do remove it.

```
sudo dpkg --purge linux-image-2.6.32-35-generic-pae linux-image-2.6.32-36-generic-pae linux-image-2.6.32-37-generic-pae linux-image-3.2.0-43-generic-pae
sudo apt-get remove --purge linux-image-2.6.32-35-generic-pae linux-image-2.6.32-36-generic-pae  linux-image-2.6.32-37-generic-pae linux-image-3.2.0-43-generic-pae
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get clean 
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install linux
```

Just try the above. Perhaps the Grub error is because of broken kernel pkgs.

---

### Post by sunblock on 2013-05-19
Still get lots of the same errors, when I get back to apt-get -f install I get fewer errors, but many of the same. the current kernel is  2.6.32-28-generic-pae

root@mike-laptop-ub:/etc/default# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libswscale0 gir1.2-gconf-2.0 libavutil49 appmenu-gtk linux-headers-2.6.32-21 linux-headers-2.6.32-22 ttf-dejavu-extra wine1.2 libpostproc51
  libaccess-bridge-java-jni libaccess-bridge-java openoffice.org-l10n-common libavformat52 libdvbpsi5 appmenu-qt libx264-85 libiso9660-7
  cups-pk-helper libavcodec52 openoffice.org-l10n-en-gb libid3tag0 libmodplug0c2 linux-headers-2.6.32-22-generic-pae ca-certificates-java libebml0
  libmpcdec3 appmenu-gtk3 libmatroska0 gir1.2-panelapplet-4.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-pc linux-generic-pae linux-image-3.2.0-43-generic-pae linux-image-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-43-generic-pae
The following packages will be upgraded:
  grub-pc linux-generic-pae linux-image-generic-pae
3 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0 B/38.4 MB of archives.
After this operation, 112 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package linux-image-3.2.0-43-generic-pae.
(Reading database ... 312562 files and directories currently installed.)
Unpacking linux-image-3.2.0-43-generic-pae (from .../linux-image-3.2.0-43-generic-pae_3.2.0-43.68_i386.deb) ...
Done.
Setting up friendly-recovery (0.2.25) ...
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
dpkg: error processing friendly-recovery (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up memtest86+ (4.20-1.1ubuntu1) ...
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 1.98-1ubuntu12); however:
  Version of grub-common on system is 1.99-21ubuntu3.9.
dpkg: error processing grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-gfxpayload-lists:
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2); however:
  Version of grub-pc on system is 1.98-1ubuntu12.
dpkg: error processing grub-gfxpayload-lists (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.0-43-generic-pae (3.2.0-43.68) ...
Running depmod.
No apport report written because MaxReports is reached already
                                                              update-initramfs: deferring update (hook will be called later)
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-3.2.0-43-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-36-generic-pae; however:
  Package linux-image-2.6.32-36-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.36.42); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 friendly-recovery
 memtest86+
 ubuntu-standard
 grub-pc
 grub-gfxpayload-lists
 linux-image-3.2.0-43-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mike-laptop-ub:/etc/default#

---

### Post by sunblock on 2013-05-19
also noticing I cant get rid of that 3.2.0

root@mike-laptop-ub:/etc/default# sudo dpkg --purge linux-image-3.2.0-43-generic-pae(Reading database ... 316942 files and directories currently installed.)
Removing linux-image-3.2.0-43-generic-pae ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
Running postrm hook script /usr/sbin/update-grub.
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
User postrm hook script [/usr/sbin/update-grub] exited with value 127
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-43-generic-pae
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.2.0-43-generic-pae ...
Running postrm hook script /usr/sbin/update-grub.
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: splash
GRUB_CMDLINE_LINUX=”i8042.nopnp: not found
User postrm hook script [/usr/sbin/update-grub] exited with value 127
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
root@mike-laptop-ub:/etc/default#

---

### Post by ibjsb4 on 2013-05-19
Any chance of some Lucid sources still lingering around?  Look in:

```
cat /etc/apt/sources.list
```

Also wine 1.2, isn't that a Lucid package?

---

### Post by sunblock on 2013-05-19
not sure, should I comment any of these out ?

root@mike-laptop-ub:/etc/default# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


# deb [http://debian.wgdd.de/ubuntu](http://debian.wgdd.de/ubuntu) jaunty main restricted universe multiverse # disabled on upgrade to precise
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
root@mike-laptop-ub:/etc/default#

---

### Post by fantab on 2013-05-19
I think you have to reinstall GRUB:

Assuming you have only one HDD:

```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

See what happens with:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you get any errors then remove [COLOR=#000000]
[/COLOR]```
&#8203;[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --purge [/FONT][/COLOR][COLOR=#000000]linux-image-3.2.0-43-generic-pae [/COLOR][COLOR=#000000]linux-image-generic-pae [/COLOR][COLOR=#000000]linux-generic-pae[/COLOR]
sudo apt-get remove --purge 
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get clean 
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install linux
```

If no errors then:
```
sudo apt-get install linux
```

EDIT: My sources.list: [http://paste.ubuntu.com/5681125/](http://paste.ubuntu.com/5681125/) you can use it to compare and edit accordingly or just copy paste the relevant parts.

---

### Post by sunblock on 2013-05-19
get that same error relating to [COLOR=#000000]i8042.nopnp when trying to reintsall grub. This box is just an older laptop that I havent used the ub install in awhile. seems its installed as 32bit as well[/COLOR]
[COLOR=#000000]Think it will be simpler just to start over fresh with a 64bit install, nothing on the laptop needs keeping. Thanks for all the help though.  [/COLOR]

---

### Post by fantab on 2013-05-19
Re-installing always works. And feels lot simpler too. :)

By the way, [COLOR=#000000]i8042.nopnp is to enable touchpad support. I don't think you will need it with 12.04. 

Good Luck...[/COLOR]

---

