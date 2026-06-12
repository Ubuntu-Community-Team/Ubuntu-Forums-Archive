---
title: "[SOLVED] Please help me decide [32-bits vs 64-bits]"
date: 2008-06-05
forum: General Help
---

### Post by robz0rz on 2008-06-05
Dear community

I am playnning to buy myself a laptop in the coming weeks for Uni next year. I'll be getting a nice Lenovo/IBM Thinkpad.

I would like your help in my decision for Ubuntu Hardy 32-bits or Ubuntu Hardy 64-bits for this system. The last time I ran 64-bits Linux on my Desktop PC, the only things I really missed were Wine, Opera and Flash.

Today, I don't feel the need to have Wine anymore (I only really need MS Office 2007, which doesn't run in Wine). Also, I don't use Opera anymore, so it is not a big deal.

I do however find Flash very important.


I'm wondering, how much faster will 64-bits really be on my laptop? Also, how does it perform battery-power-wise? Will my laptop run longer or run out faster? Is there any news on Flash regarding 64-bits Linux?


I hope I can find some answers here. Thank you in forward


-- Rob

---

### Post by Pjotr123 on 2008-06-05
This may help you decide:
[http://ubuntutip.googlepages.com/getubuntu](http://ubuntutip.googlepages.com/getubuntu)

Greeting, Pjotr.

---

### Post by steveneddy on 2008-06-05
If one owns a laptop capable of running a 64 bit OS, then by all means run in 64 but.

Things are just smoother and run better while in 64 bit.

I use 64 bit and have for over a year now and I don't think I would go back to 32 bits on this laptop.

---

### Post by robz0rz on 2008-06-05
Hmmm, I got two totally replies here. The first telling me there is only a very slight performance boost in 64-bits, and I should only get it if my system has over 3GB of RAM. The second tells me the performance boost is good enough not to switch back. I've always been wondering, how much is the performance boost really now?

---

### Post by Kernel_Krunch on 2008-06-05
> **robz0rz said:**
> Dear community

I am playnning to buy myself a laptop in the coming weeks for Uni next year. I'll be getting a nice Lenovo/IBM Thinkpad.
-- Rob

Ok all you need is AMD64 chip.  Intel is for noobs, seriously.

AMD64 is a 32bit processor with 64bit "extensions"  that means you can run both 32bit code AND 64bit.  Intel is trying to force people to buy all new 64bit software with their stupid 64bit only dumb deal... don't be dumb.

---

### Post by robz0rz on 2008-06-06
All I'm reading is that Intel also works with a 64 bit extension, at least the processor that will be in my laptop (probably a Core 2 Duo: [Linky]("http://en.wikipedia.org/wiki/Core_2_duo")).

So, after reading up some more, I've found one value somewhere. Someone suggested that 64-bits will give about 25% boost in speed ([Linky]("http://http://groups.google.com/group/comp.sys.intel/browse_thread/thread/ae3b566e0d7e633b")).

My question about battery life in 64-bits Ubuntu vs 32 bits Ubuntu still stays open. How does it compare? I remember reading something in the changelog about an improvement in Hardy's kernel for 64-bits processors, that was supposed to make it better. Was it bad before? Is it still not so good? Will there be any difference at all?

Thanks for your time guys, this is a great community

---

### Post by robinc on 2008-06-06
i found a fair amount of things aren't in the 64 bit repos so you have to force them.

---

### Post by iaculallad on 2008-06-06
Try reading the link below for more information regarding 32-bit and 64-bit architectures.

> [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by tomcheng76 on 2008-06-06
I got flash player on firefox 3 (Ubuntu 8.04 AMD64), no problem at all.
btw, you mean flash mx or flash player?
If your cpu is 64 bit, i suggest you to installl 64bit version.
However, there are many 32bit packages inside the 64bit Ubuntu as they provides backward compatibly.

Here is my suggestion:
1. 64bit CPU , >4G ram, HDD space is not a problem, little faster => AMD64
2. 32bit CPU, <4G ram, HDD space is important, a little stabler/easier to solve config problem => i386

---

### Post by robz0rz on 2008-06-08
Alright, I am slightly confused now. Is it even possible to run Ubuntu 32-bit on an Intel Core 2 Duo? I keep reading that AMD64 is able to run fine in 32-bit, but no word about EM64T and 32-bit..

Also, seeing my laptop will have 2GB of RAM, I don't think the advantages of 64-bit Ubuntu overcome the disadvantages (no flash, less stability, less packages (maybe some I need)). I'll be sure to partition my /home on an extra partition, so that I can make the switch to 64-bit when I feel I am ready for it.

---

### Post by bingoUV on 2008-06-08
> **Kernel_Krunch said:**
> Ok all you need is AMD64 chip.  Intel is for noobs, seriously.

AMD64 is a 32bit processor with 64bit "extensions"  that means you can run both 32bit code AND 64bit.  Intel is trying to force people to buy all new 64bit software with their stupid 64bit only dumb deal... don't be dumb.

So wrong that I don't know where to start.

1. Intel Core 2 Duo **is** an AMD64 chip. So is the quad core version.
2. On AMD X2 and Intel Core 2 Duo, you can run both 32 bit and 64 bit Ubuntu without big problems.
3. Intel does not have any 64bit only deal. Hope you are not getting confused by Itanium. 

Hint : Itanium does not come in laptops. It was a server chip. All 4 chips that were sold are now rusting in some basement :). It has died for all practical purposes. For home desktop/laptop purposes, it never lived so we cannot say it died.

---

### Post by bingoUV on 2008-06-08
1. You might face unforeseen difficulties in 64 bit. Admittedly, they are all with non-free stuff. Take Cisco VPN. Working patches to make it work for 2.6.24 kernel 64 bit came a full 2 weeks after those for 32 bit. And they were a bit more involved than the changes required for 32 bit.

2. My testing (Gutsy) did not reveal any perceivable benefit of 64 bit. For some purposes, it is worse than 32 bit in performance. Read this for a systematic comparison (this is of course not my testing) [http://www.phoronix.com/scan.php?page=article&item=616](http://www.phoronix.com/scan.php?page=article&item=616).

EDIT :
3. 64 being numerically twice the value of 32, there is a big placebo effect on human beings. [http://en.wikipedia.org/wiki/Placebo_effect](http://en.wikipedia.org/wiki/Placebo_effect). Those who say it *feels* faster may be deceived.

---

### Post by robz0rz on 2008-06-08
Thank you very much, my decision is made now. Great article! I'll be using 32-bit Ubuntu on my laptop, I need the stability for now. I'll be sure to set up my partitions so I can upgrade to 64-bit some day though. Thanks again

---

### Post by Sef on 2008-06-08
> I'll be using 32-bit Ubuntu on my laptop, I need the stability for now.

On my desktop, Hardy Heron is very stable.  I have had no problems with it being unstable.  Over all there is not much difference between this and the 32-bit.  Graphics are a bit sharper, and photos load faster: 32-bit took about 30-40 minutes for 2000 photos, while 64-bit takes about 4 minutes.

Also please note that that article was from 18 months ago (29 Dec 2006.)  There have been 3 upgrades since it was written.

---

