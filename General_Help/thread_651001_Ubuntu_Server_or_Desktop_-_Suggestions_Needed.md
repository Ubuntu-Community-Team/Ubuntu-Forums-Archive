---
title: "Ubuntu Server or Desktop - Suggestions Needed"
date: 2007-12-27
forum: General Help
---

### Post by smartergeek on 2007-12-27
Hello Everyone,

First let me say "hello" to everyone and thanks in advance for any and all help.

I am a relative newbie to Linux and Ubuntu. I've played around with Knoppix, Mepis, and have installed Ubuntu desktop before to play around. Plus, I've used Knoppix and Mepis frequently to rescue files from crashed Windows pc's. I own an IT Support and Consulting business, and I also do web development. Now with the introductions out of the way, let's get on to business.

I have a client that has a digital arts/printing studio. He runs a few Windows desktops with Photoshop and some other apps including his scanning software for his high resolution scanners. Part of his business is scanning artwork and creating Giclee' prints. His network is relatively simple and we want to keep it that way - p2p with Windows file sharing.

Currently his "server" is a WinXP Pro desktop that serves out large image (.TIFF and .PSD) files that are sometimes over 1GB each depending on color profiling, etc. He runs a gigabit network, but his XP server is not the most powerful in the world. It's a "recycled" desktop that he once ran PS on.

Ok - so here is the deal. We know that the slowest link in his network right now is basically his XP server. The concurrent connections are limiting his access and the machine just doesn't have the horsepower it needs. We ordered him a Dell server and opted to go with "no OS installed" to save on the Windows licensing (tax), and I convinced him to give Linux a try as a file server. My preference is to try Ubuntu.

Here are my questions:

[LIST=1]
[*]Do we need to run Ubuntu Server edition or will the desktop version do fine? I am not a command line fan - I prefer a GUI environment and using the command line only when necessary.
[*]Are the any special considerations of getting Ubuntu to recognize the hardware as spec'ed out on the Dell?
[/LIST]

[LIST]
[*]Dual Core 3060 Processor, 4MB Cache, 2.4GHz, Xeon, 1066MHz FSB for PowerEdge 840 (222-6545)
[*]2GB DDR2,667MHZ,2X1G,Dual Ranked DIMMs (311-5313)
[*]Broadcom TCP/IP Offload EngineNot Enabled (430-1765)
[*]1TB 7.2K RPM Serial ATA 3Gbps 3.5-in Cabled Hard Drive (341-5882)
[*]Onboard SATA Controller - No RAID (430-1949)
[*]1.44MB,3.5 IN,INT FDD,PE830 (341-2605)
[*]No Operating System (420-6320)
[*]On-Board Single Gigabit Network Adapter, No TOE (430-2017)
[*]CD-ROM, 680MB,48X, INTERNAL (313-2820)
[*]Onboard SATA, 1 Drive connected to Onboard SATA Controller - No RAID (341-3889)
[/LIST]

Again, thanks in advance for any help and suggestions. I want this to go smoothly for my client and myself. Any issues (positive or negative) will be graciously shared back with the community.

---

### Post by bodhi.zazen on 2007-12-27
> **smartergeek said:**
> HHere are my questions:

[LIST=1]
[*]Do we need to run Ubuntu Server edition or will the desktop version do fine? I am not a command line fan - I prefer a GUI environment and using the command line only when necessary.
[*]Are the any special considerations of getting Ubuntu to recognize the hardware as spec'ed out on the Dell?
[/LIST]

<clip>

Again, thanks in advance for any help and suggestions. I want this to go smoothly for my client and myself. Any issues (positive or negative) will be graciously shared back with the community.

#1 - Go with the desktop installation then. You may want to install the server kernel and server software.

#2 - I do not see any obvious hardware conflict.

---

### Post by smartergeek on 2007-12-27
> **bodhi.zazen said:**
> You may want to install the server kernel and server software.

So I can install the desktop version and then install the server kernel and LAMP? Would this basically give me a GUI desktop (Gnome or KDE) for the server? If so, can you point me towards instructions for doing this?

I downloaded ubuntu-7.10-desktop-i386.iso and also ubuntu-7.10-server-i386.iso last night via bt to try them out.

Thanks again for your replies and help.:)

---

### Post by zvacet on 2007-12-27
In your desktop version go to the **synaptic>edit>mark packages by task>LAMP**

---

### Post by bodhi.zazen on 2007-12-27
> **smartergeek said:**
> So I can install the desktop version and then install the server kernel and LAMP? Would this basically give me a GUI desktop (Gnome or KDE) for the server? If so, can you point me towards instructions for doing this?

I downloaded ubuntu-7.10-desktop-i386.iso and also ubuntu-7.10-server-i386.iso last night via bt to try them out.

Thanks again for your replies and help.:)

To answer the question, yes.

The server kernel is, well, optimized for servers and is available in synaptic.

You then re-boot and select the server kernel from the GRUB list.

Yes, you can run a gui (gnome/ XFCE / fluxbox / openbox) on the server kernel.

You can install LAMP as above, assuming you need those.

HTH

---

### Post by smartergeek on 2007-12-28
> **bodhi.zazen said:**
> To answer the question, yes.

The server kernel is, well, optimized for servers and is available in synaptic.

You then re-boot and select the server kernel from the GRUB list.

Yes, you can run a gui (gnome/ XFCE / fluxbox / openbox) on the server kernel.

You can install LAMP as above, assuming you need those.

HTH

That helps greatly and thanks again!

Assuming I don't have any real hardware issues, this should be relatively easy then.:)

---

