---
title: "Ubuntu 12.04 freezes"
date: 2013-04-13
forum: General Help
---

### Post by MHC on 2013-04-13
I used 64 bit Ubuntu 10.04 without it ever freezing, and successfully upgraded to 12.04. But a few months ago it started occasionally freezing. Now it does it so often it is almost unusable. Especially as I am trying to use if for professional work with deadlines - starting again, and again, and ... is not an option. I have done a google search about this, and it is a huge problem. I need to hear from Ubuntu whether this is going to be fixed soon. Because if not, then I will have to reluctantly go back to Windows.

---

### Post by gifford on 2013-04-13
What have you done to try to fix the problem? Are you using the 64 bit version of Ubuntu 12.04? What type of video card do you have? 
I appreciate your frustration, just trying to get more information on the problem.

---

### Post by MHC on 2013-04-14
Thanks for your offer to help. When I said it is a huge problem, I meant for many users, with many different configurations. That makes me nervous about tinkering with my system (not being very tech savvy) to try to get a work around. However, I guess it can't make things worse than they are, as it is also a huge problem for me at the moment. My graphics card is a VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4870]. 

Yes, I am using the 64 bit version of Ubuntu 12.04. I have not changed any hardware, but have added graphics and video recording software. I have tried using previous kernels, since this problem did not start straight away with 12.04. But my kernels don't go back far enough - all the ones I have now give the same problem. I have tried booting in recovery mode. I have tried fixing dependencies with **sudo apt-get install -f **a[FONT=arial]nd, when that didn't work, with [/FONT][FONT=arial]**sudo dpkg-reconfigure -phigh -a. **But nothing changed. [/FONT]  
[FONT=arial][/FONT]

---

### Post by gifford on 2013-04-14
I am going to assume you are using the proprietary drivers for the AMD card. As for the kernels, Synaptic Package Manager will have the older ones available. From what I read in the google search, it does seem to be a fairly common problem. Many of the solutions seem to be upgrading the kernel. The latest one I see in Synaptic for my 12.04 AMD64 system is 3.5.0-27. 
I also will assume you already know and have used the shift key while booting will give you the grub menu and allow you to select the kernel to boot.
Sorry to not have an easy answer. I can appreciate the frustration as it sometimes is just a process of elimination to find a solution.

---

