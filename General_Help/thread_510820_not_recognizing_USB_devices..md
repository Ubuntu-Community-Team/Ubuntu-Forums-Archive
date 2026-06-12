---
title: "not recognizing USB devices."
date: 2007-07-27
forum: General Help
---

### Post by xl_cheese on 2007-07-27
not recognizing USB devices. 

--------------------------------------------------------------------------------

I can see my ipod, but not my all in one USB card reader. It worked before I had to reinstall ubuntu.

I tried logging out and back in to see if it worked, but as I was logging in Ubuntu froze... again. 

I boot to my vista partion and all is well on the hardware front.

I've had a crapload of issues with Ubuntu lately.

One I haven't tried to fix yet is my network manager freezing on intial boot. I have to log out and back in for it to work right.

I can't gksudo gedit /boot/grub/menu.lst as well as other files.

I can't play most of the games in the repo. They either freeze my system or do nothing at all. Some appear to do nothing, but show up in my processes.

The list goes on.

My computer is pretty healthy. amd x2 2.2Ghz 2Gb ram 8600gt video card.

I really want Ubuntu to take the place of windows, but vista seems to be winning most of the battles.



I should add that the forum stinks for searching. I search for "usb device" and get results for the OR of the two.

What happened to the google search bar in the advanced search?
__________________

---

### Post by PaulFr on 2007-07-27
1. Your USB card reader problem: I would start with ```
sudo lsusb -v|grep iProduct      # to see what is detected on your USB.
sudo lsmod | grep usb          # To see what USB modules are loaded
``` Also I would go through the dmesg output just after rebooting (and after inserting a card to see if there are any errors, especially anything to do with USB or readers.

2. Your gksudo gedit /boot/grub/menu.lst problem: any error messages ? What other files can you not edit ?

3. Your freezing and your game problems: I cannot help you here, but I would suggest you look at your graphics drivers as the possible source of your problems.

---

### Post by xl_cheese on 2007-07-27
> **PaulFr said:**
> 1. Your USB card reader problem: I would start with ```
sudo lsusb -v|grep iProduct      # to see what is detected on your USB.
sudo lsmod | grep usb          # To see what USB modules are loaded
``` Also I would go through the dmesg output just after rebooting (and after inserting a card to see if there are any errors, especially anything to do with USB or readers.

2. Your gksudo gedit /boot/grub/menu.lst problem: any error messages ? What other files can you not edit ?

3. Your freezing and your game problems: I cannot help you here, but I would suggest you look at your graphics drivers as the possible source of your problems.

```
wes@Dork-Ubuntu:~$ sudo lsusb -v|grep iProduct 
Password:
  iProduct                2 iPod
  iProduct                2 Mass Storage Device
  iProduct                2 EHCI Host Controller
  iProduct                2 USB Optical Mouse
  iProduct                2 DELL USB Keyboard
  iProduct                2 OHCI Host Controller
wes@Dork-Ubuntu:~$ sudo lsmod | grep usb  
usb_storage            72256  1 
usbhid                 26592  0 
hid                    27392  1 usbhid
libusual               17936  1 usb_storage
scsi_mod              142348  5 usb_storage,sg,sr_mod,sd_mod,libata
usbcore               134280  6 usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
wes@Dork-Ubuntu:~$ 

```

I assume the mass storage device is the usb card reader?

In my previous install the usb memory card would just show up on the desktop.  The icon even looked just like the card.  

Thanks for your help.  I'm not sure where to go from here?

---

### Post by xl_cheese on 2007-07-27
SOLVED.  

I reinstalled Ubuntu...  Everything works now.

---

