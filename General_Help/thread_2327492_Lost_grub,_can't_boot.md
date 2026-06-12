---
title: "Lost grub, can't boot"
date: 2016-06-11
forum: General Help
---

### Post by DougieFresh4U on 2016-06-11
Haven't had this happen in years and I'm lost.
Running a dual boot Win10/Ubuntu machine.
I ran some updates in the Ubuntu then rebooted
into Win10 as I needed to do something.
When I rebooted to go back to Ubuntu I was presented
with this:

---

### Post by izznogooood on 2016-06-11
Well, you need to make a USB stick with Ubuntu on it. Then you can boot in to live mode and Chroot your enviroment and reinstall grub OR you could follow this guide: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I have used this with mostly success across the years...

---

### Post by DougieFresh4U on 2016-06-11
Got a live dvd and did boot repair
**[http://paste.ubuntu.com/17217869/](http://paste.ubuntu.com/17217869/)**
Going to reboot and see what happens/fingers crossed!

---

### Post by oldfred on 2016-06-11
HP has not been particularly friendly to booting anything other than Windows. They violate UEFI spec that specifically says not to use description as part of UEFI boot. And of course description they allow is "Windows Boot Manager".
But there are multiple work arounds. Boot- repair mentions one at the end of the report. Some are able to directly boot using HP's one time UEFI boot menu key.

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 

Most copy files so you boot hard drive UEFI entry, not ubuntu entry in UEFI. 
Boot-Repair in its advanced most should copy file & then you can boot using hard drive entry. 

     In Boot-Repair "Use the standard EFI file" Should do the same. 

If not you can manually copy files.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

Boot-Repair also sees all those HP .efi files in the ESP and creates a new 25_custom script to add them to grub. You probably do not want or need them.
 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
# Edit out entries you do not want, or you can turn execute bit off like above.
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by DougieFresh4U on 2016-06-11
Boot repair did the job.
I am back into system.
I may have panicked a little, but all 
seems good for now. I ran updates and updated grub
but haven't done another reboot, scared what I might find(?)
Thanks for suggestions.

---

