---
title: "Ubuntu 12.04 Refusing to Boot"
date: 2013-01-22
forum: General Help
---

### Post by Spite.FU on 2013-01-22
I have a PC with Duo-Core 2.4GHz processor (32bit) which I dual boot with Windows. Up until this month this has worked fine for many years with various versions of Ubuntu and Windows XP Home. Earlier this month I took the opportunity to upgrade XP to Windows 8 Pro and still everything was fine with Ubuntu 12.04 LTS.

Yesterday my son informed me that Ubuntu would not boot. It hangs forever on the Ubuntu Boot Screen. The dots cycle ad infinitum.

I booted to recovery mode which brought up the recovery menu as it should. If I try to boot into a safe graphics mode I get the following scrolling text. The same thing happens if I try to use clean, dpkg, failsafex, grub and enable networking options, except drop into a root prompt.

```
/lib/recovery-mode/recovery-menu: line 109: /lib/recovery-mode/options//lib/recovery-mode/recovery-menu:: No such file or directory
usr/bin/gettext.sh: line 90 /usr/bin/gettext: Permission denied
usr/bin/gettext.sh: line 90 /usr/bin/envsubst: Permission denied
usr/bin/gettext.sh: line 90 /usr/bin/envsubst: Permission denied
usr/bin/gettext.sh: line 90 /usr/bin/gettext: Permission denied
usr/bin/gettext.sh: line 90 /usr/bin/envsubst: Permission denied
usr/bin/gettext.sh: line 90 /usr/bin/envsubst: Permission denied
```

The only way around this is a reset boot.
The issue appears to be a file system mount issue, possibly.

If I continue to Resume a Normal Boot I get the following text:

```
fsck from util-linux 2.20.1
dev/sda6: clean, 831900/14721024 files, 44271692/58859008 blocks
mountall: mount / [1300]: Permission denied
udevd[1299]: failed to execute 'sbin/blkid' 'sbin/blkid -o udev -p /dev/dm-0': Permission denied
udevd[1303]: failed to execute '/lib/udev/udisks-dm-export' 'udisks-dm-export 252 0': Permission denied
udevd[1307]: failed to execute '/lib/udev/udisks-part-id' 'udisks-part-id /dev/cm-0': Permission denied
```

The above happens whichever old kernel I use too.

The main/current kernel is 3.2.0-35-lowlatency-pae. I have the previous kernels, all pae but not all lowlatency.

If I can get this fixed via the root shell prompt it would be preferential to having to do a complete reinstall at this stage.

---

### Post by mikodo on 2013-01-22
Have you read about using [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")? 

I haven't used it, but maybe you can look into trying it.

;p

---

### Post by xycris on 2013-01-22
Hi guys,

The Ubuntu installer 12++ has the ability to repair the system problem. The installer will automatically detect if there are any Ubuntu installed and if the installer and the installed Ubuntu are the same version then more likely it will give a system repair option.

Hope this helps.

---

### Post by Spite.FU on 2013-01-23
> The Ubuntu installer 12++ has the ability to repair the system problem. The installer will automatically detect if there are any Ubuntu installed and if the installer and the installed Ubuntu are the same version then more likely it will give a system repair option.

I created a bootable start-up flash drive using 12.04 LTS.
No option for repair was available.

I can back up all my existing Home files and reinstall but obviously I'd rather avoid having to do this if I can fix it from the root prompt in recovery.

---

