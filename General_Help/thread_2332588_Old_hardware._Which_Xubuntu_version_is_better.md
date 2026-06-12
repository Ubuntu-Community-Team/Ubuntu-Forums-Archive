---
title: "Old hardware. Which Xubuntu version is better?"
date: 2016-08-01
forum: General Help
---

### Post by stas7 on 2016-08-01
Good day,
I would like to install Xubuntu on old Gateway DX4200-09 desktop. Its specs are here (it seems to be in stock configuration, no discrete graphics card):
[http://www.cnet.com/products/gateway-dx4200-09/specs/](http://www.cnet.com/products/gateway-dx4200-09/specs/)

I choose Xubuntu, because I use it on a virtual machine and its the only distribution of Linux I have experience (my main OS win7). Which version of Xubuntu is better for such an old PC?
Can I install the latest version of Xubuntu?
The PC will be used mostly for web-browsing and C++ development (with Eclipse).
Thank you.

---

### Post by kansasnoob on 2016-08-02
This may be a problem with Xenial:

> 
Graphics Processor = ATI Radeon HD 3200


[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

But I'd still try it because Xubuntu Trusty will reach EOL next April. Xenial will be supported for two years longer so I'd give it a try.

---

### Post by QIII on 2016-08-02
Not really much of a problem.  The Radeon driver -- which is much, much improved over a few years ago -- will be used by default.  Other GPUs (such as my R9 380X) default to the AMDGPU driver.

The Radeon driver is just fine.  In fact, since AMD stopped supporting the AMD graphics adapter the OP has several years ago, the Radeon driver would have been all that would have worked anyway.  fglrx would not work with that adapter after 12.04.1.

---

### Post by Bucky Ball on 2016-08-02
That'll work. If nothing else, it still has a 7200rpm hard drive (unless that's been swapped out)!

You might want to try [Xubuntu-core 16.04 LTS]("http://xubuntu.org/news/introducing-xubuntu-core/") for extra zip, and if you don't mind spending a little extra time setting it up. See the community ISOs at the bottom of the page.

Chuck an SSD in there and with Xubuntu, or Xubuntu-core, it'll be reborn!

---

### Post by kurt18947 on 2016-08-02
That machine is quite similar to my desktop "daily driver". It should run any *buntu flavor you wish. My MoBo has integral AMD 4200HD video and the default Radeon driver seems perfectly adequate and stable for typical desktop usage. I'm not a gamer or heavy graphics user so can't comment there. full screen Flash or HTML5 video plays smoothly.

---

### Post by Yellow Pasque on 2016-08-02
I don't see any reason to use an older version (< 16.04) on this machine. It's not terribly old.

---

### Post by Bucky Ball on 2016-08-02
> **Temüjin said:**
> I don't see any reason to use an older version (< 16.04) on this machine. It's not terribly old.

+1. You should be able to sling Ubuntu 16.04 LTS at this if you wanted. The link says it has 4Gb of RAM and that is plenty. 

Avoid older releases. Additionally, interim (non-LTS) releases only have nine months support.

---

### Post by gordintoronto on 2016-08-02
Xubuntu 16.04 64-bit should work very nicely on this PC.

---

### Post by stas7 on 2016-08-24
Thank you all guys! I decided to get an SSD first, so it took me some time to choose it (actually still waiting for delivery). Will go with [COLOR=#000000]Xubuntu 16.04 64-bit[/COLOR]

---

### Post by stas7 on 2016-08-29
I am sorry for starting it again. I need to work with microsoft documents (word and excel docs), so I will likely need to install Openoffice. Does Xubuntu allow this?
May be I should go with Ubuntu? Just afraid that CPU is too slow, especially in single thread performance, so not sure if 4-cores will help. I believe Ubuntu graphics interface is much havier than in Xubuntu, right?
I just put 120gb SSD Crucial M4 into this computer and RAM now 6GB.

---

### Post by Bucky Ball on 2016-08-29
Xubuntu comes default with Libreoffice (from memory) which is pretty much identical to Openoffice in just about every way. They are closely related. Go with that. You won't see a difference.

If for some reason you really MUST use OO then, yes, it's in the software repositories, but doesn't play with Libreoffice so you need to remove first. There are how-to pages on how to do this. If you look you'll find.

---

### Post by stas7 on 2016-08-30
Thank you for reply. I decided to give Ubuntu 16 LTS a chance, and I am surprised how well it works on such an old CPU:) It also comes with [COLOR=#000000]Libreoffice. 
[/COLOR]For excel I mainly need to work with csv files. Is there a format that is well supported both by [COLOR=#000000]Libreoffice and Excel?
[/COLOR]I have another windows 7 machine, which is actually my primary.
I am slightly worried I gave to few space for / partition. Its 30GB total, and I have 12GB used (already installed some soft). I created seperate /home partition on the same drive and 6GB swap partition.

Will I be able to resize / partition if I will be out of space by downsizing /home (or moving /home to HDD)?
The space on SSD is only 120GB, though I can put there as many HDDs as I need:) The old HDD that came with this PC is not used by linux at all now.
If its not possible than I should do it right now, before I spend too much time on configuring etc.

---

### Post by Bucky Ball on 2016-08-30
Your partitioning is just fine. Your personal data is going to the /home partition. Only apps are going to / and a few other things. You only really need 2Gb for RAM but that is by the by. You'll find you won't need to resize the / partition.

For Excel, open Libreoffice and create a new Libreoffice Calc document. If you have the full Libreoffice installed you have Calc installed, too. If you double-click a .csv it may open it for you or ask what you want to open it with.

---

### Post by kurt18947 on 2016-08-30
It may depend on your .csv file source. I've dealt with account info downloaded from a bank in .csv format that does not open properly in LibreOffice Calc. I've opened .csv files from other sources that open perfectly. I haven't looked at it carefully. I've had problems printing .pdf documents from that bank in Firefox as well; I've had to download the .pdf then open and print in Evince. I'm not sure why it's just that one bank; they're probably still on Windows XP and I.E. 6 (they _were_ on XP desktops until a year or so ago)

---

### Post by stas7 on 2016-08-31
> **Bucky Ball said:**
> Your partitioning is just fine. Your personal data is going to the /home partition. Only apps are going to / and a few other things. You only really need 2Gb for RAM but that is by the by. You'll find you won't need to resize the / partition.


I am working on scientific computing code, which may take lots of RAM. Thats why I made 6gb swap. Will not use this PC for final computations of course, just for code testing runs.

---

