---
title: "Can't boot from USB. Grub rescue."
date: 2015-01-12
forum: General Help
---

### Post by markus21 on 2015-01-12
So i had Linux installed on my Windows 8.1, but had some space problem so had to get rid of the Linux partition. Unpatient as i was, i just deleted the partition with Linux. Now i can't boot into windows, i just get sent to grub rescue. I've tried booting both a windows and a linux iso from usb with no luck. (just get to the grub rescue window)
Is there a way to get off all this stuff and just start all over again, please? I really need help and have no idea what i'm doing..

---

### Post by yancek on 2015-01-12
You can easily repair it with your windows installation medium, the CD or DVD you used to install.  There should be a repair option similar to the windows 7 below.

[http://www.askvg.com/how-to-remove-linux-boot-loader-from-startup-after-deleting-linux-partition-on-a-dual-boot-system/](http://www.askvg.com/how-to-remove-linux-boot-loader-from-startup-after-deleting-linux-partition-on-a-dual-boot-system/)

You could try the bootrepair option explained in the link below.  If you have UEFI booting which is probably the case with windows8, this might work.  The windows DVD would be the best option.

[http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader](http://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader)

---

### Post by markus21 on 2015-01-12
Thank you for quick response.
I forgot to mention that i don't have an optical drive. Is there no way to force my computer into booting the usb drive? Seems weird that i can't install windows 8.1 from a usb drive.

---

### Post by yancek on 2015-01-12
I can't image that a computer new enough to have windows 8 installed can't boot from a usb.  Have you verified that the usb is set to first boot priority in the BIOS.  How did you create the bootable usb?  I don't use UEFI to boot so am not really familiar with it although my understanding is that there are separate boot files for windows as well as Ubuntu on an efi partition.

Are you using UEFI on the computer?  Most pre-installed windows 8 systems will use UEFI although if you installed it yourself it might not.  If you were booting both from Grub, you do know that almost all the files for Grub are on the Linux/Ubuntu partition.  Might be best to wait for someone more knowledgeable with UEFI if you are using it.

---

