---
title: "Installing Ubuntu on Mac mini"
date: 2007-02-26
forum: General Help
---

### Post by ubix on 2007-02-26
Last year I bought **Mac mini** to try it out. I have since decided to load Ubuntu on it. However there is a problem. In order to load Ubuntu from a CD one needs to make the CD bootable. Unfortunately, after the Ubuntu is installed, there is no way to start it from  the HD, since hardware is now set to boot from the CD, and one has no way of changing Mac's equivalent of  "CMOS" without the [COLOR="Blue"]**MacOS**[/COLOR] installed.

Does anybody have solution for my problem?

---

### Post by crispy_420 on 2007-02-26
What CPU (Intel or PPC) do you have? You may have better luck posting in the PPC user section [here]("http://ubuntuforums.org/forumdisplay.php?f=133").

---

### Post by ubix on 2007-02-27
My **Mac mini** has [COLOR="Blue"]**Intel**[/COLOR] CPU. 

I've made a significant progress since my original post. I've managed to partition disk so MacOS sits in first two partitions, the rest I've sliced up in a Linux manner and installed Ubuntu nicely. However writing **grub** in (hd0) blows  up.

Additional complication is that the disk is scsi (/dev/sda0 through /dev/sda15). The first partition is marked bootable. Due to the above mentioned problem writing grub, I suspect MacOS does not use the MBR at all. I'll try installing grub in a few different places, hopefully one will work.

---

### Post by ubix on 2007-03-03
This thread needs a conclusion, which I came up with in another post on this forum, when I in exuberance and happiness revealed what I learned in the process of getting my Linux working over a dozen partitions rather than, as officially advertised, just two.

So I'm re-publishing the same thing again:

[INDENT][I]> **wpshooter said:**
> I was just talking to someone from Apple computers and they told me that Ubuntu would NOT run on their laptop computers !!!

Do they know what they are talking about ?

Thanks.:lolflag: 

Indeed, they do know very well, what they are talking about, the question is do we (you) understand them? The trouble with Apple is their compliance with a disk organization schema, which is based on **GUID Partition Table (GPT)** rather than on _**Master Boot Record (MBR)** used with BIOS_.

GUID Partition Table (GPT) is a standard for the layout of the partition table on a physical hard disk. It is a part of the [COLOR="Blue"]Extensible Firmware Interface (EFI) standard proposed by Intel[/COLOR] as a replacement for the outdated PC BIOS. The GPT replaces the Master Boot Record (MBR) used with BIOS.

Therefor, there are two different architectures here to deal with, and **Linux** understands them both. Trouble is that GRUB and LILO are not perfectly aware of these two disk schemmas, and they do not handle "BIOS-less" **PowerPC** at all. However, Linux comuniti has addressed this issue long ago, and one can install Linux on PowerPC's too. There is an equivalent of BIOS-aware GRUB which we use on Intel platforms, for **PowerPC**s which is called [COLOR="Blue"]**yaboot**[/COLOR]. It is the Macintosh Open-Firmware loader.

Apple is trying to make it hard to put any Linux on their hardware, by exploiting the two OS Platforms and the two disk schemas, which gives them 4 different combinations for setups and installation instructions. Some of these are addressed here: [http://r[COLOR="Red"]**EFI**[/COLOR]t.sourceforge.net/myths]("http://rEFIt.sourceforge.net/myths"), **however, though they provide us with sufficient info to investigate this issue further, some of their facts are plainly wrong!**

So far it is possible to install Linux on all contemporary Apple hardware, and I believe it will continue to be so, in fact I believe things will get better, when GRUB and LILO loaders will be made aware of EFI disk layout. [COLOR="Blue"]Apple will have trouble preventing other OSes to run from their hardware, unless, they will intentionally modify requirements suggested by  the Extensible Firmware Interface (EFI) standards.[/COLOR] ;)  :biggrin: ):P[/I][/INDENT]

---

### Post by ubix on 2007-03-07
[CENTER][SIZE="6"][COLOR="Blue"]Dual boot on Mac Mini works[/COLOR][/SIZE][/CENTER]

I need to correct myself here and bump up this thread, because of new discoveries. See: [http://ubuntuforums.org/showthread.php?p=2260529#post2260529](http://ubuntuforums.org/showthread.php?p=2260529#post2260529)  :) :) :)

---

### Post by ubix on 2007-03-12
There is now detailed description of how to install Ubuntu on Apple computers, including a discussion about different partitioning schemes relevant to Apple platforms as well as installation paths to create a simple one partition or multiple partition Ubuntu installation.  See: [UbuntuOnApple]("http://doc.gwos.org/index.php/UbuntuOnApple") :)

---

