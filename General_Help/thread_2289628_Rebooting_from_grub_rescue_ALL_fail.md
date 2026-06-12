---
title: "Rebooting from grub rescue ALL fail"
date: 2015-08-05
forum: General Help
---

### Post by mario63 on 2015-08-05
I saw that post because I have the same problem: [http://ubuntuforums.org/showthread.php?t=2207871](http://ubuntuforums.org/showthread.php?t=2207871). I cant run from BIOS and I cant do "ls (hd....)" because are all "unknown filesystem". I tried the solution of the post but I dont know if I did the "2. Start installation - set your install folder as your USB stick (I recommend at least 4GB) - ! Installation will took lot of time - you have to be patient !" wrong or... Because I boot on grub rescue and I did ls over my usb and said "uknown filesystem" :(. What can I do?

---

### Post by oldfred on 2015-08-05
Instructions were basically to use a working system to create a live installer to use as a repair flash drive.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


The ls commands are in grub rescue to see if you can find your install on your hard drive and then manually boot.
       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[URL="http://ubuntuforums.org/showthread.php?t=1599293"]http://ubuntuforums.org/showthread.php?t=1599293

[/URL]
 grub rescue:
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg

OR:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

[URL="http://ubuntuforums.org/showthread.php?t=1599293"]
[/URL]

---

### Post by mario63 on 2015-08-05
Ok... When I do ls I se (hd0),(hd0,gpt7....gpt6) but when I do ls over all I found the same result: "uknown filesystem".
I tried to run usblive and dvdlive of ubuntu but the screen was freezed on the "lenovo" boot. And I tried too with windows 10 ( I have the problem since I have installed ) with a dvd but I enter always on grub rescue. I think that if I "copy" the same filysitem on a usb and boot the grub rescue and do ls over the usb ( appears as hd1 ) maybe recognise and could do set prefix, root and insmod normal but I triend with a ubuntu installation .-> over usb and reinstall over usb and says the same... uknown filesystem.. What can I do?

---

### Post by oldfred on 2015-08-05
You cannot just copy to another drive. Lots of changes are required even if that might work.

You need to be able to boot live system. How did you boot when you installed?
If it shows gpt, you probably are UEFI, best to have secure boot off in UEFI. And do you have a  one time boot key or get into UEFI to choose DVD or flash drive.

Some systems seem to get confused when too many issues. Try cold boot or full power off. Removed battery if laptop & hold power switch to drain any left over power. Then press key to get into UEFI to boot DVD or flash drive. 
Some have had to open system and jumper pins to totally reset system. Some have a master reset as a pin hole. See your manual.

---

