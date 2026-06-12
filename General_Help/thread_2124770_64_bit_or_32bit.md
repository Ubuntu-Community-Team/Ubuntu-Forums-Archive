---
title: "64 bit or 32bit?"
date: 2013-03-12
forum: General Help
---

### Post by Baldrick_NZ on 2013-03-12
Hi all,

Not strictly a 13.04 question, but as I'm thinking about testing the 64bit version...

I have a 64bit laptop with 4gb RAM. Would it be best to continue using the 32bit version I'm currently using, or do a fresh 64bit install? What are the benefits & downsides to using 64bit? I have heard that some 32bit software doesn't work with 64bit - if so, are there workarounds?

Cheers.

---

### Post by pinballwizard on 2013-03-12
64bit fresh install ftw.

---

### Post by varunendra on 2013-03-12
> **Baldrick_NZ said:**
> What are the benefits & downsides to using 64bit? I have heard that some 32bit software doesn't work with 64bit - if so, are there workarounds?
The only downside I can think of is that 64 bit uses more memory since operand addresses and address space of instructions are larger. But I don't think it can be a problem if your system meets the minimum requirements for the OS. Since if you don't use too many applications simultaneously, or resource hungry applications then you will never encounter a memory shortage problem. And if you do use them, it will pay back in terms of performance.

I have never seen or heard of any compatibility issues of 32 bit applications with 64 bit Linux for at least last 4 years or more. Either there is always a 64 bit version available, or it is supported. Besides, you can always install 32 bit libraries (approx 3-400 MB in total) on 64 bit Linux where they are explicitly required (like wine). Most often applications automatically install them as dependencies if required.

In short, using 32 bit OS on 64 bit system is using half its potential, while 64 bit brings it to its full potential without issues.
Btw, 4 GB is plenty for normal usage.

---

### Post by varunendra on 2013-03-12
> **Baldrick_NZ said:**
> 
Not strictly a 13.04 question, but as I'm thinking about testing the 64bit version...
*Thread moved to **General Help**.*

---

### Post by c2tarun on 2013-03-12
Varun gave a fantastic answer. Please mark this thread solved.

---

### Post by 3rdalbum on 2013-03-12
The only programs that don't work with 64-bit are certain games console emulators. I have used 64-bit for years and it is fine.

---

### Post by varunendra on 2013-03-12
> **3rdalbum said:**
> The only programs that don't work with 64-bit are certain games console emulators. I have used 64-bit for years and it is fine.
Well I'm not sure about others, but I myself am an addict of PCSX (PS/PS2 emulator) and GFCEU (also have bsnes FCEUX installed and running successfully, all three are NES emulators). And I think I also installed dsmume (DS emulator) mistakenly once. I realized what it is only after running it ;).

So I believe as long as an emulator (or whatever application) comes from a supported repository, it'll work.

But I'd like to know which emulator did you experience problem with, and what was its source?
Just curious (maybe I can discover some PS3 emulator in your reply, lol) :)

---

