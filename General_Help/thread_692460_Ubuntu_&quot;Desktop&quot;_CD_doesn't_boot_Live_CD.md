---
title: "Ubuntu &quot;Desktop&quot; CD doesn't boot Live CD"
date: 2008-02-09
forum: General Help
---

### Post by Tronman on 2008-02-09
Hi All,

I downloaded the AMD64 bit "desktop" version (ubuntu-7.10-desktop-amd64.iso), but I don't get a Live CD desktop, just a command line interface (the "ash" shell). Everything I read seems to indicated that I should get a Live CD desktop even if it's amd64 version.......any idea why? Or how I do get into the Live CD? 

Thanks!

---

### Post by pytheas22 on 2008-02-09
Yes, you should get a desktop.  Here are some things to check: are you sure your processor supports 64-bit?  Did you check the CD for defects (I believe there's an option for this at the boot menu)?

If those are not the problem, then it could be that Ubuntu is not able to set up your graphics card properly.  What kind do you have?

Also, what specifically happens after you put in the CD?  Do you get a list of options, the top of which is "Start or Install Ubuntu?"  Does it do anything after that?  What does the command line say?

---

### Post by Tronman on 2008-02-09
Hey, thanks for responding.

Yes, I am sure my processor supports 64-bit. It is an AMD Athlon 64-bit. I've had 64-bit openSuSE installed on it before.

When I put the CD in and boot, I do indeed get the Ubuntu disk menu. The options are "Start or install Ubuntu", "Start Ubuntu in Safe Graphics Mode", "Install with driver update CD", "OEM install (for manufactures)", "Check CD for default", "Memory Test", "Boot from Hard Disk".

When I select the first option, I see the "Ubuntu" splash screen with the little red bar that moves back and forth along the larger black bar. Shortly after that, some text flashes up thats too fast too see. The screen goes black again and then I see:

Busy Box v1.1.3 (Debian 1:1.1.3-5ubuntu7. Built-in shell (ash). Enter 'help' for a list of built-in commands.

and the prompt comes up:

(initramfs) _


The options I tried on the boot menu, "Start or Install Ubuntu", "Start Ubuntu in Safe Graphics Mode",and "Check CD for Defects" all bring up this prompt. 

I have an ATI Mobility Radeon 9600/X600 Graphics Card. I had no problems in the past with it working on my openSuSE installation and my Xubuntu 6.

Thanks

---

