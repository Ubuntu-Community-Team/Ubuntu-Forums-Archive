---
title: "Extracting Windows.iso to a USB"
date: 2015-05-03
forum: General Help
---

### Post by quinnmackenziefagan on 2015-05-03
so i've been trying to install windows to a USB in order to dual-boot my system and nothing seems to work. 

after looking on many other threads and trying about 20 different things i seem to have broken both my USB's as one of them is just no longer found by my computer and the other one gets an error if i try to mount it.

I need to know how to go about installing windows 7 on a seperate partition of my HD either without a USB, or instructions on how to fix my usbs and then how to install it using the USB's

---

### Post by RobGoss on 2015-05-03
I'm kinda baffled about your question this has nothing to do with installing Ubuntu. 

If your question is in regards to installing Windows 7, maybe you should as Windows forum [http://windowsforum.com/](http://windowsforum.com/) I'm sure they have a better understanding. Good luck

---

### Post by quinnmackenziefagan on 2015-05-03
sorry i should have mentioned, the only computer i have is runs ubuntu 14.04 and i need to learn how to reformat my usbs in ubuntu so i can actually use them

---

### Post by sammiev on 2015-05-03
I usually use Gparted which is found Ubuntu Software Center or Synaptic Package Manger to format my USB sticks.

---

### Post by yancek on 2015-05-03
> so i've been trying to install windows to a USB in order to dual-boot my system and nothing seems to work. 

I'm not sure if you are trying to install windows 7 to a usb or if you are trying to put the extracted iso on a usb and then boot it to install.  Trying to install to a usb will likely produce this error:

> "windows setup does 
not support configuration or installation to a disk connected through usb or IEEE 1394 ports"

I tried installing windows 10 and got that message.  Might be specific to windows 10 as it is just a preview I don't know.  I haven't installed windows of any kind in over 10 years.

If you want to format, you can use the suggestion above of using GParted.  If you have your Ubuntu installation media, it should be on that, otherwise it's simple enough to download and use.  A good tutorial on using it at the link below and the second link is the GParted Manual: 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

The link below explains how to extract the windows iso file and put it on a flash drive, boot the flash drive to install windows. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)
  
Iss there some reason you can't use a DVD?

---

