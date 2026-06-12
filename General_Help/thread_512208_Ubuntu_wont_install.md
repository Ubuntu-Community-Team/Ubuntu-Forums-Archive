---
title: "Ubuntu wont install"
date: 2007-07-28
forum: General Help
---

### Post by Daskies on 2007-07-28
I'm trying to install Ubuntu 7.04 to no avail. 

The error I receive when I try the 64bit version is:
(This displays at the bottom of the page)
> Kernal alive
kernal direct mapping tables up to 100000000 @ 8000-d000
The error I get with the x86 version is:
> [   40.165099] .. MP-BIOS bug:8254 timer not connected to I0-APIC
[   40.343935] Kernal panic - not syncing: I0-AIPC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the noapic option
[   40,343971]


I have a *AMD 64 Athalon X2 4200+* which is 64bits, but I _think_ I remember doing something to set it 32bits, so I could run XP. I'm not sure if I did this, or if I'm imagining it. 

My question is: what causes these errors, and how do I fix it? I built the computer myself, and can give you any more information you need.

Oh, and by the way, I have 2 hard drives. 1 has Windows XP, and the other is NFTC with a few random files on it (it has no operating system on it)

---

### Post by apjone on 2007-07-29
turn you computer on make sure it boots form the cd when the option to start the live disc comes on press the F6 key and type in:
"noapic" [without the quotes]
followed by return, it should boot up and install as normal!

---

### Post by Daskies on 2007-07-29
Any idea what wrong with the 64bit one? Does the error that it gives you tell you anything? i *do* have a 64bit processor, so it seems like a waste not to use it.
If it helps I think at one point (when I first turned the computer on) it asked me if I wanted to run 32, or 64; I said 32, as for the time being there was no good 64bit OS.

Thank you for the help with the 32 one, and if the other wont work I'll go with that.

---

### Post by rillip on 2007-07-29
the 64x error doesn't really tell me anything, but you should be able to install a 64x kernel from synaptic/adept once you are set up.  Look for the amd k8 with smp.

---

### Post by Daskies on 2007-07-29
So I can install the 32bit version, and have it upgrade it self to 64bit one? It might sound like a silly question, but I don't want to waste hours at this :p.

---

### Post by Daskies on 2007-07-29
RAWR I'm ready to stab something >_>. I've tryed to get this working for another 2 hours, so let's recap.
(First, if you didn't read up I have 2 hard drives. The SATA is my "master" and it has XP. I also have a ATA drive that's empty [it's a slave to DVD burner, as my cable is short] My processor is 64bit).

[CENTER]**With both hard drives in**[/CENTER]
Error with 64:
> Kernal alive
kernal direct mapping tables up to 100000000 @ 8000-d000
First error with 32bit:
> [ 40.165099] .. MP-BIOS bug:8254 timer not connected to I0-APIC
[ 40.343935] Kernal panic - not syncing: I0-AIPC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the noapic option
[ 40,343971]
After using "noapic":
> 
X Windows System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Ubuntu 2.6.20-15generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
[Tab Here]Before reporting problems, check with [http://wiki.x.org](http://wiki.x.org)
[Tab Here]to make sure you have the latest version
Module Loaders present
Markers (--)pro load [not sure about that one, my hand writing was off], (**)from config file, (==) default setting
[Tab Here](++)from command line, (!!) notice, (II) informationsal,
[Tab Here] (WW) Warning, (EE) Error, (NI) Not implemented, (??) unkown
(==) Log File: "/var/log/Xorg.0.log", time [The current time]
(EE) Unable to locate/open config file
New driver is "nv"
(++) Using default built-in configuration (55 lines)
(EE) Open /dev/fb0: No such file or directory
(EE) AIGLX: Screen 0 is not DRI compable
Could not inti font path element /usr/share/fonts/X11/1000dpi/:unscaled removing from list 
Could not inti font path element /usr/share/fonts/X11/Type1, removing
from list
Could not inti font path element /usr/share/fonts/X11/100dpi, removing
from list

Fatal server error:
Could not open default font 'fixed'

There were, of course, other errors, but they went by too fast

[CENTER]**With only the ATA Drive**[/CENTER]
Error with 64:
> Kernal alive
kernal direct mapping tables up to 100000000 @ 8000-d000
First error with 32bit: 
> [ 40.165099] .. MP-BIOS bug:8254 timer not connected to I0-APIC
[ 40.343935] Kernal panic - not syncing: I0-AIPC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the noapic option
[ 40,343971]
After I entered noapic I got a ton of errors that flew by, however I caught two numbers that might be useful:
> 0x1f166
7c07b35

---

### Post by Daskies on 2007-07-30
I've now tried a ton of various combinations with "noapic" on, and off. One hard drive in, the other one in, both in, completely unformatted, et cetra. I was finally told about the text version for problems with installs, so I downloaded it. I ran the Kubuntu text installer (both 32, and 64). The 64bit one just did nothing, and the 32bit on gave me this error:
>  [    1.172000} Kernal Panic - not syncing: VFS: Unable to mount root fs unknown-block(104,1)
Any more help?

---

