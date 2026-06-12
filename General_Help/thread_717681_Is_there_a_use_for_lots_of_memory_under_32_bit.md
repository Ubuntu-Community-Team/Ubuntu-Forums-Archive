---
title: "Is there a use for lots of memory under 32 bit?"
date: 2008-03-07
forum: General Help
---

### Post by starbase1 on 2008-03-07
Hello All!
I am putting together my first box that is primarily Ubuntu, and expect to run quite a few things under XP in a VM, while I wean myself away.

I understand from searching that 64 bit has quite a few issues that are not there with 32 bit Ubuntu, so it would seem very sensible to start with that.

But if course the 32 bit one can only directly address 4 Gb of memory, and I think my setup will be memory hungry - and memory is rather cheap right now.

So my question is, can I use more than 4 Gb to speed my system up in any way, or is the 4 Gb constraint deeper than that?

For example, it occurs to me that back in the days when an Atari St was state of the art, I could have what I used to call a 'Ram Disk' - in other words, a chunk of memory configured to look and act like a super fast hard drive.

If this is possible I suspect that putting the virtual machine files into a ram disk would help things fly along really quickly...

Nick

---

### Post by cdenley on 2008-03-07
> I understand from searching that 64 bit has quite a few issues that are not there with 32 bit Ubuntu
The only problems I have ever had with 64-bit has been with desktop stuff like flash, windows media codecs, or wine. If you're running a server, I would use 64-bit.

For the "ram disk", I think what you are looking for is tmpfs.
```

sudo mkdir /ram
sudo mount -t tmpfs tmpfs /ram

```
I'm not sure how much of an improvement this would be over disk caching.

---

### Post by DrMega on 2008-03-07
You might find that your motherboard is physically unable to address more than 4GB. The 4GB address limit is there because the often the address bus is 32 bits wide, allowing 2^32 unique addresses (ie 4GB).

Even if you have a 64bit processor, it doesn't necessarily follow that your mobo will use a 64bit address bus, so you should check this before investing in tonnes of memory.

---

### Post by starbase1 on 2008-03-07
> **DrMega said:**
> You might find that your motherboard is physically unable to address more than 4GB. The 4GB address limit is there because the often the address bus is 32 bits wide, allowing 2^32 unique addresses (ie 4GB).

Even if you have a 64bit processor, it doesn't necessarily follow that your mobo will use a 64bit address bus, so you should check this before investing in tonnes of memory.

Thanks, I checked the motherboard and it says it can use 8 Gb. (It's a very new one).

I just find the idea of a home system with that much memory pure hardware porn!
:twisted:

---

### Post by starbase1 on 2008-03-07
> **cdenley said:**
> The only problems I have ever had with 64-bit has been with desktop stuff like flash, windows media codecs, or wine. If you're running a server, I would use 64-bit.

For the "ram disk", I think what you are looking for is tmpfs.
```

sudo mkdir /ram
sudo mount -t tmpfs tmpfs /ram

```
I'm not sure how much of an improvement this would be over disk caching.
 
Thanks for that, I'm get busy with google to find more about tmpfs.
Would that come out of the 4 Gb addressable space under 32 bit?

It's not for a server, it's for a desktop where I plan on doing lots of 3d graphics type stuff.

Nick

---

### Post by cdenley on 2008-03-07
I think that tmpfs would be restricted by memory access limitations, and would come from the 4GB available. I don't think there would be any way to get around it, except maybe recompiling the kernel. Unless you are using some proprietary software or drivers that don't compile for 64-bit systems, I wouldn't expect any problems with 64-bit.

---

