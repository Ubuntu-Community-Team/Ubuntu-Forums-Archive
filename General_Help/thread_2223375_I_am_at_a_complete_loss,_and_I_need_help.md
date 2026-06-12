---
title: "I am at a complete loss, and I need help"
date: 2014-05-10
forum: General Help
---

### Post by vincent14 on 2014-05-10
Alright here is the story. I was updating ubuntu yesterday, and when I rebooted, I found that my graphics driver was replaced with llvmpipe, my sound card was undetected, and USB sticks were no loger getting detected (however my usb mouse was still detected). My computor is now running at a sixteenth of its normal performance. I do not care if there is a way to fix this or not, this was the final straw. I decided to switch back to mint, so I made a liveusb on one of my old rigs that still has winxp. Upon booting from the usb drive, I was prompted with the message "remove disks or other media......press any key to restart." I was told after resarching a little that this was probably an OS issue. So my question is, how do I completely wipe my HDD? I only have one HDD, and it is running my OS and has my other data on it simultaniosly. Is there any way to format and wipe it even though it has my OS on it and is my only HDD? If this is not possible, does anybody have any other solution?

---

### Post by grahammechanical on 2014-05-10
I cannot help you. You have confused me. What do you want help with? The machine that has Ubuntu on it and that is booting using llvmpipe which is Ubuntu's fallback open source video driver? The same machine that you are going to install Mint on? Is it that one? Or is it some other machine that has XP on it?

Does the USB memory stick have Mint or Ubuntu on it? The message that you saw usually appears when we are exiting from a live session. Was that what you were doing? If not then and this message appeared it may be that there is something wrong with the power supply to the motherboard. Just a wild guess.
 
Can you understand why I am confused and cannot help you even do a simple thing like formatting a hard disk using a live session. A live session of Ubuntu has a utility that will let  us format the hard drive. It is called Disks. If you simply want to install a Linux distribution, then install Linux and the installer will format the hard drive as standard procedure. 

Regards.

---

### Post by vincent14 on 2014-05-10
Sorry for making this so complicated...
1) My ubuntu on my current pc is screwed up
2) I am going to switch distros
3) I made a live usb on a different comp that is running winxp
4) I put the live usb in the comp I have that is currently messed up
5) I boot into the usb and get the error message
6) Apparently this is an os error
7) Apparently the best way to work around this is to format my entire HDD. The issue is, I can't do that from the usb because I can't boot into the live session.
8) I need a way to format my hard drive on the actual machine, since the live usb is unreadable due to my broken os
9) I can't use an actual live cd because I did not build my pc with a cd reader.

---

### Post by buzzingrobot on 2014-05-10
This -- "remove disks or other media......press any key to restart." -- is not an error message.  It is the message Ubuntu and Ubuntu derivatives display on screen at the end of a live session or after installing Ubuntu. 

If you created an Ubuntu USB stick, booted it, and saw that message display immediately, then something is wrong with either the way that image was burned or with that image itself.

You contradict yourself when you say you booted from a USB and then say the "live usb is unreadable due to my broken os".  If you boot from a USB or a DVD/CD, the condition of the OS installed on the machine is irrelevant.  The BIOS determines what medium is used for the boot.  If you insert a USB with a correctly burned OS image and tell the BIOS to boot off it, the OS on machine's drives does not execute.

You do not need to format your drives if all you want to do is install another version of Linux.  Just select manual partitioning ("Something Else..." in Ubuntu parlance) and reuse each existing partition. (Highlight a partition, click "Change", select the desired filesystem, click "Format" assuming you want to format that partition, select a mount point, doublecheck, and go.)

---

### Post by vincent14 on 2014-05-10
Well if what you said is true, then I gotta find out what I did wrong with making my actual USB key. I thank you for your input.

---

### Post by buzzingrobot on 2014-05-11
> **vincent14 said:**
> Well if what you said is true, then I gotta find out what I did wrong with making my actual USB key. I thank you for your input.

When an Ubuntu install image is booted, it displays an initial screen asking if you want to 'Try Ubuntu' or 'Install Ubuntu'.

---

