---
title: "Bootup problem"
date: 2007-04-22
forum: General Help
---

### Post by DMXell on 2007-04-22
Okay, so I downloaded the newest version that was released about an hour or so ago and thought it'd actually work for me. I ended up. however, getting the same problem I got with the version right before. Whenever I bootup into Ubuntu, a list of numbers and words scrolls down the screen, then stops and my computer does nothing.

Below is a link to a screenshot of it (okay, actually it was a picture from my camera that, for some reason, did a fish-eye effect).

[http://farm1.static.flickr.com/226/469039935_f871b934e6.jpg?v=0](http://farm1.static.flickr.com/226/469039935_f871b934e6.jpg?v=0)

---

### Post by DMXell on 2007-04-23
Can anyone help me?

---

### Post by DMXell on 2007-04-24
I've uninstalled it and reinstalled it several times, still the same problem.

---

### Post by DMXell on 2007-04-25
Can no one possibly help me on this issue?

---

### Post by leibowitz on 2007-04-25
That's what we call a kernel panic.

The linux kernel did crash. Now you want to find what is causing this. 

Try to boot in recovery console. That may help. And please, tell us about your hardware configuration.

---

### Post by DMXell on 2007-04-25
Thank you for actually responding :-p I've been dieing, my Windows is starting to critically melt down and I just don't want to use it anymore.

As for the "recovery console" do you mean in Ubuntu or Windows? In Windows I'll reboot and go into what they dub as "Recovery Mode" but I like your phrase better as it's more intuitive. Ubuntu doesn't even load to the normal menu.

As for my hardware configuration, I'll try my best explaining this (I don't fully understand what, exactly, you're looking for):

eMachine's Pre-built Crap:
-200 GB SATA HD, 7200 RPM
-2.93 GHz Intel Pentium 4 Processor
-533 Mhz FSB
-1 MB L2 Cache
-DVD+/RW Drive (nearly broken)
-512 MB DDR SDRAM (2x 256 MB sticks)
-Intel Graphics Media chipset
-300 Watt Power Supply

My few Mods:
-nVidia GeForce FX 5200, 256 MB of Video RAM (driver installed)
-1x 1 GB stick of RAM (I don't remember the grade of RAM)
-500 Watt Power Supply

Other External Stuff:
-Crappy Microsoft Mouse because my Wireless mouse broke
-Logitech Keyboard (dunno type, driver not installed)
-20" Widescreen METRO LCD monitor
-Netgear WG111v2 802.11g (or whatever, something like that)
-4-port USB extension
-HD Printer
-Boston 5.1 Surround Sound system

I can't think of anything else, I hope that I hit what you were looking for.

---

### Post by DMXell on 2007-04-26
Okay, I have no idea how to actually search for the problem... How is something like this usually fixed?

---

### Post by ali4949 on 2007-04-27
ok i had a similar problem like this.. this is what i did
on my laptop i removed the wifi pcmcia card and the boot went thru.. once in gnome i inserted the card and was able to get online.. i also blacklisted the hostap_cs and hostap drivers.. when the grub menu comes up select the option in recovery mode, i think press e and then b to boot the kernel and you should be able to save that configuration later.. 
let me know if this approach works

---

### Post by ago on 2007-04-27
If a stock kernel crashes it is usually because of a hardware problem (unlikely to be wubi specific). For instance it might be the memory which is defective, the fan that does not work or some other hardware. If you have frequent crashes in windows that might well be the case. You can try to use some Live CD.

---

### Post by DMXell on 2007-04-27
Well, I know that my 1 GB stick of RAM is less than five months old, so I doubt it's that. I bought my 500 watt box about 2 months ago, and it came with a huge fan so I also doubt that it's that. I can really only see that it's the fact that eMachine designed the computer as a problem.

I may also have a worm if that's any help. About a year ago I got it, then I reinstalled Windows without the install recovery CD, so the worm may be in my D:\ partition. Windows crashed 5 times since the worm, and is slowly dying again right now (I keep getting errors like the user32.dll was relocated in memory when I try to open some things, and CDs won't open). I might reinstall Windows soon and try.

But I don't think that it's those. I've tried Ubuntu, Kubuntu and Xubuntu in MS Virtual PC, and in them all my mouse wouldn't work. In normal VG mode my screen would screw up, but the safe VG worked, I just couldn't move my mouse. I've tried others like DSL and Slax Killbill edition in it and those let me control my mouse and do stuff (I know that I9 can boot DSL off a Live CD and have it work as well).

---

### Post by leibowitz on 2007-04-27
When I mean Recovery console, I was talking about Ubuntu. But I was not thinking about the Live-CD. And you are probably using the Live Desktop session.

When the CD shows the boot menu, please try to add an option to the kernel. You can do that by pressing F6 (Options) and write **single** at the end of the line.

That will boot a recovery console. If it's working, you won't be in a graphical interface, but in a console with a prompt like this "root#" 

Then just try some various commands, like **dmesg**, **lspci**, etc.

Note that **ago** is right, it's probably related to your Hardware. I don't mean it's broken but maybe not well supported. 


PS: it's not related to any Windows program, virus or not.

---

### Post by DMXell on 2007-04-27
I only have the previous Ubuntu Live CD (6. something). Will that still work with Feisty? I'd burn a new one but Windows has decided not to recognize my CD drive.

---

### Post by leibowitz on 2007-04-28
Yep still the same with any Ubuntu Live CD version.

---

