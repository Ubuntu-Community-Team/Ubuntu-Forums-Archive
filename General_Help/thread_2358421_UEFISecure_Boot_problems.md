---
title: "UEFI/Secure Boot problems?"
date: 2017-04-13
forum: General Help
---

### Post by thebrokenworld on 2017-04-13
A while back I tried out Ubuntu on an HP Pavilion p7-1067c, Ubuntu recognized that it was being installed on a UEFI system and changed... something. Ubuntu ran fine and I set the computer aside and forgot about it for a while. Sometime later I decided to put Windows back on it, but I didn't have the HP restore disks, couldn't get everything working right and then noticed that Ubuntu was listed in the BIOS under the UEFI boot devices, even though I had wiped Ubuntu from the hard drive. I thought that this might be causing a problem, so I did something to remove Ubuntu from that list, I got a warning that what I was doing was something that could never be undone, but went ahead with it anyway. I don't remember the details here, and I really wish that I did. I set the computer aside again for a couple of months then decided to try installing Ubuntu again, but now I can't get it to boot from the USB thumb drive and there are no options associated with secure boot anywhere in the BIOS. Did I really permanently screw up this computer? I got Mint to install from a DVD, but the BIOS hangs for quite a while on startup, and it's really annoying me. Ubuntu will also start from a DVD. 

I made the bootable USB drive using the method described [here.]("http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media") I also got the same errors described [here]("http://askubuntu.com/questions/599516/symbolic-links-error-while-creating-ubuntu-uefi-bootable-usb"), but I guess that they're not a problem?

Edit: I also tried using the Startup Disk Creator in Ubuntu.

---

### Post by oldfred on 2017-04-13
Normally we use gpt with UEFI.

 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 

HP generally is not UEFI dual boot friendly. It violates UEFI standard that says NOT to use description as part of boot. And only valid description is "Windows Boot Manager".
Depending on whether dual booting or just Ubuntu there are several alternative work arounds.
See link in my signature and:
      
 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':

---

### Post by thebrokenworld on 2017-04-13
Wow, this actually turned out to be a problem with my USB drive, I tried another and everything worked fine. Sorry about that, I forgot that I had another that I could try. I did partition the drive using the msdos option (instead of gpt) in GParted this time around, so that may have helped. I'm wondering if the Startup Disk Creator screwed up my USB drive, because I had to reconfigure its geometry with TestDisk, GParted kept giving me errors when I tried to reformat the drive. I still got the symbolic links error while making the bootable USB, but everything seems to be working fine. I'll try a different method for making that sometime soon. Thanks for all of your help.

Edit: It looks like the symbolic links error might be a result of partitioning the drive with the msdos option, I retried with gpt and didn't get the errors. The system does boot with the gpt partition.

---

