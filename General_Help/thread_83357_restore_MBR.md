---
title: "restore MBR?"
date: 2005-10-28
forum: General Help
---

### Post by BoHu on 2005-10-28
I am dual booting Win2K and Ubuntu using grub. I want to erase Ubuntu and recover the hard drive space for win2k.

But erasing Ubuntu also means erasing grub. Won't that make Windows unbootable? How do I get around this?

---

### Post by Efwis on 2005-10-28
[QUOTE=BoHu]I am dual booting Win2K and Ubuntu using grub. I want to erase Ubuntu and recover the hard drive space for win2k.

But erasing Ubuntu also means erasing grub. Won't that make Windows unbootable? How do I get around this?[/QUOTE]
I may be wrong on this, so someone please correct me if I am, but I think its really a simple fix.


I recommend doing this step first in case you have to fix the MBR. Make a boot disk and make sure your boot disk has Fdisk on it
If the your boot disk doesn't have fdisk then go to [Bootdisk.com](http://www.bootdisk.com) and download a copy of the Windows 98 boot disk.
[color=red]**NOTE:** Make sure you do not get the OEM version.[/color]
then do the following:
erase your Ubuntu partition like you want.

Reboot and see if Windows loads correctly. If it does, the next step is to regain that space that was used by Ubuntu.

If you can't  boot to Windows:

[list]
[*]start the computer with the boot disk and go to your command prompt
[*]type the following at the command prompt and hit enter[/list]

```
fdisk /MBR
```

please note the space between the "k" and the "/"
then reboot your computer normally and reclaim the space that was previously used by Ubuntu.



hope this helps.

---

### Post by BoHu on 2005-10-29
so fdisk /MBR will write a new master boot record?

---

### Post by RayH on 2005-10-29
That should do it.  I had a PIII system that I installed Ubuntu 5.10 on and then wanted to install XP Home instead for my wife.  I did the XP home install but when I rebooted I still got the grub boot loader.  I booted to a boot disk, ran fdisk /mbr and rebooted and XP came right up.

---

### Post by Moloko on 2005-10-29
[QUOTE=BoHu]so fdisk /MBR will write a new master boot record?[/QUOTE]

yes, another option is boot from the win2k cd and go to the "Recovery console", there is a couple of commands that are usefull:

FIXBOOT
FIXMBR

but at least "fdisk /mbr" is faster an easy.

---

### Post by Efwis on 2005-10-30
[QUOTE=Moloko]yes, another option is boot from the win2k cd and go to the "Recovery console", there is a couple of commands that are usefull:

FIXBOOT
FIXMBR

but at least "fdisk /mbr" is faster an easy.[/QUOTE]
its best to use "fidisk /mbr" because there are reported issues of the recovery consoles' "fiixboot" and "fixmbr" not working properly.

---

### Post by Moloko on 2005-10-30
[QUOTE=Efwis]its best to use "fidisk /mbr" because there are reported issues of the recovery consoles' "fiixboot" and "fixmbr" not working properly.[/QUOTE]

in my case when I tried to use fixboot and fixmbr was useless, it simply doesn't work, but in the M$ support web is the "oficial" solution :razz:

---

