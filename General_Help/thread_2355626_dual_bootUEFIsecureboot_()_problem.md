---
title: "dual boot/UEFI/secureboot (?) problem"
date: 2017-03-14
forum: General Help
---

### Post by Faoldorcha on 2017-03-14
I hope this is the correct board to post this question, if not feel free to transfer it to the relevant one.

I've been using ubuntu for quite a while now (currently 16.04), on a laptop with dual boot windows 10/ubuntu.
I recently tried to install virtualbox on the ubuntu system, and while installing, i was prompted to disable secure boot. I did what was asked.

When I next booted the system, I was greeted with the UEFI screen (but only this time, I guess I accidently pressed F2 during startup...), and since then, the PC automatically boots on the windows 10 system.

I tried activating/deactivating secureboot from BIOS, nothing.

I booted on a liveusb (without any problem) to run boot-repair, to no avail. Here is the diagnostic from boot-repair:
[URL="http://paste2.org/0dsU6p3J"]http://paste2.org/0dsU6p3J
[/URL]I can't see anything wrong with it, so I guess the problem comes from somewhere else, but I must admit that I have no clue where.
(If it is any help, the "grub location" tab in boot-repair>advanced is greyed out, which seems weird???)

Any help is welcome!

Thanks!

---

### Post by oldfred on 2017-03-14
You show UEFI secure boot on, have you tried it with it off?

But main problem is probably that you have an HP.
HP violates UEFI specification that says NOT to use description as part of boot.
And of course only valid description is "Windows Boot Manager". 
But many work arounds. Most listed in my signature below.

Most common work around for dual booters is to use the fallback or hard drive boot entry. 
That is the same type of entry used to boot external drives, but can be used for internal drives also. 
It uses /EFI/Boot/bootx64.efi.

If you run Boot-Repair it will auto copy shimx64.efi to be bootx64.efi. You may not may not then get an UEFI boot entry for the hard drive.
But you can use efibootmgr to add an entry if required.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 


But Boot-Repair also sees all the .efi HP files in the ESP and creates a 25_custom grub menu entry script for all of them. You may not need any or only a few of them.

       bootx64.efi Also edit of 25_custom
[http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)
# Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 

Manual rename required, before Boot-Repair started doing auto copy.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by Faoldorcha on 2017-03-15
Situation resolved.

For future reference here what worked:
I accessed the BIOS/UEFI boot order, and selected the OS boot manager. The two entries (window and ubuntu) where present, with windows first. I put ubuntu on top, and now I am again greeted with the boot selection panel.

Thanks a lot!

---

### Post by oldfred on 2017-03-15
Glad it worked.

So HP now lets users boot Ubuntu UEFI entry.

---

