---
title: "Removing options in GRUB boot loader?"
date: 2015-09-27
forum: General Help
---

### Post by jjmgray on 2015-09-27
Originally I had two options in my boot loader: Ubuntu and Windows.
However, after updating my BIOS I had to repair my boot loader. After doing so there are now a lot more options in the boot loader--mokmanager.efi I think and some other things.
It's not a big deal, but it is kind of annoying to have to click around so much between the only two options I use. 

How do I remove the extra options in the GRUB boot loader?

---

### Post by Dennis N on 2015-09-27
I would copy the menuentries I wanted from grub.cfg to create a custom grub menu. The directions to making a grub menu with your selected entries (and eliminating others) is here:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by ajgreeny on 2015-09-27
Are you sure this is a grub menu and not the UEFI menu that appears on many new systems that use UEFI instead of legacy BIOS?  It sounds as if your problem is exactly the same as the one I am already discussing at [http://ubuntuforums.org/showthread.php?t=2296623&p=13363627#post13363627](http://ubuntuforums.org/showthread.php?t=2296623&p=13363627#post13363627).

Have a look at that thread and see if it is the same problem.  Hopefully when a proper answer arrives for that thread, it might also give you a solution to your problem.

The same picture of the menu you see would be helpful, as well as the output of command ```
ls /boot | grep vmlinuz
```

---

### Post by Dennis N on 2015-09-27
ajgreeny, you may be right. If jimgray doesn't really mean Grub boot loader, then extra entries can easily be deleted from the UEFI boot manager with the EFI boot manager tool (efibootmgr). 

[http://linux.dell.com/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt](http://linux.dell.com/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt)

See "typical usage" and Example #5 for deleting entry example.

---

### Post by jjmgray on 2015-09-30
[I just took a picture of the monitor since it was quicker.]("http://imgur.com/46no6Wv")

---

### Post by oldfred on 2015-09-30
It looks like Boot-Repair added extra entries.
Usually if Boot-Repair adds entries they are in 25_custom. You can back that up and edit or turn off its use.

You will want whichever Windows entry works, of course the Ubuntu entires. And good to have system setup in case you have issues getting into UEFI.

       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

 sudo nano /etc/grub.d/25_custom
Then do:
sudo update-grub

If you do not want any from 25_custom turn off execute bit.
      
 sudo chmod a-x /etc/grub.d/25_custom

You also can just add only the entries you want to the 40_custom and turn off grub2's os-prober.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

