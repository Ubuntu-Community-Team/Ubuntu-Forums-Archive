---
title: "How to use USB-Stick like an Ubuntu-CD"
date: 2007-03-20
forum: General Help
---

### Post by ADS on 2007-03-20
Hi there, 

I tried to make my USB-stick work like the Egdy Eft CD, so whenever I start a PC with it, it should boot Ubuntu and let me work or install Ubuntu like the CD does. 

Well, my idea was to create an image of this CD and copy the image onto the USB-stick. For any reason it does not work. What would you suggest?

---

### Post by ADS on 2007-03-20
Ok, I will try this: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by RudolfMDLT on 2007-03-20
I just installed Ubuntu onto the USB disc - no when I go to varsity I just restart their pc and boot into Ubuntu.

---

### Post by ADS on 2007-03-20
> **RudolfMDLT said:**
> I just installed Ubuntu onto the USB disc - no when I go to varsity I just restart their pc and boot into Ubuntu.

Yes, this is an option but with 2 disadvantages: 1. It needs a lot of space which is scarce on USB-Sticks and 2. you cannot install Ubuntu from your USB-Stick to any PC like you could do with the Ubuntu-CD. 

I still haven't found time to try the way I linked but as soon as I do I will post the outcome.

---

### Post by ADS on 2007-03-21
Ok, now I tried it. I could install "syslinux" onto the USB-Stick, I did it under Windows XP using the DOS-Box, there was "syslinux.exe", but I cannot find a "mtools.exe".

And I have to admit I am an Linux-Newbie. So I would like to try installing "mtools" running Ubuntu but someone has to tell me how to install things without "*.exe". 

The link I posted says just: "Make sure that "syslinux" and "mtools" is installed. If they are not, install them. SYSLINUX is available for both Linux and Windows. For more information check the SYSLINUX homepage"

And the SYSLINUX-Homepage tells me only how to install Syslinux, [http://syslinux.zytor.com/faq.php#bootable](http://syslinux.zytor.com/faq.php#bootable) but does not tell me how to do this with "mtools". :( 

Help is appreciated. :popcorn:

---

### Post by Teg_Navanis on 2007-03-22
Type 

```
apt-get install syslinux mtools
```

in the terminal. This should do the trick if you're connected to the internet. If your installation is fresh, you might have to run

```
apt-get update
```

first. If you prefer a graphical interface, try synaptic. It's under system - administration.

For more info, go here: [https://help.ubuntu.com/community/SoftwareManagement]("https://help.ubuntu.com/community/SoftwareManagement")

---

