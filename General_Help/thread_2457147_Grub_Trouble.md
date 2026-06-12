---
title: "Grub Trouble"
date: 2021-01-26
forum: General Help
---

### Post by Quarkrad on 2021-01-26
Installed 20.04 on one drive and win10 on another drive.  sudo update-grub gives me:

```
dad@dadubuntu:~$ sudo update-grub
[sudo] password for dad: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
Found background image: /home/dad/Documents/icons/grub.png
Found linux image: /boot/vmlinuz-5.4.0-64-generic
Found initrd image: /boot/initrd.img-5.4.0-64-generic
Found linux image: /boot/vmlinuz-5.4.0-42-generic
Found initrd image: /boot/initrd.img-5.4.0-42-generic
Adding boot menu entry for UEFI Firmware Settings
done

```

I find this a little odd in that (forgetting win10 on the other drive at the moment) the 20.04 os is not found.  How can grub not see the OS?

---

### Post by CelticWarrior on 2021-01-26
Both 5.4.0-64 and 5.4.0-42 are kernels shipped with Ubuntu 20.04. It's correct.
And the "[COLOR=#000000][FONT=&quot]Adding boot menu entry for UEFI Firmware Settings" shows it's correctly installed in UEFI mode. Have you installed Windows in UEFI mode as well?[/FONT][/COLOR]

---

### Post by oldfred on 2021-01-26
The 5.4 kernel is 20.04.

[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/lsb-release [/COLOR]
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=20.04 
DISTRIB_CODENAME=focal 
DISTRIB_DESCRIPTION="Ubuntu 20.04.1 LTS" 
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ uname -a [/COLOR]
Linux z170-focal-k 5.4.0-64-generic #72-Ubuntu SMP Fri Jan 15 10:27:54 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

There is also the enablement stack which will upgrade kernel to more recent to support newer hardware.
If 20.04 or 20.04.1 work or work well, you typically do not need enablement stack.
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

If grub is not showing Windows, did you install both Windows & Ubuntu in same boot mode.
Or both in UEFI mode or both in BIOS mode.
UEFI & BIOS are not compatible, once you start booting in one mode, you cannot switch. Or grub can only boot other installs in same boot mode.

Also Windows fast start up has to be off for grub to find Windows as that sets hibernation flag hiding the NTFS partitions.
And grub only boots working Windows, so if it needs chkdsk, grub will not boot Windows.
You often need your Windows repair/recovery flash drive if BIOS, if UEFI you may be able to directly boot from UEFI, but still best to have repair flash drive for current version of every operating system you have installed.

[/FONT]

---

