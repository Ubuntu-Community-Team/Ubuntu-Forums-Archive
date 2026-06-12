---
title: "Kernel uninstall question"
date: 2013-05-30
forum: General Help
---

### Post by fr33z0n3r on 2013-05-30
I have a small /boot and need to clean some old kernels.  I have 4 kernels installed. 
  I just started to uninstall an old kernel via the Software Center and it is telling me that it _also_ needs to remove the "linux-image-generic" package.   Is this a normal package change, or should I be wary?

---

### Post by searchfgold6789 on 2013-05-30
Well, if it's saying it wants to uninstall linux-image-generic, then you likely have your current kernel version marked for removal. Unmark the kernel package of the kernel version you're currently using and leave the other 3 marked, then try again.

---

### Post by ibjsb4 on 2013-05-30
To find out which kernel your currently running, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
uname -r
```

---

### Post by fr33z0n3r on 2013-05-31
I should have been clear on this.  I definitely checked which kernel was in use, and I was deleting a different (older) one.  thoughts on that?

I think I always get asked about some file (a grub file perhaps?) when I upgrade kernels.  "Do I want to keep the original, replace, merge?"  Its possible the last time I got this prompt, I chose replace or merge.  Could that have something to do with it?

---

### Post by ibjsb4 on 2013-05-31
Linux-image-generic is the meta package and should be kept as far as Im concern.

I find [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") a easier and better way to manage kernels.  It can display all kernels (images) in one window, make it easy to pick and choose.  Example:

[ATTACH=CONFIG]243355[/ATTACH]

---

### Post by fr33z0n3r on 2013-06-01
I can see the individual packages as well.  Its just forcing me to "remove" the linux-image-generic one.  I do NOT recall having to do that previously.  Is there a historical log I can check to see if it acted this way previously?



[ATTACH=CONFIG]243377[/ATTACH]

[ATTACH=CONFIG]243375[/ATTACH]

[ATTACH=CONFIG]243376[/ATTACH]

---

### Post by fr33z0n3r on 2013-06-01
any other input on how I should proceed?

---

### Post by searchfgold6789 on 2013-06-03
Very odd, it seems as if you have found a bug in this Software Center. You should probably use Synaptic as ibjsb4 suggested, or use apt-get in the terminal:```
sudo apt-get purge linux-headers-3.8.0-19 linux-image-3.8.0-19-generic
```(it will remove any other packages linked to those, but probably not linux-image-generic)

---

### Post by fr33z0n3r on 2013-06-05
@SearchForGold6789 - Is there some way to run one of those in a manner that will simply report what changes will happen, such as the Software Center does?  So I don't just bork my system?

---

### Post by searchfgold6789 on 2013-06-05
Good call - add the -s option:```


sudo apt-get purge -s linux-headers-3.8.0-19 linux-image-3.8.0-19-generic
```

---

### Post by fr33z0n3r on 2013-06-08
Here are the results.  It appears I would be fine with doing this.  Confirmation anyone?  Based on the discrepancies noted earlier.

```

s@:~$ sudo apt-get purge -s linux-headers-3.8.0-19 linux-image-3.8.0-19-generic
[sudo] password for s: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.8.0-19* linux-headers-3.8.0-19-generic*
  linux-image-3.8.0-19-generic* linux-image-extra-3.8.0-19-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Purg linux-headers-3.8.0-19-generic [3.8.0-19.30]
Purg linux-headers-3.8.0-19 [3.8.0-19.30]
Purg linux-image-extra-3.8.0-19-generic [3.8.0-19.30]
Purg linux-image-3.8.0-19-generic [3.8.0-19.30]
```

---

### Post by searchfgold6789 on 2013-06-08
It looks like you're good to go. Just remove the -s option and run the command again.
You could look at [Ubuntu Tweak]("http://ubuntu-tweak.com/"). It has a tool to greatly simplify the process. All you have to do is open the program, run the tool, and your extra kernels will be deleted.

---

### Post by fr33z0n3r on 2013-06-08
Thanks for the help!    Looks like there may be a reason for this issue.  I don't understand it too well though.  Virtualbox was associated with this kernel?  I guess because I never ran it after updating my kernel?

I have uninstalled both virtualbox apps I found  - both named virtualbox.


```
user@host:~$ sudo apt-get purge  linux-headers-3.8.0-19 linux-image-3.8.0-19-generic
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.8.0-19* linux-headers-3.8.0-19-generic*
  linux-image-3.8.0-19-generic* linux-image-extra-3.8.0-19-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 195 MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 396220 files and directories currently installed.)
Removing linux-headers-3.8.0-19-generic ...
Removing linux-headers-3.8.0-19 ...
Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Removing linux-image-3.8.0-19-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
dkms: removing: virtualbox 4.2.10 (3.8.0-19-generic) (i686)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.2.10
Kernel:  3.8.0-19-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-19-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic


```

---

### Post by searchfgold6789 on 2013-06-10
The reason you're seeing that is the VirtualBox program actually needs to install a kernel module for itself. DKMS is a program that handles the insertion and removal of kernel modules such as the Virtualbox ones when kernels are installed or removed.
The reason for the trouble you were having with the Software Center, though, is that it's just a buggy program. I see several complaints from confused users about this software every week online. Many opt for the more simple and reliable Synaptic, I just use the command line.

---

