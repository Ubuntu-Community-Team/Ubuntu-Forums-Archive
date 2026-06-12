---
title: "No deinstallation of old kernels?"
date: 2015-04-12
forum: General Help
---

### Post by ofnuts on 2015-04-12
I asked a while ago[ how to prevent the automatic de-installation of old kernels]("http://ubuntuforums.org/showthread.php?t=2268989").

At the time I asked out of curiosity... I remember checking (in R/O mode...) the mentioned script, and made a note about it.

One month later I discover that I have two old kernels that haven't been de-installed (44 and 46, 46 being installed at about the time I asked the question: March 13). 

So now the situtation is:

[LIST]
[*]installed kernels: 44, 46, 48, 49 (where are 45 and 47?) 
[*]currently booted on 49 
[*]/etc/apt/apt.conf.d/01autoremove-kernels lists only 48 and 49 
[*]/etc/apt/apt.conf.d/01autoremove contains among other things:```
 VersionedKernelPackages
  {
    # linux kernels
    "linux-image";
    "linux-headers";
    "linux-image-extra";
    "linux-signed-image";
    # kfreebsd kernels
    "kfreebsd-image";
    "kfreebsd-headers";
    # hurd kernels
    "gnumach-image";
    # (out-of-tree) modules
    ".*-modules";
    ".*-kernel";
    "linux-backports-modules-.*";
        # tools
        "linux-tools";
  };
``` 
[/LIST]

Where can I find out why the old kernels aren't removed?

Edit: digging deeper:

Found /var/log/unattended-upgrades. The log for the install of the #48 kernel (that should have dropped the #44) contains:

```

run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-48-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic
Generating grub configuration file ...

```

So the apt-auto-removal script is run, but nothing seems to remove old kernels after it, since I assume that this should have happened before the grub configuration is done...

---

### Post by Bashing-om on 2015-04-12
ofnuts; Hello;

What I am aware of in this respect:
Kernel packages were marked as NeverAutoRemove in /etc/apt/apt.conf.d/01autoremove in older versions of Ubuntu, that changed with 
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/vivid/apt/vivid/revision/193/debian/apt.conf.autoremove#debian/apt.conf.autoremove](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/vivid/apt/vivid/revision/193/debian/apt.conf.autoremove#debian/apt.conf.autoremove)
 You can check if kernel packages on your system are actually marked for auto-removal with
```

apt-mark showauto ^linux-image-

```
and mark them explicitly with
```

sudo apt-mark auto ^linux-image-
sudo apt-mark manual '^linux-image-(generic|server)'

```
See: [http://ubuntuforums.org/showthread.php?t=2256452](http://ubuntuforums.org/showthread.php?t=2256452) (schragge )

Edit: of interest here:
> 
20# We generate this list and save it to /etc/apt/apt.conf.d instead of marking
 21# packages in the database because this runs from a postinst script, and apt
 22# will overwrite the db when it exits.

[INDENT][INDENT]as I too try and wrap my mind
[INDENT][INDENT][INDENT]around this
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ofnuts on 2015-04-12
> **Bashing-om said:**
> 
```

apt-mark showauto ^linux-image-

```


```

~$apt-mark showauto ^linux-image-
linux-image-3.13.0-44-generic
linux-image-3.13.0-46-generic
linux-image-3.13.0-48-generic
linux-image-3.13.0-49-generic
linux-image-extra-3.13.0-44-generic
linux-image-extra-3.13.0-46-generic
linux-image-extra-3.13.0-48-generic
linux-image-extra-3.13.0-49-generic
linux-image-generic

```

So they are?

---

### Post by Bashing-om on 2015-04-12
ofnuts; Yeah.

Kinda curious here as on my system presently:
```

sysop@1404mini:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-45 linux-headers-3.13.0-45-generic
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-45-generic linux-image-3.13.0-46-generic
  linux-image-extra-3.13.0-45-generic linux-image-extra-3.13.0-46-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sysop@1404mini:~$

bk
sysop@1404mini:~$ apt-mark showauto ^linux-image-
linux-image-3.13.0-45-generic
linux-image-3.13.0-46-generic
linux-image-3.13.0-48-generic
linux-image-3.13.0-49-generic
linux-image-extra-3.13.0-45-generic
linux-image-extra-3.13.0-46-generic
linux-image-extra-3.13.0-48-generic
linux-image-extra-3.13.0-49-generic
linux-image-generic
sysop@1404mini:~$ 

```
I do know that if I were to run "autoremove" the -45 and -46 kernels would be removed. 

No idea why you do not have the -45 kernel installed .

It is past my reliable thinkability here now, will pick this back up when I get my chores done tomorrow ( got to go get parts and repair the land mower ) . Take a fresh look at this and see what can be fingered out.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-04-12
Grasping at straws...what's the output of:
```
apt-mark showauto | grep linux
apt-mark showmanual | grep linux
```

For example, mine:
```
$ apt-mark showauto | grep linux
libselinux1:i386
[B]linux-headers-3.16.0-33
linux-headers-3.16.0-33-generic
linux-headers-3.16.0-34
linux-headers-3.16.0-34-generic
linux-headers-generic
linux-image-3.16.0-33-generic
linux-image-3.16.0-34-generic
linux-image-extra-3.16.0-33-generic
linux-image-extra-3.16.0-34-generic
linux-image-generic
linux-signed-image-3.16.0-33-generic
linux-signed-image-3.16.0-34-generic
linux-signed-image-generic
[/B]qtcreator-plugin-remotelinux

$ apt-mark showmanual | grep linux
libselinux1
linux-firmware
linux-generic
linux-libc-dev
linux-signed-generic
linux-sound-base
pptp-linux
syslinux
syslinux-common
syslinux-legacy
util-linux
```

---

### Post by ofnuts on 2015-04-13
```

$apt-mark showauto | grep linux
liblinux-inotify2-perl
libselinux1:i386
linux-firmware
linux-headers-3.13.0-32
linux-headers-3.13.0-32-generic
linux-headers-3.13.0-43
linux-headers-3.13.0-44
linux-headers-3.13.0-44-generic
linux-headers-3.13.0-46
linux-headers-3.13.0-46-generic
linux-headers-3.13.0-48
linux-headers-3.13.0-48-generic
linux-headers-3.13.0-49
linux-headers-3.13.0-49-generic
linux-headers-generic
linux-image-3.13.0-44-generic
linux-image-3.13.0-46-generic
linux-image-3.13.0-48-generic
linux-image-3.13.0-49-generic
linux-image-extra-3.13.0-44-generic
linux-image-extra-3.13.0-46-generic
linux-image-extra-3.13.0-48-generic
linux-image-extra-3.13.0-49-generic
linux-image-generic
linux-libc-dev

$apt-mark showmanual | grep linux
libselinux1
linux-generic
linux-headers-3.13.0-43-generic
linux-sound-base
pptp-linux
syslinux
syslinux-common
syslinux-legacy
util-linux

```

... and I'm now wondering why things from kernel 32 and 43 are still around :)

---

### Post by ian-weisser on 2015-04-13
> **ofnuts said:**
> ... and I'm now wondering why things from kernel 32 and 43 are still around 

The -43 headers package is still marked 'manual'.

Perhaps the -32 package is a dependency of something? Try --simulate removing it.

---

