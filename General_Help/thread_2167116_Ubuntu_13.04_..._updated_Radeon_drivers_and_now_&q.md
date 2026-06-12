---
title: "Ubuntu 13.04 ... updated Radeon drivers and now &quot;Input Not Supported&quot;"
date: 2013-08-12
forum: General Help
---

### Post by GameGuru on 2013-08-12
Ok so I went from Windows 7 to Ubuntu 13.04 about two weeks ago and it was rock solid.  Today I decided to make sure I had the newest drivers for my video card and followed this guide:

> 1 - Download Catalyst 13.4 from AMD site (previous versions will not work).

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

2 - Install 32 bit libraries, type the following command on terminal:

sudo apt-get install ia32-libs
3 - Install kernel headers, type the following command on terminal:

sudo apt-get install linux-headers-generic
4 - Install DKMS, type the following command on terminal:

sudo apt-get install dkms
5 - Install Catalyst driver, type the following commands on terminal:

cd Downloads (assuming that the driver is in this folder)

chmod +x amd-catalyst-13.4-linux-x86.x86_64.run
sudo sh amd-catalyst-13.4-linux-x86.x86_64.run
Follow the instructions and reboot the system when asked.

6 - Have fun! :)

This line "chmod +x amd-catalyst-13.4-linux-x86.x86_64.run" gave me an error but the next one and all the other ones worked perfect.  It brought up the Catalyst installation box and followed the prompts and at the end it said it needed to reboot.

It reboots, posts and even does the Ubuntu splash screen but then it blanks and my monitor displays that "Input Not Supported" box.  I have rebooted many times but it keeps doing this.  How do I get it to work again?  Please help.

---

### Post by GameGuru on 2013-08-12
I tried going into GRUB and choosing any of the options, there are two kernal choices with each having an option for recovery mode and all four still bring up "Input Not Supported".  Why would updated video drivers do this?

---

### Post by GameGuru on 2013-08-12
Is there a way I can boot into the Live CD and alter the graphics driver my install launches?

---

### Post by GameGuru on 2013-08-12
Yes ... no?

---

### Post by QIII on 2013-08-12
Hello, gameguru! 

We ask that posts not be bumped more than once every 24 hours.

Remember that we are all volunteers here on our own time as we have time.  The community is also global, so it could be that the person with the best answer lives in Wellington, Taipei, Kolkata, London or Des Moines.  At the time you post, they may be asleep, at work, eating supper, playing with their children or out on the town.

Please be patient.  Someone will be along to help.

Best wishes.

---

### Post by GameGuru on 2013-08-12
Ok sorry about that but I am dead in the water until I am able to fix this.  Ok so have been doing research and I an not sure where the issue is happening.  Right after the Ubuntu loading screen with the dots below it then goes blank and my Acer monitor is telling me "Input Not Supported."  Again this was working like a dream without a hiccup until I attempted to get the latest Radeon drivers installed.

I am seeing where I can repair the GRUB2 with the Live CD but from my reading GRUB is the bootloader so I don't think repairing that would do anything, would it?  I am past boot and to the point it would have been hitting the desktop where I am getting this error.  

With my PC loaded to desktop with a Live CD what config file am I looking for on my hard drive to change the resolution or driver or put it in default mode or something?  I really need help here community and just don't know the terminology to search for the fix.  Thanks in advance.

---

### Post by GameGuru on 2013-08-13
I just wound up formatting and starting over.  I am surprised I never got a response.

---

