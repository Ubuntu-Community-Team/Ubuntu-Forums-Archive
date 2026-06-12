---
title: "Put Ubuntu on new laptop"
date: 2007-05-10
forum: General Help
---

### Post by MacPC on 2007-05-10
Hello,

I want to buy a inexpensive laptop., an ACER Aspire 3680-2633. The reason I pick this machine is because of the price - on sale for only $399.00. 

What I want to do after getting it is to ditch the Vista crap and install Ubuntu, using the Ubuntu as a host to install VMware server. Then I will install and run  Windows XP on the VM. This way I can run dual OSs. My only concern is that whether Ubuntu supports all the hardware of this laptop. How and where can I find out?

Thanks.

MacPC

---

### Post by starcraft.man on 2007-05-10
[VOILA!]("https://wiki.ubuntu.com/HardwareSupport?highlight=%28support%29%7C%28hardware%29")

Long as its not an ATI card, and you don't have one of those blasted Vista only phoenix bios you should be fine. There are some labtop models listed, otherwise just look for your specs.

---

### Post by tommcd on 2007-05-10
Here's another good resource for linux on laptops:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/) Unfortunately, this mostly has older laptops and not a lot of current models that you are likely to find in stores.
You can also google "name_of_laptop linux" to look for linux compatibility info.

---

### Post by TheMono on 2007-05-10
To be honest with you, at that price it will probably have intel graphics and an older chipset, both of which are great for linux. However, it will probably have a broadcom wireless card, which isn't great. 

Those guesses are stabs in the dark though.

---

### Post by CyberBob on 2007-05-27
I just bought two of these last week - a great deal at $399!

Don't have my wireless working yet though - here is the output of lspci - v


03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: fast devsel, IRQ 17
        Memory at 34100000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

---

### Post by loathsome on 2007-05-27
The *best* way to find out if Ubuntu supports the hardware properly, is to simply boot up the LiveCD.

Yeah, might be a bit hard when you don't have the laptop though .. :-P

---

### Post by MacPC on 2007-05-27
Hi,

Thanks all for your reply.

I think I will save up the money for now and get a nice MacBook, that way I can a have OSX, Ubuntu and the crappy Windos BS. Three OSs on one laptop!! :)

M

---

### Post by strabes on 2007-05-27
But you'll be paying more money for equivalent hardware and you'll never be able to use any hardware that apple doesn't say you can... Just get a cheap dell inspiron and upgrade to a nvidia video card and you'll be good to go.

---

### Post by MacPC on 2007-05-28
Mmm, that's a good point.I wonder Parallel can handle both Linux and Windows. And also I hope the Mac version of VMware comes out soon. If I can find a cheap used laptop,(<$250)  I might still go for it.

M.

---

### Post by helliewm on 2007-05-28
You can get ATI cards to work they are just a pain. I bought the other week a Dell Inspiron 9400 because I wanted the 17 inch wide screen. It was the highest spec I could afford and could not afford another £150 to upgrade to the Nvida graphics card. I got the ATI card x1400 working and its fine. Beryl works etc. 

You just need to fiddle around and read the forums to get ATI cards to work. Probably only for the reasonable competent Linux user though.

Helen

---

### Post by MacPC on 2007-05-28
How do I chang the video card on a Laptop? Isn't it built into the mobo? Do you mean I need to get one that has ATI card built in? I think all Mac has ATI, may be I am wrong. My experience with Linux is limited but I did configure a Ubuntu Desktop PC with nvidia card using dual monitor. It didn't seem too hard and it was kinda fun.:D

M

---

### Post by antonc on 2007-05-28
Hi

Don't worry about it. I've got a 3680 that I've been running Ubuntu on for a while (Edgy, then Feisty), and it works great. The Wireless card is a Broadcom, but it works fine with both ndiswrapper or the bcm43xx drivers (only works up to 24Mb though).

The Graphics card is an Intel 945, works fine at native rez (1280x800) using 915resolution.
Beryl/compiz works out the box too, and is -quite- fast.
Suspend-to-RAM woks perfectly too, the inbuilt card reader works.
The only issue with Feisty out the box is that the headphone-out connector doesn't work. This can be solved by building a newer version of ALSA. (I haven't bothered. I'm lazy :-)

---

### Post by loathsome on 2007-05-28
> **MacPC said:**
> Hi,

Thanks all for your reply.

I think I will save up the money for now and get a nice MacBook, that way I can a have OSX, Ubuntu and the crappy Windos BS. Three OSs on one laptop!! :)

M

My Sony Vaio laptop runs OS X just fine :lolflag:

---

### Post by MacPC on 2007-05-29
Ha ha! Are you serious?

M

---

