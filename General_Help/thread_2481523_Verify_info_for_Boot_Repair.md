---
title: "Verify info for Boot Repair"
date: 2022-12-01
forum: General Help
---

### Post by philipb2 on 2022-12-01
Hi, 
I have an Ubuntu 18 system. It used to boot to the GUI but now lands on the Grub command line. (I can get to the GUI from there however).  All this began after installing Ubuntu 20 on a flash drive using same system. 

I'd like to invoke the Boot Repair utility to get the Ubuntu 18 system back to normal. I'm somewhat new to this - can any of you verify the 'report' text file from the utility before I pull the trigger?

You can find the report here:
[http://paste.ubuntu.com/p/3b5X4GGpMC/](http://paste.ubuntu.com/p/3b5X4GGpMC/)

Thanks!

---

### Post by grahammechanical on 2022-12-01
The Boot Repair recommended repair is the standard repair that Boot Repair does. I see nothing harmful in it. You can try something else before trying that. You say that you can get to a Ubuntu desktop. So. open a terminal and run this command.

```
sudo update-grub
```

And see what printout you get and if it solves the problem. We get a Grub command line when Grub cannot find its configuration file (grub.cfg) in /boot/grub/ or if something else is missing. Such as a Linux kernel. Or if the fstab (file system table) is messed up. 

What do you do at the Grub command line to get to the GUI?

Regards

---

### Post by oldfred on 2022-12-01
You did not run report with external drive plugged in.
see line 116, it is looking for an UUID that is not elsewhere in report. I bet it is your flash drive.

You were bit by this very old bug that they do not fix.
Ubuntu's Ubiquity only installs grub boot loader to first drive's ESP.

You need an ESP on external drive and then a work around. Several posted in bug report.
If you have ESP on external drive, you just need to reinstall grub using Boot-Repair's advanced mode.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by philipb2 on 2022-12-03
All, thanks for the responses. 
sudo update-grub did not help, but for posterity here is its output:

user@tct240:~$ sudo update-grub
[sudo] password for user: 
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-197-generic
Found initrd image: /boot/initrd.img-4.15.0-197-generic
Found linux image: /boot/vmlinuz-4.15.0-163-generic
Found initrd image: /boot/initrd.img-4.15.0-163-generic
Adding boot menu entry for EFI firmware configuration
done

** Fortunately!  The boot-repair utility was able to fix the problem (though I had to run it off a preview ISO on a flash drive). Appreciate the help.

---

