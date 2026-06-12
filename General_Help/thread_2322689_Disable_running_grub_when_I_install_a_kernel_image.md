---
title: "Disable running grub when I install a kernel image"
date: 2016-04-29
forum: General Help
---

### Post by aerojockey on 2016-04-29
Is there a documented, official way to do this, that isn't a hack?

I have a weird setup tetral-boot setup (3 linux, one windows), and I've found that it's entirely hopeless to get the linux image packages to not completely destroy the boot setup; in fact for some reason the linux image updates end up making the system unbootable.  That's probably because of some obscure thing I'm doing, but whatever.

I have my own script that I can run to recreate the correct boot setup.  Problem is, if I forget to run it after upgrading the kernel, system doesn't boot.  I want to stop the linux image packages from running grub so at least the system will be able to boot into the old kernel if I forget to run the script.

I looked at the postinst script for the linux image package, and it's some awful Perl code.  As best as I can tell, it looks like if I add a line "do_boot_enable=no" to the file /etc/kernel-img.conf it will disable running grub, but the code is so unfollowable I'm not sure that's actually the case.  Plus, it's undocumented, so heaven knows if somebody down the line is going to conveniently remove it because nobody ever doesn't want the linux image to run grub for you.

I will just mention, parentheically, that applying Windows 7 updates never clobbers the boot setup for the other systems, like these Linux packages do.  (All bets off for Windows 10, though.)

---

### Post by Bashing-om on 2016-04-29
aerojockey; Hello;

As you know there can be but one boot authority per hard drive.
I also multi-boot and my solution to keep grub from being trashed from other installs is to disable the execution of /etc/grub.d/30_os-prober in all but my primary booting system. ( I also do a no-no in installing boot code to the booting partition in some installs ) .
This arrangement works well for my use case . It does require that I stay on top of grub and update the primary when any change is made to any of the other installs . - that sometimes catches me short when I fail to take this into consideration.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-04-29
If grub is not updated when a new kernel has been installed then the system will not load into the new kernel at the next restart. If the kernel update is a security patch as they usually are, then we would be running on a vulnerable operating system.

Actually, update-grub is a script that calls grub-mkconfig. You can find the script at /usr/sbin/update-grub. Open the script in a text editor and you will see that the script contains this

> #!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

If you make the script non-executable then that should stop the Grub configuration file (grub.cfg) being updated. Then I guess, when you want to update the Grub boot menu to take into account newer kernels you run at a time of your choosing

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

I have never tired that. But there you are. 2 suggestions for what they are worth.

Regards

---

### Post by QDR06VV9 on 2016-04-29
> **grahammechanical said:**
> If grub is not updated when a new kernel has been installed then the system will not load into the new kernel at the next restart. If the kernel update is a security patch as they usually are, then we would be running on a vulnerable operating system.

Actually, update-grub is a script that calls grub-mkconfig. You can find the script at /usr/sbin/update-grub. Open the script in a text editor and you will see that the script contains this



If you make the script non-executable then that should stop the Grub configuration file (grub.cfg) being updated. Then I guess, when you want to update the Grub boot menu to take into account newer kernels you run at a time of your choosing

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

I have never tired that. But there you are. 2 suggestions for what they are worth.

Regards
+1 
On Arch "sudo grub-mkconfig -o /boot/grub/grub.cfg" is the command they use as default.
"sudo update-grub" dose nothing on Arch :eek:
```
$ sudo grub-mkconfig -o /boot/grub/grub.cfg
[sudo] password for rick: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-linux
Found initrd image: /boot/initramfs-linux.img
Found fallback initramfs image: /boot/initramfs-linux-fallback.img
done
[rick@Silversurfer ~]$ sudo update-grub
sudo: update-grub: command not found


```
Sorry Off topic! :grin:

---

### Post by Dennis N on 2016-04-29
I currently have several operating systems on this one computer (including non-Ubuntu based), and I have a permanent maintainance-free grub setup by using custom menu entries at the head of my grub menu. I never need to edit anything with these. I just followed this guide:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

including the last part where it describes "Maintainance-Free Menu Entries". You can also disable the os_prober to prevent the regular update-grub generated stuff. 

You should look into it.

---

### Post by Bashing-om on 2016-04-29
> **Dennis N said:**
> I currently have several operating systems on this one computer (including non-Ubuntu based), and I have a permanent maintainance-free grub setup by using custom menu entries at the head of my grub menu. I never need to edit anything with these. I just followed this guide:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

including the last part where it describes "Maintainance-Free Menu Entries". You can also disable the os_prober to prevent the regular update-grub generated stuff. 

You should look into it.

+1 ! I have also used cavsfan's development and attest it works well !

[INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT]

---

### Post by oldfred on 2016-04-29
With Ubuntu you can install and not install grub.

 This launches the installer program (Ubiquity) with an option (-b) to not install a boot loader from live installer in live mode:
In the Terminal window, type ubiquity -b.  

I normally installed grub to another drive, as default is always sda, but when using BIOS, my default was sdd or sde.

But with UEFI it always installs to sda, even when you tell it to install to sdb. But I just backup efi partition or really the grub.cfg in the /EFI/ubuntu folder.

Windows since at least Windows 7 on major upgrades/install resets partition table. And since Windows does not correct see Linux partitions it leaves off the logical Linux partitions with BIOS/MBR installs. Many with upgrades to Windows 10 have needed testdisk or parted rescue to restore missing partition entry in partition table. Or they reinstalled.

---

