---
title: "Dual boot, backing up Windows partition"
date: 2012-12-01
forum: General Help
---

### Post by daKoolaid on 2012-12-01
I'd like to back up the Windows partition of a dual boot Windows 7 and Ubuntu install.

I don't have a problem with using dd, but what about compressing the whole partition into a tarball? Has anyone done this who can confirm it would restore and boot correctly? 

I'm not using this on the bootloader, just the Windows partition.

---

### Post by coffeecat on 2012-12-01
I'd suggest simply using a Windows imaging application. If you don't want a paid-for application, Macrium Reflect do a free version which works very well for what you want. With Macrium you create a compressed image from within Windows and a (Linux-based!) bootable rescue CD if you need to restore an image. More here:

[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

That's free as in beer, but not open source, of course.

I very much doubt a standard tarball would work if you mean a tarball of all the files on the NTFS filesystem.

---

### Post by daKoolaid on 2012-12-01
> **coffeecat said:**
> I'd suggest simply using a Windows imaging application. If you don't want a paid-for application, Macrium Reflect do a free version which works very well for what you want. With Macrium you create a compressed image from within Windows and a (Linux-based!) bootable rescue CD if you need to restore an image. More here:

[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

That's free as in beer, but not open source, of course.

I very much doubt a standard tarball would work if you mean a tarball of all the files on the NTFS filesystem.

I was thinking Duplicity may be alright too but I'm also doubting tar would work. I haven't tried it, though.

I actually forgot about the built in Windows imaging. If I restore that through Windows in a multi boot computer, would it write over Grub? I would imagine so, and then Ubuntu would need a reinstall. I guess that wouldn't be too bad.

I just want to take snapshots of the installed systems so the computer's owner can restore them as easily as possible from an external drive.

---

### Post by coffeecat on 2012-12-01
> **daKoolaid said:**
> 
I actually forgot about the built in Windows imaging. If I restore that through Windows in a multi boot computer, would it write over Grub? I would imagine so, and then Ubuntu would need a reinstall. I guess that wouldn't be too bad.

It's not actually built in to Windows - you have to install Macrium, or one of the paid-for alternatives such as Acronis True Image.

You can restore an image without overwriting the mbr, although if I remember correctly you can opt to rewrite the mbr or not with Macrium as the case may be. So you don't have to reinstall grub. And, no, you certainly wouldn't have to re-install Ubuntu - that would be totally unnecessary. All we are talking about is the first 440 bytes of the hard drive (in an mbr partition table system). If the imaging app were to overwrite the 440 bytes of grub code there with the Windows mbr, it is trivially easy to reinstall grub to the mbr with a live CD.

Things are a bit more complicated with a UEFI system and a GUID partition table (GPT), but you'd know if you had that when you setup the dual-boot.

---

### Post by sgage on 2012-12-02
> **coffeecat said:**
> It's not actually built in to Windows - you have to install Macrium, or one of the paid-for alternatives such as Acronis True Image.

You can restore an image without overwriting the mbr, although if I remember correctly you can opt to rewrite the mbr or not with Macrium as the case may be. So you don't have to reinstall grub. And, no, you certainly wouldn't have to re-install Ubuntu - that would be totally unnecessary. All we are talking about is the first 440 bytes of the hard drive (in an mbr partition table system). If the imaging app were to overwrite the 440 bytes of grub code there with the Windows mbr, it is trivially easy to reinstall grub to the mbr with a live CD.

Things are a bit more complicated with a UEFI system and a GUID partition table (GPT), but you'd know if you had that when you setup the dual-boot.

There is indeed a built-in system image feature in Windows - you do not need a 3rd party program. 

If restoring the Windows image overwrites grub in the MBR, you can simply boot to a LiveCD of Ubuntu and chmod to the Ubuntu install, and run grub-install/update-grub. I need to do this from time to time - not hard to do.

I have been dual booting for years, and typically keep Windows in control of the MBR. At install time, I tell Ubuntu to put grub on /dev/sdax, where x is the installation partition. Then I use EasyBCD (in Windows) to add a boot menu item for Linux.

I keep Windows in the MBR only because Windows won't hibernate if it's not in control there.

---

### Post by daKoolaid on 2012-12-02
Great. Thanks guys.

---

