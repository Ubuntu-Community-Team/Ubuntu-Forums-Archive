---
title: "core 2 duo 32 vs 64."
date: 2007-05-21
forum: General Help
---

### Post by earobinson on 2007-05-21
I know for a fact that this has all ready been posted but try as I might I cant seem to find the post. I have seen a few users who installed the 32 bit version of ubuntu on there core 2 duo computer instead of the 64 bit version. I have a few questions.

1. How much performance are they losing?
2. Can they upgrade to 64 without a reinstall?
3. Anything else I should know?
4. How stable is 64 vs 32?

---

### Post by blazercist on 2007-05-21
there will be no noticable difference in performance assuming that your machine has less than 4GB or memory, at least i think its 4?  they are saving themselves alot of hassle as far as driver go, the 64 bit ones are either buggy or non-existant.

No there is no easy way to switch from 32 to 64 bit, it is not recommended and it is extremely messy and involves changing just about every file that is relevant to the core system and is simply not worth doing.

---

### Post by srt4play on 2007-05-21
Go with the 32-bit version and save yourself some headache.

---

### Post by dexter on 2007-05-21
> **blazercist said:**
>  they are saving themselves alot of hassle as far as driver go, the 64 bit ones are either buggy or non-existant.


Not only drivers, many packages aren't available for a 64 bit os. In my opinion the "benefits" of a 64 bit os don't outweigh the misery you have to solve to get all the software you need.

---

### Post by stchman on 2007-05-21
> **earobinson said:**
> I know for a fact that this has all ready been posted but try as I might I cant seem to find the post. I have seen a few users who installed the 32 bit version of ubuntu on there core 2 duo computer instead of the 64 bit version. I have a few questions.

1. How much performance are they losing?
2. Can they upgrade to 64 without a reinstall?
3. Anything else I should know?
4. How stable is 64 vs 32?

I agree, drivers and packages that are 64bit are pretty sparse.  Once the drivers and packages give full 32 bit support then 64 bit will be worth it.

---

### Post by earobinson on 2007-05-21
Thanks for all the great replys guys

anyone know what you loose out on by running the 32 bit version?

---

### Post by Crakie on 2007-05-21
What they said. 64-bit is the future, but it's hardly worth it to run it at the moment. Not that I am particularly fond of flash, though *nudge**nudge*

---

### Post by earobinson on 2007-05-21
> **Crakie said:**
> Not that I am particularly fond of flash, though *nudge**nudge* I dont get it. Well I know that, I was talking about now, is there any advantage to running the 64 bit version, is the speed advantage big? do you get more cpu options? ....

---

### Post by blazercist on 2007-05-21
like i said the only advantage that i'm aware of is that 64 bit systems can handle more memory than 32 bit systems, i think 32 bits are capped at 4GB or maybe its 8GB, either way no home comp is going to have that much memory anyway...  its the same story as with dual core processors, yea sure itll help if you multi-task a bunch of light apps because the system will spread the load across both cpus, but if you are trying to run one monster app you are double-screwed because it isnt multi threaded and each of your cpus has got half the power of a normal one.  Maybe in a few years it will actually be worth having these.

---

### Post by timblech on 2007-05-23
well, the advantage i see with x64_64 machines is not the larger virtual address space for accessing more ram, but rather the register extensions, as x86_64 provides both more general purpose and more xmm registers than x64 ...

---

### Post by mikewhatever on 2007-05-23
You'll probably notice some advantage in doing CPU heavy tasks like video editing etc, even with less then 4 GB of RAM.

---

### Post by iggyboy on 2007-05-23
I have install 64bit version a few times (Dapper & Fiesty), but in the end always end-up with the 32bit version, as some said before, including my personal experiance, its simply not worth the head-ache if you are just going to use it for general purpose use.

Even if you manage to fix most of the problem that may arise during the 64bits installation but there isn't any real performance difference that one can feel. Occasionally I do video conversion but both 32 and 64 bits come about the same.

The real advantage, I personally gain is.... I came to know more about Linux, (originally I'm a hardcore Windows user and started with 64bits Dapper) tweaking, fixing and going through HOW-TOs really make me understand the structures of Linux OS and how it actually works.

Regards:)

---

### Post by Necreia on 2007-05-23
32-bit is capped at 2GB of ram per process.  The max RAM you'll see in the machine is anywhere from 3-4 (depends on other hardware / motherboard / addressing).

I use 64Bit because I have 4 gigs of ram and didn't want either the overhead or the hassle to make it all register properly.  As for the driver problems, I've had none that others experience.  The only 'headache' was getting flash to work properly and there's a tutorial here.

Performance wise you won't see much improvement unless you run native 64 bit applications (stuff you compile yourself or whatnot).  Depending on what it is and what you do, however, it can be a gigantic improvement.

---

### Post by ebash on 2007-05-23
> **Necreia said:**
> 32-bit is capped at 2GB of ram per process.
This is not exactly true, a 32-bit Linux kernel can reference 4 GB of physical memory per process. Although, since the OS also needs memory in order to manage a process the maximal amount of memory allowed to use in a process is 3GB for the process data and 1GB for the process maintenance.

Although, having a single process take 4 GB of memory is quite exceptional and rarely occurs in personal desktops and workstations, with servers this is another story. 

This page explains more in details how much memory can be used by a 32-bit kernel:  [http://kerneltrap.org/node/2450]("http://kerneltrap.org/node/2450")

---

### Post by earobinson on 2007-05-23
Neat, It would seem that there is a general consensis that 32bit is currently the way to go.

---

### Post by Prisma on 2007-05-29
Yes we have to wait until the Linux community develops native 64 bit applications. I think the upcoming Linux video editing applications will benefit tremendously running in 64bits

---

### Post by earobinson on 2007-05-29
Im pretty sure the next version of windows will be 64 bit only so that will give us a push in the right direction

---

