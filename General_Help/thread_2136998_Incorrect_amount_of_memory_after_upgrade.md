---
title: "Incorrect amount of memory after upgrade"
date: 2013-04-19
forum: General Help
---

### Post by kkelly77 on 2013-04-19
I'm running Ubuntu 12.04 on a HP Compaq nc8430.

I've just increased the memory from 2Gb to the max of 4Gb. In the BIOS the amount of memory showing is 4Gb and memory test passed OK. However, when I check how much memory is installed in the System Details, it is only showing 3.3Gb. 

[IMG]http://i48.tinypic.com/ajpcwj.jpg[/IMG]

Anyone know why this is? Thanks.

---

### Post by Elfy on 2013-04-19
32bit with a non pae kernel I'd suspect

---

### Post by kkelly77 on 2013-04-19
[IMG]http://i48.tinypic.com/4hqyau.jpg[/IMG]

Kernel 3.2.0-40 generic pae

It is a 32 bit CPU I have. Does this mean I can't make use of the full 4Gb?

---

### Post by mörgæs on 2013-04-19
How does it look in a 64 bit live boot?

The T5600 is a 64 bit CPU:
[http://ark.intel.com/products/27254/Intel-Core2-Duo-Processor-T5600-2M-Cache-1_83-GHz-667-MHz-FSB](http://ark.intel.com/products/27254/Intel-Core2-Duo-Processor-T5600-2M-Cache-1_83-GHz-667-MHz-FSB)

---

### Post by kkelly77 on 2013-04-19
> **mörgæs said:**
> How does it look in a 64 bit live boot?

The T5600 is a 64 bit CPU:
[http://ark.intel.com/products/27254/Intel-Core2-Duo-Processor-T5600-2M-Cache-1_83-GHz-667-MHz-FSB](http://ark.intel.com/products/27254/Intel-Core2-Duo-Processor-T5600-2M-Cache-1_83-GHz-667-MHz-FSB)

Ah dammit!!! I was sure it was a 32 bit when I installed Ubuntu. I'll try a 64 bit live CD and see what it says.

---

### Post by kkelly77 on 2013-04-19
> **kkelly77 said:**
> Ah dammit!!! I was sure it was a 32 bit when I installed Ubuntu. I'll try a 64 bit live CD and see what it says.

Looks the same booting off a 64 bit live USB

[IMG]http://i35.tinypic.com/2rhmirb.png[/IMG]

---

### Post by mörgæs on 2013-04-19
It's likely to be reserved for graphics card and other peripherals. If you google "3.3 GB Ubuntu" you will find many similar threads.

Good news is that you are not likely to need more than 3.3 GB anyway unless you are a very demanding user.

---

### Post by kkelly77 on 2013-04-19
> **mörgæs said:**
> It's likely to be reserved for graphics card and other peripherals. If you google "3.3 GB Ubuntu" you will find many similar threads.

Good news is that you are not likely to need more than 3.3 GB anyway unless you are a very demanding user.

Thanks for your help [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")

I will have a search for 3.3Gb Ubuntu as you suggested.

---

