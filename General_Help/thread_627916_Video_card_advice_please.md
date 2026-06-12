---
title: "Video card advice please"
date: 2007-11-30
forum: General Help
---

### Post by Knot_Sharpe on 2007-11-30
Hi all,

This is my first post, hope u can help.  I got a cheap IBM netvista machine (P4, 1.9Ghz, 1G ram) and put Ubuntu 7.10 on it - works great!

I wanted to upgrade the onboard video, so I got an ATI/Radeon 9250 card for the AGP slot on the Mobo. Its a small form factor box, so I cut the card's metal anchor to make it fit ... I did this with my wireless NIC card, too and it worked fine.  I changed the BIOS to AGP (the other choices were PCI and Integrated), but when I boot the machine, I get a few lines of stuff loading OK, OK, OK, about 5 of them, but then it hangs and I don't get any video ... not from the monitor port or the DVI port with an adapter for the monitor.

I assumed I didn't have the right drivers, so I downloaded a pkg from ATI for this card for Linux, but it won't install ... I get a window (terminal?) that gives an error message but it disappears before I can read the reason for the failure. I'm able to run this from my desktop with the monitor connected to the on-board video port.

I sure would appreciate any suggestions, I was hoping that with the 3D card, that I could get Beryl running and some nice eye candy and games.

Best regards,
Knot_Sharpe

---

### Post by fragos on 2007-11-30
First rule of thumb is to use the video drivers that come the Ubuntu distribution.  In general, people have had better luck with Nvidia chip set cards.  I can't give you specific help with the ATI card. 

Your attention grabber is in poor taste and will actually keep some users from helping you.

---

### Post by Knot_Sharpe on 2007-11-30
Thanks for your reply fragos,

Obviously, since I'm running 7.10, any and all current drivers are loaded and didn't support the card when I installed it. One would think that the ATI driver specific for Linux, as I mentioned would be the best option ... I need some support from that point on ...

Sorry to have offended you, I'll edit out my poor taste commentary and hope for a workable suggestion that doesn't require me to invest in Nvidia chipsets ....

---

### Post by XVII on 2007-11-30
FYI for when you buy your next card, ATI has notorious problems with linux compatibility.

---

### Post by fragos on 2007-11-30
The best approach is to research the success others have had before buying.  Most hadware is supported by Linux and in my opinion some of it better than in the Windows environment.  There are some cases of proprietary hardware that it's not as well supported.  Video and wireless are areas that come to mind.  I wasn't offended -- the comment left a poor first empression of you.  I recommend you use serch on this web site to find threads that may help.  Beware of quick fix solutions that aren't in the Ubuntu repositories.

---

### Post by Knot_Sharpe on 2007-12-01
Thank you for your replies.

Perhaps someone can tell me how to freeze or copy the contents of a terminal window that is trying to run the installer file for the ATI drivers. At least I could move on from there ...

I could also use some advice on how to check for the following:

[COLOR="Blue"]Minimum System Requirements 
Before attempting to install the ATI Proprietary Linux driver, the following software must be installed: 

POSIX Shared Memory (/dev/shm) support is required for 3D apps 
glibc version 2.2 or 2.3 
Linux kernel 2.4 or higher 
XOrg 6.7,6.8,6.9,7.0 or 7.1; XFree86 version 4.3 

System Recommendations 
For best performance and ease of use, ATI recommends the following: 

Kernel module build environment - should include the following: 
Kernel source code: Either the Kernel Source or Kernel Headers packages 
ISSE Support enabled in your Linux Kernel 
Applies to Intel Pentium III and later CPUs only 
Enabled by default on version 2.4 and later kernels 
The rpm utility should be installed and configured correctly on your system, if you intend to install via RPM packages 
QT version 2.x.x is needed for the ATI Control Panel, but is not mandatory 

Note:  The following 32 bit packages must be installed in order for 64 bit drivers to install and work properly: 
· XFree86-Mesa-libGL
· libstdc++
· libgcc
· XFree86-libs
· fontconfig
· expat
· freetype
· zlib
 
Note:  In order to use the fglrx internal AGP support, you have to make sure that the kernel agpgart support is not active, i.e. it is not compiled into the kernel and the kernel modules are not loaded. If the fglrx kernel module detects that the kernel agpgart support is active, it will automatically use that even if its internal AGP support is requested in order to avoid conflicts that can cause problems under some circumstances.  [/COLOR]

Sorry for the length of the post. Any suggestions are appreciated.

---

### Post by fragos on 2007-12-01
Not sure about freezing the terminal window but you can use the virtucal scrool bar to see lines all the lines.   To copy, use your mouse to select the area you want copied and then to copy <Ctrl><Shift>C.  Paste in the terminal is <Crtl><Shift>V.  Paste in other windows is the <Ctrl>V we normaly use.

---

