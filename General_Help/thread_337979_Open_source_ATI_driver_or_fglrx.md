---
title: "Open source ATI driver or fglrx"
date: 2007-01-13
forum: General Help
---

### Post by rekahsoft on 2007-01-13
Hi all, i just finished up messing up my working fglrx 8.32.5 trying to install the latest fglrx (8.33.6). I have a Radeon 200M. I managed to fix it but now am wondering if i should just run the open source drivers (afaik they do not support DRI for my card :() I can install the version i had working before but i would prefer using the open source alternative and be able to get DRI. It would also be nice to get support for AIGLX. So can anybody confirm that the open source ATI drivers do not support DRI for radeon 200M cards. thanks

---

### Post by rekahsoft on 2007-01-13
ok..now i have a problem...for some reason i am getting the same build error when i try and compile the fglrx module. The following is the error message:```
dh_testroot                                                                
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a 
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
        cat /usr/src/modules/fglrx/debian/control.template >
/usr/src/modules/fglrx/debian/control; \
        fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
        mv /usr/src/modules/fglrx/debian/postinst
/usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17-10-generic.postinst; \ 
        fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /lib/modules/2.6.17-10-generic/build
SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
Makefile:495:
/usr/src/linux-headers-2.6.17-10-generic/arch/i386/Makefile: No such
file or directory
make[1]: *** No rule to make target 
`/usr/src/linux-headers-2.6.17-10-generic/arch/i386/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [build] Error 2 
``` Why is this happening and most importantly, how do i fix it?

---

### Post by Patrick-Ruff on 2007-01-16
with the open source drivers you will get expiremental 3d accel (or no 3d accel at all.) 

therefore, you must use the fgrlx drivers. as for your problem, why are you trying to build the fglrx module?

you can get it off the repositories.

good luck

---

### Post by gwpritch on 2007-01-16
The driver on the repositories is only .28 so if you want the latest you have to get it directly from AMD. 
I would be interested how you got .32 to work. I have the same card and all I get is a black screen and locked up system when I try to login to X. 
.28 works for me but no acceleration.

---

### Post by rekahsoft on 2007-01-16
> **gwpritch said:**
> The driver on the repositories is only .28 so if you want the latest you have to get it directly from AMD. 
I would be interested how you got .32 to work. I have the same card and all I get is a black screen and locked up system when I try to login to X. 
.28 works for me but no acceleration.

I simply compiled 8.32.5 using the unofficial wiki. Although now that i tried reinstalling it i get the same error as i posted above :( ATI does one crappy job with there drivers :(

---

### Post by Brightrock on 2007-01-19
Hi,

I recently made the mistake of trying to make aiglx work on Dell 9300 with an ATI x300. Before I started working on this beryl and my graphics driver worked fine. Now fglrxinfo always tells me I'm using the mesa gl stuff and the driver doesn't seem to work--or at least not well. Here's the fglrxinfo output:

ERROR: DDX driver fingerprint mismatch: got 0x7A3E2CF0, but expected 0x32C4A39B
libGL error: InitDriver failed
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I can't find anything out about the DDX mismatch on these forums although when I google the issue I get this.

[http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877](http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877)

which makes it look like the new kernel will solve the problem. However, do I have to wait until Ubuntu updates? Is there some solution before that. Anyone else out there dealt with this problem?

Also I'm running edgy and have recently (in the process of trying to get this to work) updated my xorg.conf (installed breezy originally). (Don't worry I've followed the guides and modified the xorg.conf as needed for the fglrx driver. Still doesn't work.)

Thanks,

BR

---

### Post by rekahsoft on 2007-01-19
> **Brightrock said:**
> Hi,

I recently made the mistake of trying to make aiglx work on Dell 9300 with an ATI x300. Before I started working on this beryl and my graphics driver worked fine. Now fglrxinfo always tells me I'm using the mesa gl stuff and the driver doesn't seem to work--or at least not well. Here's the fglrxinfo output:

ERROR: DDX driver fingerprint mismatch: got 0x7A3E2CF0, but expected 0x32C4A39B
libGL error: InitDriver failed
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I can't find anything out about the DDX mismatch on these forums although when I google the issue I get this.

[http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877](http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877)

which makes it look like the new kernel will solve the problem. However, do I have to wait until Ubuntu updates? Is there some solution before that. Anyone else out there dealt with this problem?

Also I'm running edgy and have recently (in the process of trying to get this to work) updated my xorg.conf (installed breezy originally). (Don't worry I've followed the guides and modified the xorg.conf as needed for the fglrx driver. Still doesn't work.)

Thanks,

BR

if the newest kernel does fix the problem you could compile the kernel from source. or you could wait until the ubuntu updates are out (i would say to wait but it is up to you).

---

### Post by Brightrock on 2007-01-22
I probably will wait.  Do you know when they are going to update the kernel?  Will it be Feisty Fawn?  I think we just updated to something.something.17 around the holidays.  Or was that just my system?

---

### Post by igknighted on 2007-01-23
> **Brightrock said:**
> Hi,

I recently made the mistake of trying to make aiglx work on Dell 9300 with an ATI x300. Before I started working on this beryl and my graphics driver worked fine. Now fglrxinfo always tells me I'm using the mesa gl stuff and the driver doesn't seem to work--or at least not well. Here's the fglrxinfo output:

ERROR: DDX driver fingerprint mismatch: got 0x7A3E2CF0, but expected 0x32C4A39B
libGL error: InitDriver failed
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I can't find anything out about the DDX mismatch on these forums although when I google the issue I get this.

[http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877](http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877)

which makes it look like the new kernel will solve the problem. However, do I have to wait until Ubuntu updates? Is there some solution before that. Anyone else out there dealt with this problem?

Also I'm running edgy and have recently (in the process of trying to get this to work) updated my xorg.conf (installed breezy originally). (Don't worry I've followed the guides and modified the xorg.conf as needed for the fglrx driver. Still doesn't work.)

Thanks,

BR

the command 'fglrxinfo' is only for the proprietary ati drivers.  The only command you need to worry about with the open source radeon driver is 'glxinfo', or more specifically 'glxinfo | grep render' to cut right down to whether or not you have 3D rendering enabled.  The driver should work with the x300, as anything up to x850 should be passable.  Unfortunately for the OP who has the x200M, some of these cards work and others do not.  There is for some reason a discrepancy amongst these cards and some work alright, while other get nothing.  I'd say its worth a shot, because it won't leave you any worse than you are now (so long as you back everything up before you edit anything) and while the performance isn't quite as good with the open source driver, I'd still much rather use it just on principle.

---

### Post by igknighted on 2007-01-23
> **Brightrock said:**
> I probably will wait.  Do you know when they are going to update the kernel?  Will it be Feisty Fawn?  I think we just updated to something.something.17 around the holidays.  Or was that just my system?

Edgy will always be the 2.6.17 kernel, however it my update from -10 to a newer patch.  Feisty will use 2.6.20 if I am not mistaken.

---

