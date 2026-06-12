---
title: "IBM T30: Lubuntu 14.04 running incredibly slowly"
date: 2014-08-26
forum: General Help
---

### Post by csiebester on 2014-08-26
The computer is an IBM T30
Pentium 4 mobile 2.0 GHz 
400MHz bus speed
1Gb (2x512Mb) RAM
4200RPM 60GB hard drive (new)

Opening and closing anything is painfully slow.  Just as an example opening Abiword took 23 seconds to open when I randomly timed it.  It is able to stream youtube smoothly at 480 but nearly freezes as soon as I click to change tabs.  I feel like this machine should be more than capable of running a Linux distro for old computers, but right now it's just about unusable.  Under task manager it says that 100% of CPU is being used all the time but the list of tasks can't even add up to 50%.  Also it says it's using 400 something Megs of RAM out of 494 for some reason, but I opened it up to check and make sure I was right about how much there is.

---

### Post by mörgæs on 2014-08-26
Please run **free -m** and post the results in CODE tags.

---

### Post by csiebester on 2014-08-26
This is with 4 tabs of Chromium open. Underscores are to hold the formatting.

____________total____used____free_____shared___buffers___cached
Mem:_______494_____461_____33______13_______1________93
-/+ buffers/cache:____366_____127
Swap:______507_____212_____295
csiebe@csiebe-ubuntu-laptop:~$

---

### Post by mörgæs on 2014-08-26
CODE tags are better to hold the formatting. Please use the advanced editor. 

Nevertheless, you have 494 MB of memory which is likely 512 minus a little for the graphics card. You can try some [performance tweaks]("http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289") but I'm afraid it won't do much of a difference having so little memory.

Is some memory disabled in BIOS? 

Here's some explanation about measuring memory: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by csiebester on 2014-08-26
I'm now pretty sure that the problem is memory.  The same installation (physically swapped the hard drive) runs much much better on a different but comparable computer.  I went into Bios and it thinks that only 512 Mb of ram is installed.  I also tried a different set of ram also 2x512 and the Bios still thinks there is only 512 Mb.  I see no way to change this in Bios.  Using sudo lshw detects both RAM modules for 1Gb total.   Suggestions?

---

### Post by mörgæs on 2014-08-26
Upgrading the BIOS?

---

### Post by csiebester on 2014-08-26
I was afraid you were going to say that.  I guess that's the next step.  It seems like a lot of poeple have this problem and after an hour of searching I have still not found a good soluton.

---

### Post by csiebester on 2014-08-27
Morgaes, just for your interest I believe I figured out the problem.  The laptop, an IBM T30, has a known hardware flaw which causes one of the laprop's memory slots to disconnect from the motherboard due to fatigue failure of the pins.  I'm afraid that's the deth knell for the computer because I don't think that I'm up to the task of resoldering the pins on a RAM slot and it won't run Lubuntu as is.  

Thank you for your interest and your help.

---

### Post by mörgæs on 2014-08-27
Hmmm, strange. Lshw read both memory modules? Please post the output from **sudo lshw -C memory** in CODE tags.

---

