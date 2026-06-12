---
title: "Have a question on the amount of RAM and Ubuntu?"
date: 2016-08-30
forum: General Help
---

### Post by irv on 2016-08-30
I read this today:
> Remember that 64-bit Windows 10 Pro, Enterprise, and Education will support up to 2TB of RAM, while the 64-bit version of Windows 10 Home is limited to only 128GB.


After reading this, My Question is how much RAM will Ubuntu 64bit support? Can it handle up to 2TB like Windows 10 Pro? Not that I plan on installing that amount. I am running it on 8GB now and it works great but I find if I am doing research I have two browser windows open and have many tab in both and I find I do slow down at that point. 

I also read this in my searching.
> Ubuntu 64 Bit - A LOT! (Actually 2^64) but because of hardware limits and real world computers the limit is around 1TB ( 1024GB RAM)
Why can't Ubuntu handle 2TB? Is it because of the kernel?

---

### Post by QIII on 2016-08-30
Hello!

Notice that the quote you cited indicates a hardware limitation.

As far as the kernel is concerned, you could buy all the memory in a 10 mile radius of your machine and use it all.

(OK, that's an exaggeration.)

---

### Post by grahammechanical on 2016-08-30
This refers to the CPU architecture.

> Larger physical address space
The original implementation of the AMD64 architecture implemented 40-bit [physical addresses]("https://en.wikipedia.org/wiki/Physical_address") and so could address up to 1 TB (2[SUP]40[/SUP] bytes) of RAM.[SUP][[1]]("https://en.wikipedia.org/wiki/X86-64#cite_note-amd-24593-1")[/SUP][SUP](p24)[/SUP] Current implementations of the AMD64 architecture (starting from [AMD 10h microarchitecture]("https://en.wikipedia.org/wiki/AMD_K10")) extend this to 48-bit physical addresses[SUP][[16]]("https://en.wikipedia.org/wiki/X86-64#cite_note-amd10h-16")[/SUP] and therefore can address up to 256 TB of RAM. The architecture permits extending this to 52 bits in the future[SUP][[1]]("https://en.wikipedia.org/wiki/X86-64#cite_note-amd-24593-1")[/SUP][SUP](p24)[/SUP][SUP][[17]]("https://en.wikipedia.org/wiki/X86-64#cite_note-17")[/SUP] (limited by the page table entry format);[SUP][[1]]("https://en.wikipedia.org/wiki/X86-64#cite_note-amd-24593-1")[/SUP][SUP](p131)[/SUP] this would allow addressing of up to 4 [PB]("https://en.wikipedia.org/wiki/Pebibyte") of RAM. For comparison, 32-bit x86 processors are limited to 64 GB of RAM in [Physical Address Extension]("https://en.wikipedia.org/wiki/Physical_Address_Extension") (PAE) mode,[SUP][[18]]("https://en.wikipedia.org/wiki/X86-64#cite_note-shanley-ppro-18")[/SUP] or 4 GB of RAM without PAE mode.[SUP][[1]]("https://en.wikipedia.org/wiki/X86-64#cite_note-amd-24593-1")[/SUP][SUP](p4)[/SUP]


[https://en.wikipedia.org/wiki/X86-64](https://en.wikipedia.org/wiki/X86-64)

For Ubuntu there is this

> Its the architecture of the kernel. The release is irrelevant.

 32bit Ubuntu can access up to 3.4Gb
32Gb Ubuntu + PAE can access to 64Gb RAM
64Gb Ubuntu up to 4Eb but in real world it's going to be about 1Tb...



[https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/200916](https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/200916)

Exabyte? 

[https://en.wikipedia.org/wiki/Exabyte](https://en.wikipedia.org/wiki/Exabyte)

An indication of what the Linux kernel is capable of

[https://access.redhat.com/articles/rhel-limits](https://access.redhat.com/articles/rhel-limits)

Regards

---

### Post by irv on 2016-08-30
On the last link you posted, it said,
> Red Hat Enterprise Linux 6.7 is required for support of 12TB of RAM. Red Hat Enterprise Linux 6.6 can support up to 6TB of RAM. Previous versions of Red Hat Enterprise Linux 6, starting with Red Hat Enterprise Linux 6.3, support up to 3TB of RAM. Versions of Red Hat Enterprise Linux prior to Red Hat Enterprise Linux 6.3 support up to 1TB of RAM.
Is Red Hat using a different kernel? or is this just a version number of Red Hat Linux? It is so long since I used Red Hat, over 10 years now. It looks like Red Hat can support more memory then Ubuntu.

---

### Post by grahammechanical on 2016-08-30
The most important thing that I know about Red Hat is that it is a paid for version of Linux. What we could be seeing is a marketing ploy to get server users to upgrade to newer versions of Red Hat in a similar approach to what we see with Microsoft.

Different versions of distributions use different (newer) Linux kernels. This is true also of Ubuntu. But I think that the quote from Launchpad shows that Linux itself has great capacity for accessing memory but there are practical reasons for a limit. I can only guess that motherboard hardware limits might be a practical reason.

I found this about the Titan super computer that runs a hybrid Linux.

> Titan has 18,688 nodes (4 nodes per blade, 24 blades per cabinet),[SUP][[38]]("https://en.wikipedia.org/wiki/Titan_%28supercomputer%29#cite_note-spots-38")[/SUP] each containing a [16-core]("https://en.wikipedia.org/wiki/Multicore_processor") [AMD Opteron 6274]("https://en.wikipedia.org/wiki/Opteron") CPU with 32 GB of [DDR3]("https://en.wikipedia.org/wiki/DDR3_SDRAM") [ECC memory]("https://en.wikipedia.org/wiki/ECC_memory") and an Nvidia Tesla K20X GPU with 6 GB [GDDR5]("https://en.wikipedia.org/wiki/GDDR5") ECC memory.[SUP][[39]]("https://en.wikipedia.org/wiki/Titan_%28supercomputer%29#cite_note-olcf_debut-39")[/SUP] There are a total of 299,008 processor cores, and a total of 693.6 TiB of CPU and GPU RAM

[https://en.wikipedia.org/wiki/Titan_(supercomputer)](https://en.wikipedia.org/wiki/Titan_(supercomputer))

Regards

---

### Post by yancek on 2016-08-30
Red Hat is always several versions behind with it's kernel.  Release 7.0 is now using the 3.10 kernel while many Desktop Linux systems are in the 4+ kernel. 
Red Hat focuses on stability and servers and given the fact that almost all Red Hat installations are used in commercial enterprises, I would think the amount of RAM used would be much more than standard Desktops and the hardware used would also be different.  I doubt you would be able to run the servers at the New York Stock Exchange ,which use Red Hat, on 1-2GB of memory which will work for most Desktop installs.  I think it probably relates more to the hardware used but I don't really know.

[https://techcrunch.com/2014/06/10/red-hat-enterprise-linux-7-0-is-here-guarantees-10-years-of-compatiblity/](https://techcrunch.com/2014/06/10/red-hat-enterprise-linux-7-0-is-here-guarantees-10-years-of-compatiblity/)

[http://www.pcworld.com/article/238068/how_linux_mastered_wall_street.html](http://www.pcworld.com/article/238068/how_linux_mastered_wall_street.html)

---

### Post by HermanAB on 2016-08-30
Well, consider that almost all super computers run Linux:
[https://www.top500.org/](https://www.top500.org/)

---

### Post by irv on 2016-08-31
With all that was said, I think I will mark this thread solved because we can all agree that hardware is the driving factor. And yes many supercomputers run Linux. The max amount of RAM for my system is 16GB two slots that will take up to 8GB each. So even if Linux can go higher my system will not.

---

### Post by kurt18947 on 2016-08-31
If you want to read about some interesting hardware, check out the specs on IBM's Watson as seen on Jeopardy a few years ago. I think typical Linux kernels support around 256 processor cores. Watson  was a case where I imagine "they had to compile their own kernel", one  of the venerable bits of FUD about linux.


[URL="http://www.ibmsystemsmag.com/ibmi/trends/whatsnew/It%E2%80%99s-Technical,-Dear-Watson/"]http://www.ibmsystemsmag.com/ibmi/trends/whatsnew/It%E2%80%99s-Technical,-Dear-Watson/
[/URL][INDENT]
In part:

[LIST]
[*]The Power 750 uses a 3.5 GHz POWER7 eight-core processor, with four threads per core. Watson has a total of 2,880 POWER7 cores
[*]The cluster has a total of 16 Terabytes of RAM. The file system containing all of Watson's data is on 4 Terabytes of disk. 
[*]When Watson starts up, much of the data on the disk is loaded into memory and replicated across many servers in the cluster. 
[*]In order to be fast, all of Watson's knowledge must be loaded into memory. 
[/LIST]
 
[LIST]
[*]Like many other high performance computing workloads, Watson's DeepQA software runs on Power Linux 
[/LIST]

I'm not sure why they didn't just use Windows. :lolflag: 
[/INDENT]

---

### Post by mörgæs on 2016-09-01
> **grahammechanical said:**
> The most important thing that I know about Red Hat is that it is a paid for version of Linux. What we could be seeing is a marketing ploy to get server users to upgrade to newer versions of Red Hat in a similar approach to what we see with Microsoft.



This is most likely the explanation. Microsoft (as mentioned in original post) has a long tradition of limiting which hardware resources are available to the user. If you want to see and utilise the memory which you have already bought then you need to buy one of the more expensive Windows licenses atop of it.

---

