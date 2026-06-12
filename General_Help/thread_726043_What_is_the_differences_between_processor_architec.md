---
title: "What is the differences between processor architectures?"
date: 2008-03-16
forum: General Help
---

### Post by MONODA on 2008-03-16
Could someone list them all (or just some) with a description and how they are different thanks.
EDIT: Also what is the differences between 32 bbit and 64 bit processors?

---

### Post by eldragon on 2008-03-16
CPU architectures are related to what "language" the cpu understands (instruction set)

the most known one is the X86 instruction set.(from your at computer to today), difference is they have been adding extensions to the instruction set with newer processors.

you get from i386, to todays (dont know the name) X86. (extensions usually have a name, like 3dnow, mmx, SSE1, SSE2, SSE3 etcetera).

32 / 64 bit is the size of their data bus. how many chunks of bits can the processor process at a given time.

thats why they say a cpu cant get more than 4gb of ram, because having 32 bits to decode the address of a given byte, it can only address 4gb of ram (2^32 = 4gb )

i hope im clear enough.

---

### Post by Sef on 2008-03-16
> 32 / 64 bit is the size of their data bus. how many chunks of bits can the processor process at a given time.

thats why they say a cpu cant get more than 4gb of ram, because having 32 bits to decode the address of a given byte, it can only address 4gb of ram (2^32 = 4gb )

64-bit systems can use up to [16.8 million tetrabytes]("http://en.wikipedia.org/wiki/64-bit").

---

### Post by jayson.rowe on 2008-03-16
One other factiod to note, is that AMD64 versions of Windows and Linux are really only 40-bit operating systems. The original AMD64 processors started off as 40-bit but are the newer AMD64 and EM64T processors are 48-bit. The theoretical maximum of a full 64-bit address space is 2^64, or 16 exabytes (1.6×1019), however current AMD64 operating systems actually only use 40 bits for addressing memory, yielding an address space of 2^40, or 16 TB.

---

### Post by eldragon on 2008-03-16
> **jayson.rowe said:**
> One other factiod to note, is that AMD64 versions of Windows and Linux are really only 40-bit operating systems. The original AMD64 processors started off as 40-bit but are the newer AMD64 and EM64T processors are 48-bit. The theoretical maximum of a full 64-bit address space is 2^64, or 16 exabytes (1.6×1019), however current AMD64 operating systems actually only use 40 bits for addressing memory, yielding an address space of 2^40, or 16 TB.

you are definately mixing up virtual memory vs physical memory.

the real physical memory address is 64bit, but the virtual memory system is set to 40bit. something related to not needing to address that much ;)

theres nothing stopping an operating system update that uupdates to 64bit virtual memory usage. but dont quote me on this. :lolflag:

---

### Post by jayson.rowe on 2008-03-16
> **eldragon said:**
> you are definately mixing up virtual memory vs physical memory.

the real physical memory address is 64bit, but the virtual memory system is set to 40bit. something related to not needing to address that much ;)

theres nothing stopping an operating system update that uupdates to 64bit virtual memory usage. but dont quote me on this. :lolflag:

Definitely not "mixing up" Virtual Memory and Physical Memory.

Operating systems don't really differentiate between Virtual Memory and Physical Memory - the only thing that matters to an OS is the Address Space (which is 40-bits in current x86-64 operating systems).

You might want to read through these articles...

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

---

### Post by eldragon on 2008-03-17
i stand corrected, thanks for the info ;)

---

