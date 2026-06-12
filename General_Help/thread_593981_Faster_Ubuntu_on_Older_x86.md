---
title: "Faster Ubuntu on Older x86"
date: 2007-10-27
forum: General Help
---

### Post by Ian505 on 2007-10-27
Please note that I am a beginner at linux, so this seemed like a general question to me rather than a Absolute Beginner question. I am sorry if this is in the wrong section. 
--------
I just finished installing Ubuntu 7.10 on an old Compaq w/ a Pentium II, 128MB of RAM and a 10GB HD. The installation took 5 hours... with the text based install. Now it is installed, it is very slow. (OpenOffice.org Writer takes FOREVER (3min+) to run and close.) Is there a way that I can speed it up? The first thought that I had was more RAM, but after opening the System Monitor I discovered the ram was only about 1/2 way used up- but the processor was at 50% or greater with only the system monitor running... do I have to upgrade my hardware to make it faster or is there another way? (Please note this machine is NOT hooked up to the internet.)

Thanks.
-Ian

---

### Post by zach12 on 2007-10-27
Xubuntu
or install openbox

---

### Post by kellemes on 2007-10-27
You should first try another (lighter) windowmanager, like XFCE, Fluxbox, Openbox or another one (not sure what windowmanagers are on the disk)
You can simply install and start another windowmanager from your loginscreen without having to rearrange your hole system, so just try and see if it works for you.

Also it's possible OpenOffice simply is too heavy for this machine.. If you're looking for a very good wordprocessor that's also very light, look at Abiword.
Just use synaptic to browse the Ubuntu-disk for alternative software for this system, there is a lot to choose from.

---

### Post by Ian505 on 2007-10-29
> **kellemes said:**
> You should first try another (lighter) windowmanager, like XFCE, Fluxbox, Openbox or another one (not sure what windowmanagers are on the disk)
You can simply install and start another windowmanager from your loginscreen without having to rearrange your hole system, so just try and see if it works for you.

Also it's possible OpenOffice simply is too heavy for this machine.. If you're looking for a very good wordprocessor that's also very light, look at Abiword.
Just use synaptic to browse the Ubuntu-disk for alternative software for this system, there is a lot to choose from.

AbiWord has, unfortunately, not been scripted for ubuntu x86. I tried to switch to another windows manager and decided it would be easier to simply download Xubuntu. I am going to try that and see how that turns out. 

-Ian

---

### Post by az on 2007-10-29
> **Ian505 said:**
> AbiWord has, unfortunately, not been scripted for ubuntu x86. I tried to switch to another windows manager and decided it would be easier to simply download Xubuntu. I am going to try that and see how that turns out. 

-Ian

There certainly is a version of abiword in the repos.

---

### Post by Ian505 on 2007-10-29
> **az said:**
> There certainly is a version of abiword in the repos.

Huh... weird. I guess the older repo that was on the 7.10 disk is outdated, as it was only available for 64 bit. Sorry bout that. I am going to try xubuntu first though as I am used to OpenOffice and would prefer it. If OpenOffice still wont work then I will happily get AbiWord.

-Ian

EDIT- Disk just finished burnin.

---

### Post by maybeway36 on 2007-10-29
Xubuntu comes with Abiword, but you can install OO.o if you like.

---

### Post by NJC on 2007-10-29
> **Ian505 said:**
> I just finished installing Ubuntu 7.10 on an old Compaq w/ a Pentium II, 128MB of RAM and a 10GB HD. 

I installed Ubuntu 6.06 on a PII/400Mhz but I have 512megs RAM ... I've since upgraded to a neck-snapping PIII/500Mhz and it's slow, but doesn't take 3mins to load OpenOffice.

Try and get more mem if possible. 384 or 512megs is preferable.

---

### Post by altu on 2007-10-30
128 mb ram is not really enough for Ubuntu even if you install openbox. I suggest switching to a distribution that is specifically designed to run on few resources. Before Ubuntu I used to run Vector Linux standard (IceWm  desktop) on a P3@733 with 128 mb ram and it was quite fast. Or you could try DSL.

---

### Post by oldos2er on 2007-10-30
The minimum ram requirement for Ubuntu is 256MB, so I don't doubt your installation is slow.
 I second the nomination for Vector Linux--it's a great distro for older hardware.

---

