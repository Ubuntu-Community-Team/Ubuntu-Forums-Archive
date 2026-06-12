---
title: "cant get aiglx to work in edgy...comp freezs"
date: 2006-11-15
forum: General Help
---

### Post by zeltak on 2006-11-15
Hi all

I recently upgraded to edgy from dapper. i am prtty new to linux and tried to install beryl with XGL first (i have an ati card and thats what the guide reccomend). only problem is that it worked very bad if at all. the computer was Really slow and now window decorations were seen. so i decided ill remove it and give aiGlx a shoot. now im trying to use aiglx (i understood its built in edgy?) and i get this message after i run beryl-manager:

zeltak@voices:~$ beryl-manager
zeltak@voices:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
                                 

what does it mean? is aiglx not installed? i think the ati drivers are installed correctly (they worked with the XGL "fglrxinfo" command...)
can anyone please help me a bit and guide me?

thx alot in advance

Zeltak

---

### Post by CCBalla10 on 2006-11-15
AIGLX will already be installed with Edgy, it comes with it...no need to try and install AIGLX

**Note where it says assuming AIGLX, means that it will by default use AIGLX...so you are set to go!**

---

### Post by CCBalla10 on 2006-11-15
what are your computer specs? maybe your computer and graphics card are not good enough to run Beryl

---

### Post by zeltak on 2006-11-15
thx for the answers!

I dont think its a hardware problem. i have a  intel P4 3.0Ghz, a ati radeon 9800 pro and 1.5 GB of DDR. could the XGL i installed before corrupt the beryl install or the aiglx? what more can i try? also what does it mean in the command line :->  "beryl: No composite extension"?

thx

Zeltak

---

### Post by juraj on 2006-11-15
You need to add the composite extension to your /etc/X11/xorg.conf

Just append this to it:

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by igknighted on 2006-11-15
> **zeltak said:**
> what does it mean? is aiglx not installed? i think the ati drivers are installed correctly (they worked with the XGL "fglrxinfo" command...

Are you still using the same drivers?  AIGLX does not work with the fglrx drivers, you need to use 'radeon' instead.  My apologies if you are already using this one, but the fglrxinfo command should no longer worg with the new drivers.  Instead, use :~$ glxinfo | grep "direct rendering" and if this says yes and you are using the radeon driver, then AIGLX should work fine.

---

### Post by zeltak on 2006-11-16
wow thx igknighted!


it did the trick, it now works! Awesome!

thx again to everyone

Zeltak

---

