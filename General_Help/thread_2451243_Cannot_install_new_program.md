---
title: "Cannot install new program"
date: 2020-09-29
forum: General Help
---

### Post by tomnguyen168 on 2020-09-29
Hi all,

I am quite still quite new to Ubuntu, and having a dual boot system (Ubuntu 20.04 & Win 10), UEFI
After around 2 months running on this set up, I cannot install using apt anymore.
For example, when I try to install mkchromecast:

```


viet@viet-Vostro-15-3568:~$ sudo apt install mkchromecast
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ffmpeg flac javascript-common lame libavdevice58 libavresample4 libjs-jquery
  libnode64 libqt5designer5 libqt5help5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5xml5 libsox-fmt-alsa libsox-fmt-base libsox3 nodejs
  nodejs-doc opus-tools python3-flask python3-ifaddr python3-itsdangerous
  python3-jinja2 python3-markupsafe python3-nose python3-openssl
  python3-psutil python3-pychromecast python3-pyinotify python3-pyqt5
  python3-pyxattr python3-sip python3-werkzeug python3-zeroconf rtmpdump sox
  vorbis-tools youtube-dl
Suggested packages:
  ffmpeg-doc lame-doc libsox-fmt-all libav-tools mkchromecast-pulseaudio
  mkchromecast-alsa npm python-flask-doc python-jinja2-doc python-nose-doc
  python-openssl-doc python3-openssl-dbg python-psutil-doc
  python-pyinotify-doc python3-pyqt5-dbg python3-pyxattr-dbg
  python-pyxattr-doc ipython3 python-werkzeug-doc python3-lxml
  python3-termcolor python3-watchdog libfribidi-bin | bidiv phantomjs
The following packages will be REMOVED:
  linux-image-5.4.0-42-generic
The following NEW packages will be installed:
  ffmpeg flac javascript-common lame libavdevice58 libavresample4 libjs-jquery
  libnode64 libqt5designer5 libqt5help5 libqt5sql5 libqt5sql5-sqlite
  libqt5test5 libqt5xml5 libsox-fmt-alsa libsox-fmt-base libsox3 mkchromecast
  nodejs nodejs-doc opus-tools python3-flask python3-ifaddr
  python3-itsdangerous python3-jinja2 python3-markupsafe python3-nose
  python3-openssl python3-psutil python3-pychromecast python3-pyinotify
  python3-pyqt5 python3-pyxattr python3-sip python3-werkzeug python3-zeroconf
  rtmpdump sox vorbis-tools youtube-dl
0 upgraded, 40 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/17.9 MB of archives.
After this operation, 65.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Extracting templates from packages: 100%
(Reading database ... 221558 files and directories currently installed.)
Removing linux-image-5.4.0-42-generic (5.4.0-42.46) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-42-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-42-generic (--remove):
 installed linux-image-5.4.0-42-generic package post-removal script subprocess r
eturned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.4.0-42-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

and when I try to re-configure dpkg, things not working:

```

viet@viet-Vostro-15-3568:~$ sudo dpkg --configure -a
Setting up grub-pc (2.04-1ubuntu26.4) ...
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 1
Setting up linux-image-5.4.0-48-generic (5.4.0-48.52) ...
Processing triggers for linux-image-5.4.0-48-generic (5.4.0-48.52) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-48-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-48-generic (--configure):
 installed linux-image-5.4.0-48-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 grub-pc
 linux-image-5.4.0-48-generic



```

I guess that the issue is with my grub but I dont know how to fix it  :(
Can I please have some help. Thanks in advance.



[UPDATED]: re-install ubuntu solved the issue

---

### Post by Impavidus on 2020-09-30
Some time in the past you (or unattended-updates) removed the old kernel 5.4.0-42 and failed. Now the package manager will continue to try and fail until this is fixed by a human.

> **tomnguyen168 said:**
> 
```

viet@viet-Vostro-15-3568:~$ sudo dpkg --configure -a
Setting up grub-pc (2.04-1ubuntu26.4) ...
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
[b]Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.[/b]
...

```
Let's start there. What's in your /etc/default/grub, what's in your /etc/grub.d/ and what's in your /boot/grub/grub.cfg.new?
```
cat /etc/default/grub
ls -l /etc/grub.d
cat /boot/grub/grub.cfg.new
```
Further, have you done anything special with grub? Any changes compared to what it was when you first installed Ubuntu?

---

### Post by tomnguyen168 on 2020-09-30
hi,
Thank you for your reply.
These are contents of my grub files:

```
viet@viet-Vostro-15-3568:~$ cat /etc/default/grub# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
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
viet@viet-Vostro-15-3568:~$ ls -l /etc/grub.d
total 0
viet@viet-Vostro-15-3568:~$ cat /boot/grub/grub.cfg.new
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
viet@viet-Vostro-15-3568:~$ 



```

2. I dont remember doing anything fancy with my grub file, just update grub2

---

### Post by CelticWarrior on 2020-09-30
> [COLOR=#000000]2. I dont remember doing anything fancy with my grub file, just update grub2[/COLOR]

Please elaborate. How exactly did you update grub2?
Grub updates are served alongside all the other updates and typically users don't even notice it. The "just update grub2" part of your sentence is what bothers me now (and surely Impavidus is curious too).

---

### Post by mc4man on 2020-09-30
Don't you have /boot/grub/grub.cfg & why is there a /boot/grub/grub.cfg.new file?
(- i'd likely delete  /boot/grub/grub.cfg.new & run sudo update-grub

---

### Post by Impavidus on 2020-09-30
I don't know if there's no /boot/grub/grub.cfg and I didn't ask. I guess it's actually there and correct, or the system would be unbootable. I think update-grub creates a /boot/grub/grub.cfg.new and only if that's successful (so not in this case), it deletes the old grub.cfg and renames grub.cgf.new to grub.cfg.

In any case, what's wrong here is that the scripts run by update-grub in /etc/grub.d/ are missing. I wonder what could have caused that. Reinstalling grub-common may fix it. On most Ubuntu systems there's also a memtest in that directory, which has to reinstalled too (package is called memtest86+), but reinstalling grub-common is vital before the package manager can be fixed. Let's see if apt can reinstall it:```
sudo apt install --reinstall grub-common
```I wouldn't be surprised if this fails, but there are more low-level ways to do this.

It may be good to know more about the status of some vital packages. If above command doesn't allow you to fix it, can you show the output of```
dpkg --list linux-* grub*
dpkg --list | grep -v '^ii \|^rc '
```

---

### Post by tomnguyen168 on 2020-09-30
Hi,

> **CelticWarrior said:**
> Please elaborate. How exactly did you update grub2?
Grub updates are served alongside all the other updates and typically users don't even notice it. The "just update grub2" part of your sentence is what bothers me now (and surely Impavidus is curious too).

I just ran "sudo update-grub"

> **Impavidus said:**
> I don't know if there's no /boot/grub/grub.cfg and I didn't ask. I guess it's actually there and correct, or the system would be unbootable. I think update-grub creates a /boot/grub/grub.cfg.new and only if that's successful (so not in this case), it deletes the old grub.cfg and renames grub.cgf.new to grub.cfg.

In any case, what's wrong here is that the scripts run by update-grub in /etc/grub.d/ are missing. I wonder what could have caused that. Reinstalling grub-common may fix it. On most Ubuntu systems there's also a memtest in that directory, which has to reinstalled too (package is called memtest86+), but reinstalling grub-common is vital before the package manager can be fixed. Let's see if apt can reinstall it:```
sudo apt install --reinstall grub-common
```I wouldn't be surprised if this fails, but there are more low-level ways to do this.

It may be good to know more about the status of some vital packages. If above command doesn't allow you to fix it, can you show the output of```
dpkg --list linux-* grub*
dpkg --list | grep -v '^ii \|^rc '
```

The re-installation was failed as you suspected:

```
viet@viet-Vostro-15-3568:~$ sudo apt install --reinstall grub-common[sudo] password for viet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.4.0-42-generic
0 upgraded, 0 newly installed, 1 reinstalled, 1 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 1,873 kB of archives.
After this operation, 11.7 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://ca.archive.ubuntu.com/ubuntu focal-updates/main amd64 grub-common amd64 2.04-1ubuntu26.4 [1,873 kB]
Fetched 1,873 kB in 4s (484 kB/s)        
Preconfiguring packages ...
(Reading database ... 221558 files and directories currently installed.)
Removing linux-image-5.4.0-42-generic (5.4.0-42.46) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-42-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-42-generic (--remove):
 installed linux-image-5.4.0-42-generic package post-removal script subprocess r
eturned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.4.0-42-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
viet@viet-Vostro-15-3568:~$ 



```


And this is the result of command you gave me:

```


viet@viet-Vostro-15-3568:~$ dpkg --list linux-* grub*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version              Architecture Description
+++-=====================================-====================-============-==============================================================
un  grub                                  <none>               <none>       (no description available)
un  grub-cloud-amd64                      <none>               <none>       (no description available)
ii  grub-common                           2.04-1ubuntu26.4     amd64        GRand Unified Bootloader (common files)
un  grub-coreboot                         <none>               <none>       (no description available)
un  grub-doc                              <none>               <none>       (no description available)
un  grub-efi                              <none>               <none>       (no description available)
rc  grub-efi-amd64                        2.04-1ubuntu26.3     amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version)
ii  grub-efi-amd64-bin                    2.04-1ubuntu26.4     amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 modules)
un  grub-efi-amd64-signed                 <none>               <none>       (no description available)
un  grub-efi-arm                          <none>               <none>       (no description available)
un  grub-efi-arm64                        <none>               <none>       (no description available)
un  grub-efi-arm64-signed                 <none>               <none>       (no description available)
un  grub-efi-ia32                         <none>               <none>       (no description available)
un  grub-efi-ia64                         <none>               <none>       (no description available)
un  grub-emu                              <none>               <none>       (no description available)
ii  grub-gfxpayload-lists                 0.7                  amd64        GRUB gfxpayload blacklist
un  grub-ieee1275                         <none>               <none>       (no description available)
un  grub-legacy                           <none>               <none>       (no description available)
un  grub-legacy-doc                       <none>               <none>       (no description available)
un  grub-linuxbios                        <none>               <none>       (no description available)
iF  grub-pc                               2.04-1ubuntu26.4     amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                           2.04-1ubuntu26.4     amd64        GRand Unified Bootloader, version 2 (PC/BIOS modules)
un  grub-uboot                            <none>               <none>       (no description available)
un  grub-xen                              <none>               <none>       (no description available)
un  grub-yeeloong                         <none>               <none>       (no description available)
un  grub2                                 <none>               <none>       (no description available)
ii  grub2-common                          2.04-1ubuntu26.4     amd64        GRand Unified Bootloader (common files for version 2)
ii  linux-base                            4.5ubuntu3.1         all          Linux image base package
un  linux-doc                             <none>               <none>       (no description available)
ii  linux-firmware                        1.187.3              all          Firmware for Linux kernel drivers
un  linux-firmware-raspi2                 <none>               <none>       (no description available)
un  linux-firmware-snapdragon             <none>               <none>       (no description available)
ii  linux-generic-hwe-20.04               5.4.0.48.51          amd64        Complete Generic Linux kernel and headers
un  linux-headers                         <none>               <none>       (no description available)
un  linux-headers-3.0                     <none>               <none>       (no description available)
ii  linux-headers-5.4.0-42                5.4.0-42.46          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic        5.4.0-42.46          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-45                5.4.0-45.49          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-45-generic        5.4.0-45.49          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-48                5.4.0-48.52          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-48-generic        5.4.0-48.52          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04       5.4.0.48.51          amd64        Generic Linux kernel headers
un  linux-image                           <none>               <none>       (no description available)
rH  linux-image-5.4.0-42-generic          5.4.0-42.46          amd64        Signed kernel image generic
ii  linux-image-5.4.0-45-generic          5.4.0-45.49          amd64        Signed kernel image generic
iF  linux-image-5.4.0-48-generic          5.4.0-48.52          amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04         5.4.0.48.51          amd64        Generic Linux kernel image
un  linux-image-unsigned-5.4.0-42-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.4.0-45-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.4.0-48-generic <none>               <none>       (no description available)
un  linux-initramfs-tool                  <none>               <none>       (no description available)
un  linux-kernel-headers                  <none>               <none>       (no description available)
un  linux-kernel-log-daemon               <none>               <none>       (no description available)
ii  linux-libc-dev:amd64                  5.4.0-48.52          amd64        Linux Kernel Headers for development
ii  linux-modules-5.4.0-42-generic        5.4.0-42.46          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-45-generic        5.4.0-45.49          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-48-generic        5.4.0-48.52          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-42-generic  5.4.0-42.46          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-45-generic  5.4.0-45.49          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-48-generic  5.4.0-48.52          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
un  linux-restricted-common               <none>               <none>       (no description available)
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5 all          base package for ALSA and OSS sound systems
un  linux-source-5.4.0                    <none>               <none>       (no description available)
un  linux-tools                           <none>               <none>       (no description available)


```

---

### Post by Impavidus on 2020-09-30
You missed the last command, but I already see which three are broken. I also see that grub-pc is half-configured, so that must be fixed too.

Let's first try to get grub-common re-installed.```
apt-get download grub-common
sudo dpkg --install grub-common<tab>
```Use tab completion to get the full name of the .deb package with grub-common, which can contain a rather long version string.

Try to get grub-pc configured:```
dpkg --configure grub-pc
```

Maybe then apt works again and manages to remove kernel 5.4.0-42 and install kernel 5.4.0-48.

---

### Post by tomnguyen168 on 2020-09-30
hi all,

It failed when I tried to configure grub-pc:

```

viet@viet-Vostro-15-3568:~$ apt-get download grub-common
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) focal-updates/main amd64 grub-common amd64 2.04-1ubuntu26.4 [1,873 kB]
Fetched 1,873 kB in 2s (1,213 kB/s)      
viet@viet-Vostro-15-3568:~$ sudo dpkg --install grub-common_2.04-1ubuntu26.4_amd64.deb 
[sudo] password for viet: 
(Reading database ... 221558 files and directories currently installed.)
Preparing to unpack grub-common_2.04-1ubuntu26.4_amd64.deb ...
Unpacking grub-common (2.04-1ubuntu26.4) over (2.04-1ubuntu26.4) ...
Setting up grub-common (2.04-1ubuntu26.4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for systemd (245.4-4ubuntu3.2) ...
Processing triggers for man-db (2.9.1-1) ...
viet@viet-Vostro-15-3568:~$ dpkg --configure grub-pc
dpkg: error: requested operation requires superuser privilege
viet@viet-Vostro-15-3568:~$ sudo dpkg --configure grub-pc
Setting up grub-pc (2.04-1ubuntu26.4) ...
Sourcing file `/etc/default/grub'
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
viet@viet-Vostro-15-3568:~$ 

```


and when I try to re-install grub, it says that something cannot be found:
```

viet@viet-Vostro-15-3568:~$ sudo apt-get install grub-pc --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.4.0-42-generic
0 upgraded, 0 newly installed, 1 reinstalled, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 11.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
E: Internal Error, No file name for grub-pc:amd64
viet@viet-Vostro-15-3568:~$ 


```

when I try to dpkg remove grub-pc, it says that grub-gfxpayload-lists depends on grub-pc
and then if I try to remove grub-gfxpayload-lists, it says that grub-pc depends on grub-gfxpayload-lists ! (they seem to depends on each other)
```


viet@viet-Vostro-15-3568:~$ sudo dpkg --remove grub-pc
dpkg: dependency problems prevent removal of grub-pc:
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2).


dpkg: error processing package grub-pc (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 grub-pc
viet@viet-Vostro-15-3568:~$ sudo dpkg --remove grub-gfxpayload-lists
dpkg: dependency problems prevent removal of grub-gfxpayload-lists:
 grub-pc depends on grub-gfxpayload-lists.


dpkg: error processing package grub-gfxpayload-lists (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 grub-gfxpayload-lists
viet@viet-Vostro-15-3568:~$ 



```

---

### Post by Impavidus on 2020-10-01
It says it did unpack grub-common, so that should have brought the scripts in /etc/grub.d/ back, but when building the grub.cfg it still encounters the same error.

Can you check again what's in /etc/grub.d/?

I'm still wondering what could have gone wrong here. Files in /etc/grub.d/ shouldn't go missing without a reason.

---

### Post by tomnguyen168 on 2020-10-01
> **Impavidus said:**
> It says it did unpack grub-common, so that should have brought the scripts in /etc/grub.d/ back, but when building the grub.cfg it still encounters the same error.

Can you check again what's in /etc/grub.d/?

I'm still wondering what could have gone wrong here. Files in /etc/grub.d/ shouldn't go missing without a reason.


hi,

My system seems to deteriorate, more things stop working so I just decided to re-install Ubuntu. Things are good now. :)
I think we can mark the topic as closed. Thank you very much for your support :p

---

### Post by TheFu on 2020-10-01
If things get worse and worse, then I'd look for a hardware problem.

Only YOU can mark the thread as SOLVED to help the community.  That will let others see that a reinstall was the solution and stop people who want to help from wasting time in a thread.

---

### Post by tomnguyen168 on 2020-10-01
> **TheFu said:**
> If things get worse and worse, then I'd look for a hardware problem.

Only YOU can mark the thread as SOLVED to help the community.  That will let others see that a reinstall was the solution and stop people who want to help from wasting time in a thread.


Pardon me, how can I do that? Manually change the thread's name or we have special buttons for that?

Edit: Found the button

---

