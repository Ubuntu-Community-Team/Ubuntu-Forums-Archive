---
title: "AMD Drivers, HD 4250"
date: 2014-12-10
forum: General Help
---

### Post by ramon9 on 2014-12-10
I can't install AMD 13.1 drivers in Xubuntu 14.04

My GPU is a HD 4250

---

### Post by Bashing-om on 2014-12-10
ramon9; Hi ! Welcome to the forum;

Yep, that is a fact - after release 12.04.1 .
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards. Terminal command -> X -version to determine the x-server version.
(Mark Phelps) 
&&
Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] ->
Sorry, but AMD dropped fglrx driver support for your card a while back. The default Radeon drivers that work on it now are the ones you have already installed.


Blame AMD .

[INDENT][INDENT][INDENT]sometimes there just is
[INDENT][INDENT][INDENT][INDENT]nothing you can do (start writing code ?)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2014-12-11
The open source Radeon drivers delivered in a standard Buntu are not as fast as drivers from AMD, but still they are advancing. You could try a live boot of 14.10 to see if you notice an improvement.

---

