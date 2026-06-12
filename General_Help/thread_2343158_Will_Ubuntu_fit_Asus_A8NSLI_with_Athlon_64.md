---
title: "Will Ubuntu fit Asus A8NSLI with Athlon 64 ?"
date: 2016-11-13
forum: General Help
---

### Post by abrogard-yahoo on 2016-11-13
My old XP machine has crashed for the last time and I'm going to switch to Linux - Ubuntu I guess.  Going to download the distro I see it says recommended is 2 core at 2G or better, etc..

Will my Asus A8NSLI with an Athlon 64 cpu do alright, you think?  If not, what should I look at?

---

### Post by QIII on 2016-11-13
Hello!

It is very hard to say definitively.  The best thing to do might be to work with a Live DVD for a while to see if you run into problems.

I would suspect that Ubuntu might be a bit problematic because the Unity interface is very resource intensive.  So it might be a good idea to also try Xubuntu and Lubuntu with their lighter desktop environments.  All they cost you is burning a DVD!

Cheers.

---

### Post by abrogard-yahoo on 2017-03-31
Thank you for that.  I"m a bit late getting back here aren't I?  I've been away but I don't think I got any email notification of replies. Should I?

Anyway I tried Xubuntu and it ran too slowly and I had to have a machine to drive a Hewlett Packard laserjet 3150 so I fired up XP again and have been running it.   The only drivers I can find for it are Linux or XP.

Now I'm ready to have another shot at linux.

Try a live DVD you say?  What's that?  Surely not a ubuntu distro on a dvd?  if it's resource intensive enough to slow my Asus surely it wouldn't run off a DVD?

I will search for info and I'll look into Lubuntu.

---

### Post by Impavidus on 2017-03-31
You only get e-mail notification of replies if you enable them. For regular visitors of the forum e-mail notifications are quite useless.

[Live dvds](https://en.wikipedia.org/wiki/Live_CD) and [live usbs](https://en.wikipedia.org/wiki/Live_USB) (but your computer may be too old to support those) allow you to test the operating system before you install. They are a bit slower than the version installed on the hard drive, but should tell you whether your hardware can handle it. They also provide the environment from which you can partition the hard drive and run the installer, which is included on the live disk.

If you've got very weak hardware, you could try a minimal install, which runs an installer from a command line interface.

---

### Post by mastablasta on 2017-03-31
what kind of GPU do you have?
What CPU do you have?
and how much ram?

all variants work well on Athlon 64, as long as the GPU has good support.

if Xubutnu was slow then it is likely because GPU has bad support or it is a poor one in general. with mor einformaiton i could tell you more.

i regulary test Kubuntu64 bit on my Athlon, as well as Ubuntu and i can easilly run Xubuntu and lighter versions in virtualbox in WinXP. But i have 4 GB RAM, nVidia GT730 2GB (that replaced the old Radeon HD3650 512 MB) and Athlon 64 which i think is a 3 Ghz one. single core.

---

### Post by abrogard-yahoo on 2017-03-31
Thanks for the replies.

Here's an extract from Belarc:

[TABLE]
[TR]
[TD]2.00 gigahertz AMD Athlon 64 3200+
128 kilobyte primary memory cache
512 kilobyte secondary memory cache
64-bit ready
Not hyper-threaded                        
[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD]                            Board: ASUSTeK Computer INC. A8N-SLI DELUXE 1.XX
Bus Clock: 200 megahertz
BIOS: Phoenix Technologies, LTD ASUS A8N-SLI DELUXE ACPI BIOS Revision 1016 12/01/2005                        
[/TD]
[/TR]
[/TABLE]

             [TABLE]
[TR]
[TD]                            1524.18 Gigabytes Usable Hard Drive Capacity
1007.54 Gigabytes Hard Drive Free Space

HL-DT-ST DVDRAM GH22NS70 [Optical drive]
3.5" format removeable media [Floppy drive]

Maxtor 6V200E0 [Hard drive] (203.93 GB) -- drive 2, s/n V40LHVFG, rev VA111630, [SMART]("http://www.belarc.com/smart.html") Status: Healthy
ST3320620AS [Hard drive] (320.07 GB) -- drive 0, s/n 5QF0G86S, rev 3.AAC, [SMART]("http://www.belarc.com/smart.html") Status: Healthy
WDC WD10EZEX-08WN4A0 [Hard drive] (1000.20 GB) -- drive 1, s/n WD-WCC6Y4KLEDZ7, rev 01.01A01, [SMART]("http://www.belarc.com/smart.html") Status: Healthy                        
[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD]                            3072 Megabytes Usable Installed Memory

Slot 'A0' has 1024 MB
Slot 'A1' has 512 MB
Slot 'A2' has 1024 MB
Slot 'A3' has 512 MB                        
[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD][TABLE="width: 100%"]
[TR]
[TD="width: 45%"][/TD]
[TD="width: 15%"][/TD]
[TD="width: 20%"][/TD]
[TD="width: 5%"][/TD]
[TD="width: 15%"][/TD]
[/TR]
[TR]
[TD]c: (NTFS on drive 1) *
[/TD]
[TD="align: right"]1000.19 GB[/TD]
[TD="align: right"]987.37 GB free[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]e: (NTFS on drive 2)[/TD]
[TD="align: right"]203.92 GB[/TD]
[TD="align: right"]3.63 GB free[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]f: (NTFS on drive 0)[/TD]
[TD="align: right"]137.43 GB[/TD]
[TD="align: right"]11.67 GB free[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]g: (NTFS on drive 0)[/TD]
[TD="align: right"]182.64 GB[/TD]
[TD="align: right"]4.86 GB free[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
        * Operating System is installed on c:

[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]*None detected*                        
[/TD]
[/TR]
[/TABLE]

  
[TABLE]
[TR]
[TD] [TABLE="width: 100%"]
[TR]
[TD]HP LaserJet 3150[/TD]
[TD]on LPT1:[/TD]
[/TR]
[TR]
[TD]Microsoft XPS Document Writer
[/TD]
[TD]on XPSPort:[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

             [TABLE]
[TR]
[TD]                            Standard floppy disk controller
NVIDIA nForce4 Parallel ATA Controller
NVIDIA nForce4 Serial ATA Controller (2x)                        
[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD]                            RADEON X800 SE [Display adapter]
RADEON X800 SE Secondary [Display adapter]
hp m703 [Monitor] (15.7"vis, s/n 1295529271, March 2003)                        
[/TD]
[/TR]
[/TABLE]

             [TABLE]
[TR]
[TD]                            Standard Enhanced PCI to USB Host Controller
Standard OpenHCD USB Host Controller                        
[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD]                            MPU-401 Compatible MIDI Device
Realtek AC'97 Audio
Standard Game Port                        
[/TD]
[/TR]
[/TABLE]

             
I just fired up the old Linux installation ( it is on a separate hard drive , I only have to plug it in ) and I find I switched from Ubuntu or xubuntu, whichever it was that I found ran too slow, to Linux Mint and that's what I've got there now.

I couldn't give it a good test because I couldn't get the wifi to work.  It works fine when the XP hard drive is in there.   And it used to work on the Mint hard drive.  But not today.  so I put another, new,  wifi stick in there but it still wouldn't connect, though it found the possible connections.  And tried to connect - got as far as asking me for the password.  But still wouldn't connect after getting the password.

I have two wifi connections available and it found and started the connection process for each one as I pointed it that way but on both it just wouldn't complete the connection.  Maybe a driver problem but I can't understand how to install the drivers that came with the wifi stick.   There's just a bunch of files and no install prog.

That's a digression I guess.  Just a heads up on where I'm at.

Interested to know what you think of my hardware, with respect to running linux.  (mint or whatever).  I would like to run this old printer off it and I would also like to use it as a little web server and run apache on it if it's capable of that.  No heavy traffic, not lots of connections.  Just for my immediate friends and family.   

That's the plan.  That's the aim.

:)

---

### Post by oldrocker99 on 2017-03-31
Your PC is pretty close to the one I had in 2008, when I started using Ubuntu. It certainly ran fine on my deck, and should run fine on yours; Linux is famous for making old machines run.

---

### Post by abrogard-yahoo on 2017-03-31
well that's good news. that's what i expected but learned in recent time that modern distros - because of the heavy windows-like gui I guess - don't all do that.  hence searching for a distro that will.  i don't remember switching to mint but now I'm there i guess that's good enough?  no reason you know of why i should go back to ubuntu or xubuntu?

do you know where I can look for help on getting this wifi working on it?  i'm using those tiny cheap chinese usb things - i think they have the number 8188 associated with them somehow.

very peculiar how it does everything except finalise a connection.  needs a complete reinstall maybe - except i don't remember installing anything !

---

