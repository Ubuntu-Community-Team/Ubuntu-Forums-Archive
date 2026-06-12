---
title: "can t boot anymore cause no more ESP partition on wintel W8"
date: 2016-11-29
forum: General Help
---

### Post by gaut2 on 2016-11-29
hello,

i have try to install ubuntu on my wintel W8 but during installation i made a mistake and delete the ESP partition of the EMMC storage device of my wintel W8. Now i can't boot anymore even with my USB key connected to the wintel...

Is there a way to get the USB key booting again?

---

### Post by oldfred on 2016-11-29
Deleting ESP on internal device, would have nothing to do with not booting external flash drive.

What settings do you have in UEFI/BIOS? Many have to allow USB boot. And many have to turn off secure boot.

---

### Post by gaut2 on 2016-11-30
ok, since i did that there's no more boot overides options in save&exit UEFI tab.....

each time i boot my wintel w8 with my usb ubuntu installation key inserted, it shows the constructor brand (here american mega trends), then it's a black screen during one second, and then it's the UEFI configuration menu.

here's a part of my UEFI configuration :

```
-------------- advanced tab --------------------
-------------- USB configuration menu -----------
legacy support -> enabled
usb3.0 support -> enabled
xhci hand-off -> enabled
ehci hand-off -> disabled
usb mass storage driver support -> enabled

usb hardware delays and time-outs :
usb transfer time-out -> 20 sec
device reset time-out -> 20 sec
device power-up delay -> auto

mass storage devices :
Generic storage device 1402 -> auto

--------- advanced tab -------
------ Security configuration menu -------
TXE -> enabled

--------- chipset tab --------
----------- usb configuration menu ----------
usb otg support -> disabled
usb vbus -> ON
XHCI controller -> enabled
xhci mode -> enabled
usb2 link power management -> enabled
usb2 (ehci) support -> disabled
all usb port -> enabled
uhci port 1 -> enabled
uhci port 2 -> enabled
uhci port 3 -> enabled
uhci port 4 -> enabled

----------chipset tab---------
bios read/write protection -> disabled
rpmb provision -> disabled

----------security tab-----------
secure boot -> disabled
secure boot mode -> standard

---------boot tab--------------
setup prompt timeout -> 1
bootup numlock state -> on
quiet boot -> disabled
fast boot -> disabled
boot options priorities :
boot option #1 -> UEFI : generic storage device 1402
```

---

### Post by oldfred on 2016-11-30
Please use code tags for longer text or terminal output.

Is 1402 the name of your internal drive?
Then you may need to set USB flash drive as first in boot order.

---

### Post by gaut2 on 2016-11-30
"[COLOR=#000000]Is 1402 the name of your internal drive?[/COLOR]
[COLOR=#000000]Then you may need to set USB flash drive as first in boot order."

[/COLOR][COLOR=#000000]1402 is the name of my usb key : it's already[/COLOR][COLOR=#000000] the first device in the boot order :[/COLOR]
```
---------boot tab--------------
setup prompt timeout -> 1
bootup numlock state -> on
quiet boot -> disabled
fast boot -> disabled
boot options priorities :
boot option #1 -> UEFI : generic storage device 1402
```

---

### Post by oldfred on 2016-11-30
Are you sure flash drive is correctly configured?
We have seen issues where download of ISO was not correct, where one installer software worked but another did not, where one brand of flash drive worked and another did not. And even where different USB ports worked and others did not.
May require some experimentation.

Not familiar enough with your specific system to know more details. It may still be one of the settings in your UEFI. Sometimes it is some setting that is not obviously related.
Is this what your system is?
[https://www.avforums.com/review/wintel-w8-android-windows-10-tv-box-review.12697](https://www.avforums.com/review/wintel-w8-android-windows-10-tv-box-review.12697)
With only 2GB of RAM Lubuntu or Xubuntu may work better if you can install.

 [http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/) 

 [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 
      
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
     [https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by gaut2 on 2016-11-30
"[COLOR=#000000]Are you sure flash drive is correctly configured?"
-> during the same day i was using this usb key on the wintel w8 for an installation of ubuntu on it, and i was getting it booting the same day on ubuntu. But then during the installation process i deleted my efi partition, and the installation can't install grub-efi-ia32 on the new partition created, so i shutdown my wintel and tried to boot on my usb key again, and it wasn t working anymore, i use another usb key (a usb key 2.0 that time with linux mint) that one too i wasn t able to boot from it. So i don't know which parameter i have to change in the uefi configuration to get it booting on usb key again.....

"[/COLOR][https://www.avforums.com/review/wint...x-review.12697]("https://www.avforums.com/review/wintel-w8-android-windows-10-tv-box-review.12697")"

that's effectively the hardware i m using.

---

### Post by oldfred on 2016-11-30
Is this then one of those limited systems that has a 32 bit UEFI but is really a 64 bit system?
Those were created as Linux did not have a 32bit UEFI and most suggested it should not even be done.
But vendors/Microsoft created it to try to lock out other installs. 
Now there is the bootia32.efi     , but you have to manually copy that into live installer and maybe into your system. Do not know how that all works.

I saved some links, but now you do not have to compile your own, as you can download it.
 [http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393)
Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 16.04 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md)
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)

Next time backup ESP partition before changing things.  And if you have backup, you can just copy it back. With UEFI no special install is required.

---

### Post by gaut2 on 2016-11-30
ok i find how to boot on the UEFI shell and then to boot on an ubuntu installation usb key :

you need 2 usb keys :
- one with your ubuntu installation
- one formatted in FAT32

first i have to download the bootia32.efi here : [https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi](https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi)
then i have to copy bootia32.efi on my empty FAT32 usb key, and to rename it Shell.efi, take care of writing it with the "S" in uppercase,

after this start the wintel W8 with the FAT32 usb key plugged in, and in the save&exit tab i have to choose "Launch EFI Shell from filesystem device",
here i get on the shell

---

