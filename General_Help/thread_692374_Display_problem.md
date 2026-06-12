---
title: "Display problem"
date: 2008-02-09
forum: General Help
---

### Post by jlh68 on 2008-02-09
I recently installed a new motherboard and processor.  A new Hard drive for Ubuntu.
I had a hard time installing Ubuntu.  I first tried a CD with 7.10 on it and it would stop at 90%.  so I tried 7.04.  I got it installed and then had to update 189 files or so.

Ok the problem is on my LCD display I am getting some vertical lines and it appears that the left most line have material that is from the right side.  there are four "noise"lines on the right and three on the left.

My system is an AMD Athlon 64 X2 4000+ dual core processor, a mother bard that uses SIS Northbridge and South Bridge.  I have 2-GB of RAM.  My Ubuntu HD is 320 GiB, and the Windoze HD is 120 GiB.  I do not get these lines using the windoze XP OS.

I got the lines using the live Cd as well as installed Ubuntu.  I did not experience the lines when using my laptop (Ubuntu 7.10) hooked to the LCD.

I have no ideal as to the cause of the problem.  Help from this forum would be great.

---

### Post by pytheas22 on 2008-02-09
The most likely culprit is your graphics card or driver.  What kind of graphics card do you have, and what driver are you using for it (e.g. proprietary or open-source), if you know?  If you don't know, just post your /etc/X11/xorg.conf file here.

---

### Post by sigmarhophi on 2008-02-09
If the problem is durring the installation phase, have you tried changing the vga setting at the install menu?  Otherwise I agree we are looking at a driver set up issue.  Post the contents of your xorg.conf and we can go from there.  what is your graphics card?

---

### Post by jlh68 on 2008-02-12
Ok I have found a reference to my problem.   [http://www.winischhofer.eu/linuxsispart1.shtml#13](http://www.winischhofer.eu/linuxsispart1.shtml#13)

[SIZE="1"][B][I]A few words about the SiS 760 (all versions)
	[/B]
The SiS760 is a chipset for the AMD64 and AMD Sempron platform. These CPUs have a memory controller built-in, ie in systems based on these CPUs, there is no dedicated memory controller present.

As with all integrated SiS chipsets, the SiS 760 supports shared video memory, ie. memory that is shared between the system and the graphics (this technique is called "UMA"). However, the 76x also supports dedicated video RAM (so-called "local framebuffer memory" = "LFB") which connects directly to the graphics chip and is accessible for the CPU via the bus. Shared memory and local memory can be combined ("hybrid mode").

Shared memory is slower, because the graphics chip has to access it via the system memory bus, while it can access local framebuffer RAM directly. Most if not all modern graphics cards therefore use local video memory.

While shared memory was quite usable on all previous integrated chips (630/730, 65x, 661, 74x), there is a serious problem with it on the SiS760 - caused by the aforementioned fact that the CPU contains the system memory controller. This leads to severe memory bandwidth limitations if only shared system memory is used and no local framebuffer memory is present.

Therefore, the 760 - if used with shared memory only - is not really usable in dual head configurations; even in single-head operation, some features are limited. This especially affects video overlay support (Xv): Although the SiS760 supports two video overlays, these are in most cases not usable: Heavy flicker in the video and the graphics may occure as a result of exceeding the available memory bandwidth. The X driver takes some counter-measures on such systems (even advanced ones in the Premium Version), but it can't avoid the problems entirely. On systems with both shared and local video memory, the drivers will only use the local memory part. You may likewise disable the shared memory in the BIOS.

My advice: Don't buy a machine with a SiS760 unless this machine has dedicated local video memory. And please don't complain about "driver bugs" if you see "flashing lines" on the screen; these are the typical effects of a bandwidth problem and unavoidable - even the Windows driver can't do better. In such cases, reduce the resolution and/or refresh rate and/or color depth, or use one output (CRT1 or CRT2) only. Sorry, can't help it. There is no driver bug involved.

For poor Averatec 6240 users: My drivers at least allow 1280x800 on the LCD if the external monitor is enabled... the Windows driver kicks you back to 1024x768 in such a case.[/I][/SIZE]

I have an AM2 Socket, MoBo with an Athlon 64 2X 4000+ CPU, 2 GiB of dual channel RAM, the MoBo has a SiS 761GX/965L chipset.  I have Ubuntu 7.10 installed on a 320 GiB HD, and WinXP installed on a 120 GiB HD.  I stillhave npt gotten my WinXp "Activated" since the MoBo replacement.

I am thinking about installing a PCI or PCI express Graphics card with its own GPU and RAM to see if that would correct my display problem.

Are there merits to that approach?

---

### Post by pytheas22 on 2008-02-12
I have an old SiS card and it's not very impressive in Ubuntu.  I think the drivers are just not that good, and the cards themselves are pretty weak to begin with.  I remember doing some research once to try to get my card to work better in Linux (specifically, to be able to get resolutions higher than 1024x768) and there were a few tricks that could be done to tweak out some extra performance--although I never did get a higher resolution.  Try some search terms like "sis linux or sis xorg," or if I get time in the next few days I'll see if I can find the sites I used.
> 
I am thinking about installing a PCI or PCI express Graphics card with its own GPU and RAM to see if that would correct my display problem.

Are there merits to that approach?

If you have this hardware available, I would say that it's definitely worth a try.  You have a much better chance of getting a better configuration, especially if those cards use chips that are better supported.  Moreover you'd be freeing up more system memory by using a PCI/PCIE card instead of onboard video.

---

### Post by Therion on 2008-02-12
> **jlh68 said:**
> 

I am thinking about installing a PCI or PCI express Graphics card with its own GPU and RAM to see if that would correct my display problem.

Are there merits to that approach?
Absolutely.  

A discrete graphics solution (meaning an actual video card) is going to be a far superior solution compared to just about any onboard/integrated graphics setup.  I'd suggest you try and find an inexpensive nVidia series 6xxx or 7xxx ...  Something along those lines -- you certainly don't need to blow a load of money on this.

---

