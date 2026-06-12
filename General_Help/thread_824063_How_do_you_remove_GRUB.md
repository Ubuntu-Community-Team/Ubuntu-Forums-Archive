---
title: "How do you remove GRUB?"
date: 2008-06-09
forum: General Help
---

### Post by kazoo boy on 2008-06-09
I have been dual booting Windows Vista and Ubuntu for some time now. I had it set up so that Vista was on one hard drive and Gutsy was on the other. Later, I ran into some problems and installed Kubuntu over the Ubuntu installation. Both times, GRUB worked just fine, (although to those in charge of Kubuntu, make sure the GRUB knows it's Kubuntu and not Ubuntu, it's a little easier for users). 

Today, I reformatted and thought I wiped clean the Kubuntu hard drive from within Windows, with the intent of using the extra hard drive space for virtual machines I would control from within Windows. When I reboot however, GRUB pops up and gives "error 17." How can I wipe GRUB out of my computer so I can just boot to Windows? This is rather important, because now all I can do is boot to live disk. I don't mind reinstalling Linux on the one hard drive if necessary, but I would like to save my Windows drive at least. PLEASE, help :confused:

---

### Post by tyler_roach on 2008-06-09
Download and burn the super grub disk:

[www.supergrubdisk.org](www.supergrubdisk.org)

and boot from it. It will enable you to restore the Windows bootloader to your MBR.

---

### Post by kazoo boy on 2008-06-09
Thank-you So Much!!!! Especially for your quick response. My boot is working perfectly now. It's so nice to be able to boot straight to windows and not have to worry about it. For that matter, it's nice to be able to boot at all! 

To all you other Linux newbies out there, you'll make mistakes (like me) but you do learn something and it can be quite an adventure! Keep persevering! 

Keep up the good work on the forums,
     -kazoo boy

---

### Post by atoponce on 2008-06-09
It's important to understand the nature of master boot records, or MBRs.  They are installed within the first 512 bytes of your disk, regardless of operating system.  When you installed Ubuntu, you overwrote the Windows MBR with GRUB.  Removing your Ubuntu installation doesn't affect the MBR at all, still keeping it in place.  GRUB is a perfectly good MBR for booting Windows, and there really is no need to remove it, unless you don't like the lack of integration.

The best way to restore the MS-DOS or Windows MBR, is to boot off of an Ubuntu Live CD then install the package ms-sys:

```
sudo aptitude install ms-sys
```Lastly, run the following command on the disk or partition where your MBR resides.  In this case, it would be /dev/sda.  Change as appropriate:

```
sudo ms-sys -m /dev/sda
```You should now be able to use the Windos MBR to boot your Windows machine, rather than GRUB.  Again though, GRUB is a perfectly good bootloader for booting Windows, and you can configure it to lauch Windows automatically, fast enough that you never see the GRUB boot menu.

EDIT:  I actually surprised myself, when I saw that ms-sys was no longer in 8.04.  Come to find out, the ms-sys package was removed from Debian Sid due to copyright infringement, and thus, removed from Ubuntu.  In this case, you can boot from a Windows boot disk, and fix your MBR in that manner.  I have no experience with this, however.

---

### Post by AndyCee on 2009-01-06
Old post, I know, but it seems a package to replace ms-sys exists called "mbr".

Enable universe repository, then

Update the repository cache
```
sudo apt-get update
```

Get the 'mbr' package
```
apt-get install mbr
```

Run the program
```
install-mbr /dev/sda
```

There are other options supported, but this is the default. Of course change /dev/sda if that's not the disk where the MBR is located.

---

