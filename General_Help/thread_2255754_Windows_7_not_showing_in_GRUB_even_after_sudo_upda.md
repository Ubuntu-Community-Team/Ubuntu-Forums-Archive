---
title: "Windows 7 not showing in GRUB even after sudo update-grub"
date: 2014-12-07
forum: General Help
---

### Post by Sagar_Patil on 2014-12-07
Please help me. I have no idea what to do. 

I was on Windows 7 10 minutes ago and I saw a partition with only 200 MB. So I decided to format it. After formatting, I restarted my laptop and now I cannot see windows 7 in the bootloader. I can access all the C drive from ubuntu but cannot boot into windows 7. I have tried sudo update-grub but no success. 

```

Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.Found linux image: /boot/vmlinuz-3.16.0-25-generic
Found initrd image: /boot/initrd.img-3.16.0-25-generic
Found linux image: /boot/vmlinuz-3.16.0-24-generic
Found initrd image: /boot/initrd.img-3.16.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda4
done

```

---

### Post by nerdtron on 2014-12-07
> was on Windows 7 10 minutes ago and I saw a partition with only 200 MB. So I decided to format it.

Basically that's the problem. This is where windows stores it boot files. I don't why you format it (it is not an empty right?) or how to restore it. But I'm sure that partition is used to boot windows.

---

### Post by Sagar_Patil on 2014-12-07
So is there anyway to fix it?

---

### Post by nerdtron on 2014-12-07
Let's wait for others to answer as I don't know. At least you data in windows 7 is still intact. It's just that it won't boot.

---

### Post by Mark Phelps on 2014-12-07
> **Sagar_Patil said:**
> So is there anyway to fix it?

You would have to do a Win7 repair -- which you could have done easily when you could boot into Win7.  But now you can't, you will need to go to the link, purchase the image needed, download the appropriate Win7 ISO file, burn that to CD, boot from the CD -- and run  Startup Repair three times, that's right, three times: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by dragonfly41 on 2014-12-07
Depending on how you chose to format that Windows boot partition it might be possible to restore.

Investigate use of testdisk to restore .. but remember that you formatted from Windows and not Ubuntu.

You _might_ have to restore the partition by physically removing the internal drive from your laptop and putting it in a USB container to be restored as an external drive by another Windows laptop.

---

### Post by nerdtron on 2014-12-07
HHHmm I think you can boot into a windows 7 DVD or bootable USB, choose Repair windows, and choose startup repair.
If it is successful you'll be able to boot windows 7, but GRUB will be erased. Not 100% here

---

### Post by Sagar_Patil on 2014-12-07
Tried that didn't work.

---

### Post by oldfred on 2014-12-07
Tried What? You need to tell us details, so better suggestions can be made.

Test disk may be able to recover files with deeper search, but you have to make sure partition is NTFS with boot flag.
Does main Windows install have bootmgr? if only BCD is missing you can use third party tools to rebuild it. But then you have to have boot flag on main install NTFS partition. It needs both bootmgr & BCD file to be bootable.

If you have access to another Windows 7 system you can make the repair disk for free, otherwise it can be expensive to get that.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

