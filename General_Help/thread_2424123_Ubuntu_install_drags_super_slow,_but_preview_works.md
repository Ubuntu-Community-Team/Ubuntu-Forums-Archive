---
title: "Ubuntu install drags super slow, but preview works fine.  Ideas?"
date: 2019-08-03
forum: General Help
---

### Post by boermac on 2019-08-03
Okay, first I apologize... I'm a big noob with Ubuntu.  I have extensive computer experience and some experience with Linux (Red Hat), but from command line only.  This is my first time trying Ubuntu.  

I've got an old Windows server that was running Win7.  I downloaded Ubuntu Desktop and have it on a Flash Drive.  When I boot from that drive and run the "trial" everything seems to be working great.  In fact, I'm posting this thread from that trial boot.

But when I install on the harddrives it run soooooo slow that it's 100% unusable.  I move the move and it registers the move perhaps 60-90 seconds later.  I have type in my password and that's a little faster, but even typing lags horrible.

Any ideas why this would be?  I have the hard drives configured in RAID 6 right now.  Now sure if that's the problem or not.

---

### Post by TheFu on 2019-08-03
The stock Ubuntu desktop wants a $200 GPU. I'm exaggerating a little about the GPU needs.  It matters much more if you run a desktop inside a virtual machine.  I can't use Gnome3 inside my VMs and find it too bloated for use on my Intel iGPU systems.

BTW, please always include the exact release you are running. Ubuntu changes default GUIs like some people change socks.  We don't know which release you are running. On older hardware, especially "servers" which don't have some HOT GPU, best to start with a lite GUI - Ubuntu-Mate or Lubuntu or Xubuntu, if you like the whole distro method, or you can just install the bare DE (or use a pure WM setup), if you like.

Depending on the GPU and release, there are different GPU drivers that can help, sometimes.  Please post the output from **sudo lshw -C video** which will show the GPU and driver being used.

If your "extensive computer experience" is with Unix, then you have a good background.  If it is Windows, well, things are different.

Is there a reason you didn't load Ubuntu Server?  That doesn't have a GUI and only a few things are different between RHEL and Ubuntu's Server besides package management. 90% is almost identical, if not identical.  This isn't important, just curious.

---

### Post by boermac on 2019-08-03
Thanks for the reply.  I'll look up some of that stuff soon here an I'll post results from the video info.

Yeah, my extensive experience is 95% windows, so I know things are going to be different, but I want to learn more Linux.  The reason I didn't do server was that I wanted the GUI interface but if it's (probably) the GUI that's killing it, I try loading server and see how that works.  

What I'm not understanding though is why it works just fine running the "trial" but dies when running the full install.  Is the trial just using more "lite" gui stuff?

---

### Post by TheFu on 2019-08-03
> **boermac said:**
>  What I'm not understanding though is why it works just fine running the "trial" but dies when running the full install.  Is the trial just using more "lite" gui stuff?

I'm afraid to answer any questions without knowing the specific release you are running. The answers are different.  It is possible that the GPU driver installed was a bad choice.  In Linux, don't go out to the vendor sites for any drivers.  That's a good way to make things harder initially and harder with every patch cycle ... but the solution is different DEPENDING ON WHICH RELEASE IS BEING RUN.  Drivers provided directly by the vendor sometimes are buggy, so using the curated by Canonical versions is best for many different devices.  No all, but most.

---

### Post by boermac on 2019-08-03
Okay, installed Ubuntu server 18.04.2

There's dual VGA ports on this machine, one in front, one in back.  I'm connect to the back one. Both ports apparently are shown doing the above line command.  I'm not sure which I'm plugged into.

First is:

VGA compatible controller
GM206GL [Quadro M2000]
NVidia Corp

Second listed is:

VGA compatible controller
G200eR2
Matrox Electronics Systems

Thinking about it more.... There's a video card in this thing.  This server used to be used for security camera stuff back in the day and suspect the card is in there to help manage that.  I'm not that card at all.  That's probably the NVidia.

---

### Post by boermac on 2019-08-04
I put mate on the server install and that seems to be working pretty well for my needs so far.  Thanks much for your help.

---

### Post by Artim on 2019-08-04
That's so weird.  I know that Gnome is a resource hog, but it's amazing that something as simple as a DE can make so much of a difference!  My Xubuntu is plenty fast, and on modest hardware.

---

### Post by boermac on 2019-08-04
> **Artim said:**
> That's so weird.  I know that Gnome is a resource hog, but it's amazing that something as simple as a DE can make so much of a difference!  My Xubuntu is plenty fast, and on modest hardware.

Please forgive the noob question, but what does DE mean in this context?

---

### Post by Autodave on 2019-08-04
DE = desktop environment.

You may be having issues because of the 2 different graphics cards in there.  If it were my machine, I ould try getting rid of one and then the system would install the proper driver for the other one.  If the system installed and Nvidia driver and you are using the non Nvidi card, that could / would give you very poor performance.

Personally, I would keep the Nvida one.

---

### Post by oldos2er on 2019-08-04
> **boermac said:**
> Please forgive the noob question, but what does DE mean in this context?

[Desktop environment]("https://en.wikipedia.org/wiki/Desktop_environment"), it's a particular graphic interface with an accompanying suite of applications. Ubuntu's default DE is [Gnome3]("https://en.wikipedia.org/wiki/GNOME").

---

### Post by Autodave on 2019-08-04
The more that I think about this, I am thinking that the install program installed the driver for the wrong GPU.  In other words, it saw one of them and installed the proper driver for that one, but you were using the other GPU.

From what I read, the Matrox is on the motherboard, so the Nvidia card is the add on one. The Nvidia card should have way more graphics RAM than the Maxtor.  Make sure that you are connecting the monitor to the Nvidia card.

---

### Post by TheFu on 2019-08-04
When a specific command is requested, please
* run the command
* post the output, including the command actually run

It provides the details we need, which we don't have at this point.  Still missing the GPU drivers actually being used.  For example:
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: UHD Graphics 620
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:126 memory:ee000000-eeffffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff

```
wrapped in code tags, as above.  There isn't any question or misinterpretation from what command or the output this way.  The only thing that I would consider slightly sensitive would be a MAC for a NIC and _maybe_ a public IP for a DHCP connection.  A public IP for a static connection isn't worth hiding. It is already public.

Please and thank you.

---

