---
title: "/boot too full, no encryption, 14.04 Lts"
date: 2014-12-12
forum: General Help
---

### Post by yonnie on 2014-12-12
I'm using 14.04LTS because it is the latest LTS and wine seems to actually work without a lot of trouble.

I have several computers all running 14.04LTS.  None are using encryption.  All will not update properly.  /boot is maxed out.  sudo apt-get autoremove doesn't do the job.  sudo apt-get -f install doesn't do the job.  Don't know why the standard tools aren't working, maybe that is the problem?  Maybe problem related to the pathetic Muon?  Is there a MuOFF?  And what is so wrong with using Synaptic lilke everyone else in the Linux world?

Why is the default installation making the  /boot partition so damned small (243MB) and why doesn't the updater remove the old crap?

Is there an easy way to grow the /boot partition larger without losing the contents of the other partitions?

---

### Post by Bashing-om on 2014-12-12
yonnie; Hello;


All things are not equal.

There is a bug report in this respect. Please add your voice:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

[INDENT][INDENT]open source
[INDENT][INDENT][INDENT]all in this, together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by schragge on 2014-12-12
Yes, this is a long known problem.

All kernel packages were marked as NeverAutoRemove in */etc/apt/apt.conf.d/01autoremove* in older versions of Ubuntu, that changed with [this revision]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/vivid/apt/vivid/revision/193/debian/apt.conf.autoremove#debian/apt.conf.autoremove"). The change first landed in raring (13.04), but obviously it's not enough.

The idea behind this change is that when your're installing new kernel, a postinstall script in */etc/kernel/postinst.d/* gets called that generates apt config file snippet */etc/apt/apt.conf.d/01autoremove-kernels* protecting only the currently booted, the just installed, the latest and the second-to-latest kernels from autoremoval. Usually, the kernel having just been installed is also the latest, and the currently booted kernel is the second-to-latest, so only two kernels are protected by the script. All other kernels are then teoretically free to be autoremoved with
```
sudo apt-get autoremove
```
Unfortunately, that not always works in practice as advertised. You can check what kernel packages on your system are actually marked for auto-removal with
```
apt-mark showauto ^linux-image-
```
and mark them explicitly with
```

sudo apt-mark auto ^linux-image-
sudo apt-mark manual ^linux-image-generic

```

My systems usually have the package linux-generic  installed. It depends on linux-image-generic which in turn always depends on the latest kernel. This way linux-image-generic could be kept marked for autoremoval together with all other linux-image- packages, but always stays on system as dependency of linux-generic. If neither of these packages is installed, you should mark the current kernel package as not autoremovable:
```
sudo apt-mark manual ^linux-image-`uname -r`
```
After that, old kernels could be cleaned up with
```
sudo apt-get autoremove
```

If that still doesn't work (and it probably doesn't if you have any dkms-based kernel modules installed like proprietary NVIDIA/AMD video drivers or VirtualBox), hopefully this will:
```
sudo apt-get --no-install-recommends autoremove
```

If not, try this script:
```

#!/bin/sh
# Keeping $1 kernels (two by default)

set -e
test -z "$1" && set -- 2
case $1 in *[!0-9]*) echo "Usage: $0 [number_of_kernels_to_keep]" >&2; exit 1; esac
exec sudo apt-get purge $(
      dpkg -S /boot/vmlinuz-* 2>/dev/null |
      sed -e 's/^\([^,:]*\).*/\1/' -e "/-`uname -r`$/d" | sort -rV | tail -n+$1
)

```
Even this script may not work if there are any self-compiled kernels or kernels from older Ubuntu releases remained after distro upgrade.

As last resort, you can try
```
sudo apt-get --only-upgrade purge '^linux-image-[0-9]' linux-image-`uname -r`+
```
This will remove **all** installed kernels but the currently booted.

Bear in mind that there're more packages pertaining to each kernel version than just linux-image-*. Since most of them install something under */lib/modules*, you can get a picture of what other kernel-related packages are installed on your system with
```
dpkg -S /lib/modules | sed s/:.\*//
```
Fortunately, they usually don't install files under /boot, thus being less of an issue.

---

### Post by nerdtron on 2014-12-12
> Why is the default installation making the  /boot partition so damned  small (243MB) and why doesn't the updater remove the old crap?

Is there an easy way to grow the /boot partition larger without losing the contents of the other partitions?

Old kernels are not deleted because in case you need to rollback changes you have the option to boot hte older kernels.

I'm not sure of any easy way to resize the /boot partitions. It would be better to just delete the olde kernels.

---

