---
title: "Help with version needed"
date: 2007-04-16
forum: General Help
---

### Post by midlandman on 2007-04-16
Hi, it's the newbie here again with another dumb question...
I'm trying to DL Automatrix and it looks like I have to choose between 386 and AMD 64.
Which one do I choose? I looked around my admin area and "About Ubuntu" and couldn't find anything there to tell me what I need.
Any help would be appreciated.
As a side note, the only reason I'm trying to DL this is to play MP3s. The MP I have doesn't seem to support this and I can't seem to find the codecs for it.
Thanks.

---

### Post by raja on 2007-04-16
If you are running an Intel processor, choose the 386 one. If you have a 64 bit AMD processor, choose the AMD 64 one.

---

### Post by midlandman on 2007-04-16
Thanks, raja. I had a feeling it was something like that, but I wanted to be sure.

---

### Post by midlandman on 2007-04-16
Somethings not right. I keep getting an error "Error: Wrong architecture i386"
I'm using intel. Any ideas to whats happening here?

---

### Post by DougieFresh4U on 2007-04-16
Could you post your computers specs here for us to see?Not sure of the code but maybe copy and paste thids to terminal and post the output here code:;** lspci**

---

### Post by midlandman on 2007-04-16
What kind of specs are we talking about? I have a P4 3.2g processor and 1g of DDR ram with a 250g Sata HDD. I'm using the onboard graphics,Extreme Graphics 2 from Intel. FSB 800/533 and a Intel 865G chipset.
If theres anything else you need, I'll try to find out about it.
Thanks.

---

### Post by midlandman on 2007-04-17
OK, I did the code <uname -a> and something seems strange. It came up with AMD64. Isn't that an AMD prosessor? If thats what it means, then it's weird, because I use Intel.
I looked in my device manager and it even says -PCI Bridge>Intel...USB UHCI>Intel.
Am I wrong on this?
And how do I get back to my desktop? So far the only way I can is to hit the reset button and reboot. I'm sure there must be a better way to exit this thing.

---

### Post by eggdeng on 2007-04-17
The uname command tells you the kernel version you are using. It looks like you have installed the wrong (64-bit) kernel for your (32-bit) processor. As for getting back to your desktop, how did you get away from it in the first place? To use the command line, all you need to do is open a terminal in Applications -> Accesories -> Terminal.

---

### Post by midlandman on 2007-04-17
As for the terminal, I read here someplace that to get to it was <CTL><ALT><F3>. But it's nice to know there's an easier way to get to-and out- of it.
Now, about this kernel, will this be a problem? I have no idea how I did this. Can I, or should I change it?
And if it's no big deal, should I DL the Automatrix for AMD64?
Thanks.

---

### Post by midlandman on 2007-04-17
I thought I'd add this...

0000:00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
rick@rick-desktop:~$

---

### Post by eggdeng on 2007-04-17
If I were you, I'd wait until Thursday ,which is when the new ubuntu 7.04 is due to be released, & then download and install the x86 version. That way you'll get the benefit of all the latest stable packages and avoid the kind of hassle you're having now. Your specs, Intel graphics etc look good for ubuntu.

---

### Post by midlandman on 2007-04-17
Thanks for the reply, I do appreciate it.
I think I'll take your advice and do that, and I think I'll do a deep format first.
But can I ask 1 more question?
I'm trying to install flash, and the instructions say for me to navigate to a directory called install_flash_player_9_linux. How do I navigate to this?

---

### Post by zvacet on 2007-04-17
```
cd /install_flash_player_9_linux
```

---

### Post by midlandman on 2007-04-17
I followed the instructions exactly as they were written, and when I use that code I get " No such file or directory". When I extract the files, it goes to the desktop.
Is there any other way I can navigate to this directory?

---

