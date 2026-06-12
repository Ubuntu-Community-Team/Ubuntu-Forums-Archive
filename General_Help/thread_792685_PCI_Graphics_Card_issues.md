---
title: "PCI Graphics Card issues"
date: 2008-05-13
forum: General Help
---

### Post by joe281180 on 2008-05-13
Hi, I'm having trouble getting my graphics card to work in ubuntu.
I'm currently using the on board intel 915gv graphics chip as I had to remove my graphics card in order to boot from the live CD. Now that ubuntu is installed (and working fine) I still cannot boot with the graphics card fitted.

The card is Nvidia quadro NVS 280 PCI.

I have downloaded the linux driver from the nvidia site, which is a .run file.
When I run the .run file however, it says that it can't install the driver as it cannot find the graphics card. Obviously this makes sense as the card isn't fitted. But since I can't boot with the card fitted I'm rather stuck.

If anyone has any ideas, I'd be very greatful.

---

### Post by njparton on 2008-05-13
With the quadro card in place how far do you get?
 
You need it in in order to install the drivers (as you've found out). If you can get as far as the command line then we can give you the commands to install envy from there and then use that to install the nvidia drivers.
 
Make sure onboard graphics are turned off in the bios.

---

### Post by joe281180 on 2008-05-13
thanks for the reply,

when I boot with the card fitted, it hangs on the ubuntu loading screen so I guess that means no command line, however I don't think there is an option in the BIOS to disable the onboard graphics, but I'll have another look...

---

### Post by njparton on 2008-05-13
There will be an option in the bios trust me.  It might be called something unexpected though.

Turning that off and putting in your quadro should solve most of your problems.

---

### Post by joe281180 on 2008-05-14
It looks like the only option in the BIOS is called 'First Boot', which can be set to the onboard graphics or PCI, it is already set to PCI.

I have discovered however that from the boot menu if I start up in recovery mode, I get as far as the log in screen. I can enter my user name and password, but it hangs before getting to the desktop.

---

### Post by ardvark71 on 2008-05-14
> **joe281180 said:**
> It looks like the only option in the BIOS is called 'First Boot', which can be set to the onboard graphics or PCI, it is already set to PCI.

I have discovered however that from the boot menu if I start up in recovery mode, I get as far as the log in screen. I can enter my user name and password, but it hangs before getting to the desktop.

Hmmm. That's strange. Any motherboard I've ever worked with that had onboard graphics always included an option to *disable* it entirely. What is the model and brand of your board?

Best Regards...

---

### Post by joe281180 on 2008-05-14
My motherboard is MSI MS-7036 (L-I915M).

Here's a link to a page with specs about the machine:
[http://www.uktsupport.co.uk/advent/pc/t9004.htm](http://www.uktsupport.co.uk/advent/pc/t9004.htm)

Thanks,
Joe

---

### Post by ardvark71 on 2008-05-15
Hi...

It probably doesn't, but by any chance does your Nvidia card show up in the xorg.conf file under /etc/x11?

Best Regards...

---

### Post by joe281180 on 2008-05-16
Hi, I've just got a reply from the motherboard manufacturer, saying the onboard gfx chip automatically disables when a PCI card is fitted. I don't think that is correct as I have to disable it in device manager in windows, so looks like I may be stuck.

I have discovered, contrary to my previous post (I'm pretty new to linux) that I can get to a command line, so can I run the installer from there? If so, how do I go about it - what commands do I need to type? The .run nvidia installer is sat on my desktop. As I say, I'm pretty new to linux so I don't know the commands etc yet but I'm proficient in DOS/windows.

I'll check the xorg.conf next time I have time to remove the gfx card and boot with out it,

thanks for help,
Joe

---

