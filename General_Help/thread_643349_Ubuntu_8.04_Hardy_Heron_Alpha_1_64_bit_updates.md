---
title: "Ubuntu 8.04 Hardy Heron Alpha 1 64 bit updates?"
date: 2007-12-17
forum: General Help
---

### Post by kdarkentity on 2007-12-17
Hmm... now this is interesting i swear i saw a few 64 bit updates in the list of updates that i just installed, however i installed the 32 bit version. My cpu supposedly does support 64 bit though but i tried installing 64 bit ubuntu before and my bios would not allow it. 

Is there a way i can check to see if my os is still 32 or now 64 bit?

By the way  i am running Ubuntu 8.04 Hardy Heron.

---

### Post by rsambuca on 2007-12-17
If you are running 32bit, then you are running 32bit.  You won't be using any 64bit packages, because it would hose your system.  To confirm, you can enter the following command in a terminal:

uname -a

---

### Post by kdarkentity on 2007-12-17
This is the output i got for "uname -a"

Linux kevin-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

Is it 32 or 64 bit?

---

### Post by rsambuca on 2007-12-17
> **kdarkentity said:**
> This is the output i got for "uname -a"

Linux kevin-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

Is it 32 or 64 bit?

That is 32-bit (i686).  The 64-bit systems are referred to as  x86_64.

---

### Post by kdarkentity on 2007-12-17
Ah alright then. i thought my cpu should be i386 but i guess not than.

---

### Post by jrharvey on 2007-12-17
What kind of processor do you have? You should be able to find out if it supports 64 bit.

---

### Post by rsambuca on 2007-12-17
> **kdarkentity said:**
> Ah alright then. i thought my cpu should be i386 but i guess not than.

The uname command just tells you what version of the Operating system you are using.  It doesn't tell you whether you have a 64bit capable cpu.

---

### Post by kdarkentity on 2007-12-17
Well i have an Intel pentium dual core (not the core 2 duo) 

according to intels web site m cpu is 64 bit capable, but i don't think my current bios has 64 bit support therefore whenever i try to boot up any 64 bit cd whether it be 64 bit winodws or 64 bit ubuntu i get an error message stating that i do not have a 64 bit cpu.

---

### Post by rsambuca on 2007-12-17
Some of the dual core Intels are 64bit, but most aren't.  Do you know the exact model number?

---

### Post by kdarkentity on 2007-12-17
What do you mean model number, the number on the chip itself? 
This link is to the overview of my processor.
[http://www.intel.com/products/processor/pentium_dual-core/]("http://www.intel.com/products/processor/pentium_dual-core/")

---

### Post by rsambuca on 2007-12-17
As I said, some are and some aren't.  Look at [this page]("http://www.intel.com/products/processor_number/chart/pentium_dual-core.htm") and you will see the listing.

---

### Post by kdarkentity on 2007-12-17
aww damn no kidding my cpu just happens to be one of the non 64 bit cpu's 

The model number is T2060

---

### Post by jrharvey on 2007-12-17
I dont think any of the Dual Core Pentiums are 64 bit. The only Intel 64 chip that I know of is the core 2 and Xeon series. Maybe the centrino duo. Not even the core 1 is 64 bit. Its a shame though. I think they should only use 64 bit chips. Whats the point, they are just slowing down the transition.

---

### Post by kdarkentity on 2007-12-17
> **jrharvey said:**
> I dont think any of the Dual Core Pentiums are 64 bit. The only Intel 64 chip that I know of is the core 2 and Xeon series. Maybe the centrino duo. Not even the core 1 is 64 bit. Its a shame though. I think they should only use 64 bit chips. Whats the point, they are just slowing down the transition.

Look [Here]("http://www.intel.com/products/processor_number/chart/pentium_dual-core.htm")

Most of the Pentium dual cores are 64 bit

---

### Post by jrharvey on 2007-12-18
I just dont understand why Intel doesnt take advantage of the 64 bit marketability. AMD has been putting 64 all over the names of their processors yet i cant tell if an intel chip is 64 but intil i research. That is just a shame.

---

### Post by kdarkentity on 2007-12-18
Yea i totally agree, intel probably made this chip in particular because it would be cheaper and easier to sell. And it was probably made almost two years ago now.

---

