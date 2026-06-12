---
title: "Hardware Change"
date: 2007-01-30
forum: General Help
---

### Post by twshadow101 on 2007-01-30
I am planning on changing my motherboard, memory, and processor due to the fact they are wearing down and beginning to cause problems with my system.

Currently right now I use,
AMD Duron / 1.2Ghz
Im not sure of the motherboard.

I want to upgrade to,
Foxconn 6100K8MA-RS Socket 939 NVIDIA GeForce 6100 Micro ATX AMD Motherboard
 AMD Athlon 64 3700+ San Diego 2.2GHz Socket 939 Processor Model ADA3700CFBOX

My question is, can I change the motherboard and processor and use the same hard drive which contains Ubuntu 6.10.

Basically, can I change the motherboard and processor. Then plug in my hard drive and boot it right up like I would now? Is it that easy? Or, do I have to do something else. Because im going to use the same hard drive which contains all of my data and Ubuntu.

---

### Post by kidders on 2007-01-30
Hi there,

Although you probably *could* (with some relatively minor tweaks), I wouldn't recommend making such a radical archtectural change without installing the appropriate Ubuntu build for the new platform. Although there are, in reality, certain reasons for doing so, it seems odd to buy a 64-bit processor, only to make it emulate 32-bit operation.

If holding on to your current base system is very important to you, and you are prepared to tinker with whatever (if anything) doesn't work quite right, you might as well try. Having said that, I would strongly recommend downloading 64-bit Ubuntu instead, and copying over your personal files.

To answer your question more generally, Ubuntu can (in theory) handle fairly arbitrary hardware changes, without much difficulty. Unless you've spent some time customising your hardware configuration, any new bits & pieces you might plug in should be handled pretty gracefully. The only major caveats are (a) your Ubuntu build must have the appropriate drivers, and (b) nothing on your system must explicitly conflict with your changes. Two examples:

1. You switch CPU architecture. As may be the case for you, the Ubuntu for the original architecture may lack some of the drivers necessary to handle some of the new motherboard's integrated peripherals.

2. You tinker around with your hard disks, and all of a sudden, an /etc/fstab entry pointed at /dev/sda1, now points somewhere unexpected. Similar things can happen with network cards.

---

### Post by djheadley on 2007-01-30
Actually, I did just this thing (different mobo's) when I went from a 433mhz machine to a 1ghz machine.  The only thing I had to do was to reconfig xorg.  Yes, you may run into troubles so at least backup your important data 1st!!  I dual boot with Windows and had to reboot **6** times before Windows was done, only 1 time and Ubuntu was purring along!

Good luck!

---

### Post by kidders on 2007-01-30
> **djheadley said:**
> Actually, I did just this thing (different mobo's) when I went from a 433mhz machine to a 1ghz machine.  The only thing I had to do was to reconfig xorg.  Yes, you may run into troubles so at least backup your important data 1st!!  I dual boot with Windows and had to reboot **6** times before Windows was done, only 1 time and Ubuntu was purring along!

Good luck!

That's encouraging. :-) Out of interest, did you switch CPU architecture too?

---

### Post by twshadow101 on 2007-01-31
Hmm... Alright I understand your point. I didn't realize the 32bit to 64bit either..lol. 

Now what if I was to buy another brand new hard drive and install the 64bit Ubuntu on it. Can I plug this current hard drive into another IDE/SATA port and copy everything over to the new hard drive such as all of my pictures, music, and personal files without any problems? 

Once I copy everything from the current hard drive to the new one, then I could reformat the second hard disk to work with the new 64bit install. Can that be done?

Also, whats the difference between 32 and 64??? I don't understand it much. Actually I was planning on switching to Intel from AMD but even I knew that was to much of a change..lol. :D

---

### Post by kidders on 2007-01-31
Hey again,

> **twshadow101 said:**
> Now what if I was to buy another brand new hard drive and install the 64bit Ubuntu on it.No problem. :-) If you wanted to, you could just mount the entire original disk into your new home directory and delete any files that you don't want to keep (ie almost everything!). There are certain advantages to having your personal files on a separate partition/device. I suggest ensuring that your /etc/fstab is using UUID-based device names, to avoid any possible confusion that might result from your /dev paths moving around though.

> **twshadow101 said:**
> I could reformat the second hard disk to work with the new 64bit install.You can reformat the disk if you'd like to, but it's not necessary.

> **twshadow101 said:**
> Also, whats the difference between 32 and 64??? I don't understand it much.Basically, the difference is in the size of the numbers a processor can manipulate in a single operation. Since 64-bit processors can handle 64-bit numbers (well... obviously!), they tend to be able to support extremely large amounts of RAM, ginormous (ie several terabytes) filesystems, and can perform certain mathematical operations more efficiently. While most are capable of emulating 32-bit operation, the reverse is *never* true.

In my opinion (and it's only one person's opinion), you should _not_ buy a 64-bit processor unless...

[LIST]
[*]You are familiar with the strengths of the 64-bit platform, and have something specific to gain by using it.
[*]You intend to run a 64-bit operating system.
[*]You are prepared to deal with the many downsides of taking the 64-bit plunge.
[/LIST]

Almost all the disadvantages of using a 64-bit CPU architecture are similar to, for instance, Linux's poor support for NTFS. Since many software authors don't release their source code, you often have to rely on them to produce 64-bit versions of their applications/drivers themselves. Many don't bother.

In terms of a processor architecture switch, AMD -> Intel is far less radical than AMD -> AMD64. If you're thinking about making a change, the best advice is to read a little about how well the various strengths & weaknesses of each CPU type compare against what you're planning on doing with it.

Hope that helps!

---

### Post by eeried on 2007-02-14
Hello,

I thought having an Athlon 64 processor gave your computer quite more power compared to Sempron even if you don't intall the 64bits version of Ubuntu.

Now if you don't get an Athlon 64, the choice is rather narrow: in France yu can buy only Sempron 2600+, and I doubt many people would be satisfied with its performance any longer.

Shall we move to dual core though it is a useless expense for most of us?

BTW Does the Foxconn works fine with Ubuntu?

---

### Post by mips on 2007-02-14
eeried,

I don't quit understand what you are asking.

Eache processor will provide a performance gain over the lesser spec one Sempron->Athlon64->Athlon64 X2

But it depends very much on your applications and computer usage as to whether you will notice a significant performance gain or not. Just reading mail & browsing the web you will not notice much of a difference or any at all.

Foxconn ? What foxconn device are you referring to ? Provide product type & Model number please.

---

### Post by eeried on 2007-02-14
This thread which started with talking about this mobo: Foxconn 6100K8MA-RS -- so I'm referring to that mobo.
It looks good and I thought perhaps  twshadow101, now, or someone else might be using it with Ubuntu.

---

### Post by mips on 2007-02-14
> **eeried said:**
> This thread which started with talking about this mobo: Foxconn 6100K8MA-RS -- so I'm referring to that mobo.
It looks good and I thought perhaps  twshadow101, now, or someone else might be using it with Ubuntu.

Seem Ok. The major chipsets are nVidia and the LAN/Audio are Realtek.
[http://www.foxconnchannel.com/EN-GB/Product/motherboard_detail.aspx?ID=en-tt0000037](http://www.foxconnchannel.com/EN-GB/Product/motherboard_detail.aspx?ID=en-tt0000037)

I don't know Foxconn products and what their reputation is like.

---

