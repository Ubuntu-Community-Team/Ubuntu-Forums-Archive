---
title: "Avoiding Bad Memory"
date: 2013-05-04
forum: General Help
---

### Post by Jack Waugh on 2013-05-04
When I use my favorite search engine to find what people have written about starting Linux in such a way as to make it skip using some area of memory known to be bad, I have seen at least a couple of ways described.  There's a variable you can set in /etc/default/grub that according to the comments in there will do that, although I haven't seen a clear explanation of the mechanism whereby this is supposed to take effect.  Alternatively, some people write, you can put a memmap=<size>$<address> specification on the kernel command line.  Evidently the two methods conflict with one another, because when I try both at once, my kernel hangs with a blank screen somewhere in getting started.

Now my question is, with either of these methods (or any other you recommend with Ubuntu), how can I verify that the kernel has indeed indicated the memory location in question from some table or structure such that the location won't be used?

---

### Post by tgalati4 on 2013-05-04
If your computer stays up for a month, then you can be reasonably sure it is not using that memory location.

There are a few tools in the repositories:

tgalati4@Mint14-Extensa ~ $ apt-cache search read memory location
libio-string-perl - Emulate IO::File interface for in-core strings
bowtie - ultrafast memory-efficient short read aligner
bowtie-examples - Examples for bowtie, the ultrafast memory-efficient short read aligner
devmem2 - simple program to read/write from/to any location in memory
electric-fence - A malloc(3) debugger
jvm-7-avian-jre - lightweight virtual machine using the OpenJDK class library
libtinyxml2-0.0.0 - C++ XML parsing library
libtinyxml2-dev - TinyXML2 library - header and static library
mutrace - mutex and realtime memory allocation profiling tools
nvramtool - Read/write coreboot-related NVRAM/CMOS information
sysbench - Cross-platform and multi-threaded benchmark tool

*devmem2* looks interesting.  Try writing through the protected area and then read it back.

Otherwise you would have to write a small program to do the same with *malloc*:  

```
man malloc
```

---

### Post by Jack Waugh on 2013-05-05
To answer my own question:

In GRUB, I edited the kernel command line to say "memmap=8\$0x791a224".  REEEEEEEEE-ZULT????

After logging in, I run "dmesg | less" and observe:

[    0.000000] user-defined physical RAM map:
. . .
[    0.000000]  user: 0000000000100000 - 000000000791a224 (usable)
[    0.000000]  user: 000000000791a224 - 000000000791a22c (reserved)
[    0.000000]  user: 000000000791a22c - 000000001ffc0000 (usable)

So we can see that the kernel is acknowledging my command to exclude the bad memory location.  Thank you, kernel maintainers; thank you, Linus Torvalds.  From you according to your ability, to me according to my need.

---

