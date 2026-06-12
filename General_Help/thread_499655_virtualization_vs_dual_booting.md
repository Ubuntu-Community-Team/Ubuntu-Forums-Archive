---
title: "virtualization vs dual booting"
date: 2007-07-12
forum: General Help
---

### Post by huangja on 2007-07-12
Hi, 

I used to dual boot linux and windows on my laptop, but i have since gotten rid of the windows partition, because i didnt really need it and it was a pain to reboot the machine. I am considering virtualization, however. I just want to know how well does a program like virtualbox run windows on linux, especially in regards to devices and such. 

For example, I have a SD card reader which doesnt work very well on linux, but works perfectly on windows. Would I be safe to assume that it will work under a virtualization of windows if I installed the drivers? 

Also, how seamlessly does virtualization actually run? System resourses aside, does it run smoothly? Do all windows programs work on it? Is it ever buggy like wine?

Thanks

---

### Post by zero244 on 2007-07-12
I use Vmware server which is free. It works very well it will run just about any Windows program that doesnt require 3D acceleration......like games etc.
I was able to play a DVD movie but most high end games are out.
Look for a How To........there are some additional files to install before you actually install Vmware server.
I run Windows XP in as a virtual machine to do online banking and some audio streaming.
I haven't tried Virtual Box but it appears vmware server is easier to set up.
Your usb drives will work........you just have to make so you turn them on when you first start up vmware.
They must be mounted before you try to run Windows in a virtual box.
Its really pretty slick software, you can even test out other versions of Linux.
The only real restriction is 3D rendering and any device that wont run on Linux probably will not work in a Windows virtual machine.

---

### Post by huangja on 2007-07-12
The reason I am asking about the SD card reader is that I dont believe that the drivers for it on linux are that robust. My SD card mounts fine on linux, but then crashes when i try to transfer large files to it. However, it runs perfectly under windows with the official texas instruments driver. Will i be able to install and use this driver under a virtualization of windows?

---

### Post by bettlebrox on 2007-07-13
> **huangja said:**
> . Will i be able to install and use this driver under a virtualization of windows?
No I don't think it will work. All calls from the Virtual image still have to go through the host OS. So if the host OS can access the drive, then the Virtual image won't. 

Have you asked in the forum about getting the SD drive working properly?

---

### Post by swisscow on 2007-07-13
I've tried this Virtualbox thing and it's great. It took me 5 minutes to set up following the instructions in the virtualbox manual. Had WindowsXP installed in ......well as long as it normally takes to install windowsXP. Added USB support (which for some reason then got my wireless internet working with it) which took about another 5 mins. Shared a folder between Linux and Windows, took another 5 mins.

What I'm saying, **is it doesn''t take long **to try virtualbox out and you may find yourself pleasantly surprised with your SD card reader. 

Here's some links:

[HTML]http://www.virtualbox.org/wiki/Downloads [/HTML] - for manual and deb file (I don't know if it is the repositories).
[HTML]http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices [/HTML] - for enabling USB

For the shared network folder, have a look in the virtual box manual. You will need to install the guest additions first (once you have installed windows - about page 43 I think) then set up the shared network.

Give it a go!

---

