---
title: "Missing windows in boot after updating kernel"
date: 2018-10-15
forum: General Help
---

### Post by vidovic-slobodan on 2018-10-15
Hi guys,
I'v updated my ubunutu machine to a newer kernel and after that Im missing boot option for win 7.
I tried doing

```
sudo update-grub
```

but still Im missing win7 option. You can find Boot Info Script log on pastebin
```

:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-137-generic
Found initrd image: /boot/initrd.img-4.4.0-137-generic
Found linux image: /boot/vmlinuz-4.4.0-134-generic
Found initrd image: /boot/initrd.img-4.4.0-134-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

[https://pastebin.com/f2GSi1n1](https://pastebin.com/f2GSi1n1)

---

### Post by oldfred on 2018-10-15
You should install a Windows boot loader to sda, and grub boot loader to sdb and set sdb to default boot in BIOS.
But grub only boots working Windows, so if Windows has issues like needing chkdsk or is hibernated then you may be able to directly boot from sda to get to f8 recovery console. But still better to have Windows repair disk.

When grub output says partition 97 that is saying it is not correctly installed.
I would use Boot-Repair's advanced mode and totally uninstall & reinstall grub to sdb.

I would remove grub4dos. Is that from EasyBCD? With two drives & two MBRs, you do not need EasyBCD & grub4dos.

---

### Post by vidovic-slobodan on 2018-10-16
I dont know from where I got grub4dos and EasyBCD I did not installed them, so I need to do win7 repair MBR ? I never used BootRepair is that boot cd or what ?

---

### Post by yancek on 2018-10-16
>  I never used BootRepair is that boot cd or what ? 		

You can download boot repair from the site below.  Best to use the 2nd option to install using ppa as explained at the site and thoroughly read the instructions before beginning and if you don't understand something, post a question here before doing anything which could just make things worse.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vidovic-slobodan on 2018-10-27
> **yancek said:**
> You can download boot repair from the site below.  Best to use the 2nd option to install using ppa as explained at the site and thoroughly read the instructions before beginning and if you don't understand something, post a question here before doing anything which could just make things worse.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Ok here it is [URL="http://paste.ubuntu.com/p/mhzpK3r35Q/"]http://paste.ubuntu.com/p/mhzpK3r35Q/ but it did not helped
[/URL]

---

### Post by oldfred on 2018-10-27
See post #2.
Grub only boots working Windows.
And since you have two drives, you want Windows boot loader in Windows drive and grub only in Ubuntu drive.
Do not run Boot-Repair autofix as that installs grub to every MBR, you want Windows boot loader in sda.

If in Boot-Repair's advanced mode, you cannot choose the Windows install and a "Windows" type boot loader to MBR of sda, then you will probably need a Windows repair disk. You also may be able to manually install a Windows type boot loader from Ubuntu.

---

