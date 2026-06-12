---
title: "XP boot doesn't show up as an option"
date: 2007-07-10
forum: General Help
---

### Post by StephanGFX on 2007-07-10
Once again, I'm back because of a problem I'm having. I followed a tutorial, and successfully installed ubuntu. I want to make it so XP boots as default, but it's not letting me. In the grub boot menu, all I have is 4 ways to boot ubuntu and another way that lets me boot ubuntu memtest. This is what they told me to do:

[B]Configure GRUB

If you want to modify how GRUB handles the new dualbooting environment, you need to edit the boot menu. Boot into Ubuntu and open up a Terminal window (Applications, Accessories, Terminal), and type in:

sudo gedit /boot/grub/menu.lst

Dualboot - Configure Boot MenuDualboot - Configure Boot Menu

This opens up the boot menu as a text file in gedit.

Dualboot - Boot OptionsDualboot - Boot Options

There are loads of options you can change, but only a couple that you&#8217;re likely to be interested in. The default boot entry is defined by the &#8220;default&#8221; value.

The default value is 0, which means that the first entry in the list (which is Ubuntu) always gets loaded.

If you want to make it so that Windows XP loads by default, change the value to 4, as XP is the fifth item in the list (the numbering system starts at 0).

The other way to load Windows XP by default is to change the value for &#8220;default&#8221; from a numerical value to &#8220;saved&#8221;. Then, GRUB will load whichever boot entry has been marked with &#8220;savedefault&#8221;.

If you scroll down the list and have a look at the entries, you&#8217;ll notice that both the main Ubuntu entry and Windows XP have been marked with &#8220;savedefault&#8221;. Remove the value for Ubuntu and Windows XP will launch by default.

You can also increase the boot menu timeout &#8211; just change the value for &#8220;timeout&#8221;. You can also hide the GRUB boot menu by removing the hash in front of &#8220;hiddenmenu&#8221;. Save and exit gedit to keep any changes.

And that&#8217;s about it. Dualbooting Windows XP and Linux when Windows is installed first is by far the easiest method of dualbooting, because most up-to-date Linux distros are very aware and accommodating of other operating systems, and GRUB is an excellent and highly flexible bootloader.[/B]

I put in 4 as the default value, and It didn't boot xp, it booted ubuntu memtest. XP isn't even an option in my grub menu. Any help? :confused:

heres a link to the tutorial: 
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by StephanGFX on 2007-07-10
*bump* (I really need help)

---

### Post by jespdj on 2007-07-10
Normally when you install Ubuntu on a new partition and you already have Windows XP on another partition on your harddisk, it should automatically have added Windows XP to the GRUB boot menu. You did not delete your Windows XP partition during installation, did you? Can you access your Windows partition from Ubuntu (there should be a directory in /media which links to your Windows partition)?

What do you see if you type in the command "sudo fdisk -l" in a terminal? You should see your Windows XP partition, this is for example what I get:
```
jesper@jesper-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31871   256003776    7  HPFS/NTFS
/dev/sda2           37918       38913     8000370   82  Linux swap / Solaris
/dev/sda3           31872       37917    48564495   83  Linux

Partition table entries are not in disk order
```
Partition /dev/sda1 (HPFS/NTFS) is my Windows XP partition.

If you don't see it, then you most likely deleted it during the installation of Ubuntu.

---

### Post by StephanGFX on 2007-07-10
wtf i get this:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

and i followed the tutorial and it said that i wouldn't lose windows xp. It would just use the leftover space I had to put ubuntu.

so what can i do to get xp back?

---

### Post by StephanGFX on 2007-07-10
grrr...bump

---

### Post by jespdj on 2007-07-10
So your Windows XP partition and all the data on it is gone. The only thing you can do is make some space on your harddisk (make a new partition for Windows) and re-install it. :cry:

---

### Post by StephanGFX on 2007-07-10
so how do i make a new partition>?

---

### Post by jespdj on 2007-07-10
You can manage partitions with gparted. You need to start it with root privileges: sudo gparted

---

