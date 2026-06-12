---
title: "GCC not working after fresh 7.04 Desktop install"
date: 2007-07-10
forum: General Help
---

### Post by bkaskar on 2007-07-10
Hi All,

Even before I could get to my real problem (IPN2220 PCI not working), I'm having troubles with NDISWrapper. 

Its on a Dell Dimenssion 8100 w/o any network, so I added the IPN2220 PCI wireless card (its not a PCMCIA or mini-pci). currently dual boot with XP and working fine but trying to switch. Only thing stopping me from doing that is I reboot to XP to download any thing and try it as I don't have any other easy way of getting stuff on this PC as of now. 

Already installed 7.04 desktop 3 times, first tried to put in the latest ndiswrapper from sourceforge, while trying make distclean it fails on me with gcc error; so next time tried to upgrade gcc 4.1.2 from 04 to 13 and broke the package dependencies.. since no network is present  so apt-get and other things I don't think I can make them work...

Now in the 3rd install I would like to do it right.. but how do I proceed as whenever I try to compile ndiswrapper 1.47 it couldn't even find stdio.h and other very basic headers to begin with :( 

when I check synaptic it shows that all the dev packages are installed.. Could someone please guide be as in what am I doing wrong. Why a simple 'make' turning its back on me?

---

### Post by stchman on 2007-07-10
> **bkaskar said:**
> Hi All,

Even before I could get to my real problem (IPN2220 PCI not working), I'm having troubles with NDISWrapper. 

Its on a Dell Dimenssion 8100 w/o any network, so I added the IPN2220 PCI wireless card (its not a PCMCIA or mini-pci). currently dual boot with XP and working fine but trying to switch. Only thing stopping me from doing that is I reboot to XP to download any thing and try it as I don't have any other easy way of getting stuff on this PC as of now. 

Already installed 7.04 desktop 3 times, first tried to put in the latest ndiswrapper from sourceforge, while trying make distclean it fails on me with gcc error; so next time tried to upgrade gcc 4.1.2 from 04 to 13 and broke the package dependencies.. since no network is present  so apt-get and other things I don't think I can make them work...

Now in the 3rd install I would like to do it right.. but how do I proceed as whenever I try to compile ndiswrapper 1.47 it couldn't even find stdio.h and other very basic headers to begin with :( 

when I check synaptic it shows that all the dev packages are installed.. Could someone please guide be as in what am I doing wrong. Why a simple 'make' turning its back on me?

The gcc C compiler requires the build-essential package.

sudo apt-get install build-essential

This contains all the C/C++ headers.  Without them you cannot compile C programs.  Make calls gcc to compile C for the kernel.

---

### Post by bkaskar on 2007-07-11
Hi Stchman,

Thanks for the help. I did manage to get GCC working with proper packages installed from the install CD. Infact after that I didn't have to recompile ndiswrapper and it the deb packages got installed smoothly.

Now I'm onto my main problem. with NDISWrapper I managed to get the infamous IPN2220 working but now WPA is not working so will look for help in appropriate forum.

Thanks again for your help
-B

---

