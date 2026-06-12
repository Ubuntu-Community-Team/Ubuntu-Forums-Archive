---
title: "WUBI USB Loader"
date: 2008-03-31
forum: General Help
---

### Post by Naraltd on 2008-03-31
Sorry if this has been covered before, but I can't find it via search, so I hope it hasn't.

Anyway where I work, I am not allowed to 'modify/install' anything to my laptop which would include installing WUBI.

Of course that doesn't mean I can't simply copy a few files to the hard drive..... :)

So I have installed WUBI at home and would like to use my small USB key as a boot loader for the WUBI install on my laptop.

I am able to boot into Grub4Dos, but I can't get it to find my WUBI install and start the load.  I copied the menu.lst file from the WUBI install for my Grub4Dos install.  And for the record I am using the NTLDR calling GRLDR on the USB key.

This all seems to work, but I get an error that it can't find the /ubuntu/disks/..... files to load.

Any ideas?

Thanks!
Eric

---

### Post by ago on 2008-03-31
Copy the content of /ubuntu/winboot onto the root of the usb device then put wubildr.mbr on the mbr of the usb device. I never tried that but might work. See grub4dos website for ways to modify the mbr.

Note that next versions of wubi will not allow to install if you are not an administrator (I may add a commandline flag to override that...).

---

### Post by Naraltd on 2008-03-31
I am currently booted in linux, would this work with the mbr file?

install-mbr -I wubildr.mbr -T /dev/sdc

assuming /dev/sdc is my usb key, do I need /dev/sdc1 instead?

There is 1 partition on the key.


> Note that next versions of wubi will not allow to install if you are not an administrator (I may add a commandline flag to override that...).

But using this method, I should be fine.  I have it installed on my home PC where I am the admin.  I am just wanting to copy the image files and boot from them w/o installing on my work PC.

---

### Post by ago on 2008-03-31
Something like that: [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Install_GRUB_for_DOS_boot_code_to_MBR](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Install_GRUB_for_DOS_boot_code_to_MBR)

I might be wrong, but install-MBR might be a grub only tool, you will have to use probably grubinst that comes with grub4dos. Do not remember if it takes as argument an existing mbr file. If it does not you will have ro rename wubildr -> grldr. I would assume you have to target the full device (/dev/sdc).

Let me know how it goes.

---

### Post by ago on 2008-03-31
That of course would also a good way to have a bootable wubi installation on usb/pen drive (+5GB)...

---

### Post by ago on 2008-03-31
One thing you may also want to change is to use

"find --set-root /path/to/some/wubi/file" within menu.lst as opposed to "root (hd0,0)"

That will be slightly annoying though since the relative path of kernel and initrd will be reset on grub updates...

---

### Post by Naraltd on 2008-03-31
Interesting thing I am noticing.

It appears as though the internal HD is hd1 when booting on the USB key.

I am going to look at changing the hd0 entry to hd1 and see what that gets me.

---

### Post by ago on 2008-03-31
Yeah the boot order may change from machine to machine, so if you want a really portable USB device with Wubi you will have to use:

find --set-root

That will basically set the root to the device that contains the specified file, so it goes around device order. BUT if you notice root in menu.lst also has a path suffix "/ubuntu/disks"... The root line in fact does 2 things, it selects the root device and it sets the relative path (paths in the subsequent lines are considered relative to the path in root).

Not sure if it is possible to set  a relative path using find --set-root...

See the menu.lst generated in /ubuntu/install/boot/grub/menu.lst (gets deleted after installation)

---

### Post by Naraltd on 2008-03-31
So a change to the root entry in my initial menu.lst resolved the problem.

Apparently my usb device is hd0 and the internal drive hd1 when booting from usb.

Thanks for the help!

---

### Post by ago on 2008-03-31
You might want to write a small how-to so that others might use it as well.

---

### Post by Zakhafr on 2008-10-14
Yes indeed, a small "How to" would be a great thing!

---

### Post by Zakhafr on 2008-10-15
So I made it.

Here it is:

[http://ubuntuforums.org/showpost.php?p=5966083&postcount=7]("http://ubuntuforums.org/showpost.php?p=5966083&postcount=7")

Now I have a key that serves as a *"dongle"* to boot Ubuntu.
No key inserted => boots Windows without asking anything
Key inserted + BIOS Boot menu select key => boots Ubuntu without asking.

---

