---
title: "Has swap usage become feasible on SSDs for low RAM laptops?"
date: 2013-06-09
forum: General Help
---

### Post by chronos00 on 2013-06-09
Hi everyone.

I am considering to purchase an [ultrabook]("https://en.wikipedia.org/wiki/Ultrabook"), which has SSD for storage, but only 4GB of RAM. (Just in case anyone wants to get into detail, [this is the ultrabook]("http://us.acer.com/ac/en/US/content/model/NX.M3EAA.009") I'm intereseted in)

I have always been a heavy RAM user. I usually have many browser windows opened (and many tabs), use Virtual machines frequently, etc. I know that 4GB of RAM will NOT be enough for me. This has been the case so far, because the swap is absolutely painful to use. I mean, we can talk about hundreds of times slower...

But just came to my attention... What if the swap becomes at least remotely "comparable" to system memory? (RAM).
What if the SSD allowed me to actually use the swap as intended and, despite feeling a noticeable sluggishness, being able to open more programs than would fit into RAM without having to wait minutes for the computer to respond?

Of course, this is absolutely dependent on how well the swap would perform on a SSD, which brings us to my question to you:

Do you have any personal experience with frequent swap usage on a SSD?
Is it bearable?
Is it usable?


Thanks in advance!

---

### Post by HermanAB on 2013-06-09
The new Macbooks have SSDs.  

Nuff sed.

---

### Post by chronos00 on 2013-06-09
Thanks for your answer HermanAB, but I still don't understand why the Macbooks come into reference here.
Do you mean that Macbooks are also prepared for heavy RAM usage, despite having only 4GB of RAM?

I can see from [Macbook Air's specification]("https://en.wikipedia.org/wiki/MacBook_Air#Specifications") that it has 4GB of RAM, but there is also a model available with 8GB. This may mean that the 8GB model is intended for heavy users, while the 4GB model is just meant for light usage (so I don't know if swapping to a SSD is considered for these models).

Do you think that Macbook Airs are prepared to swap heavily on the SSD and not feel a performance hit?

Thank you.

---

### Post by chronos00 on 2013-06-09
In case anyone is looking for information about this, I found a blog article talking about this situation: [https://blogs.oracle.com/partnertech/entry/swap_space_on_ssd](https://blogs.oracle.com/partnertech/entry/swap_space_on_ssd)

---

### Post by ahallubuntu on 2013-06-09
~

---

### Post by chronos00 on 2013-06-09
I am not thinking in SSDs as a replacement to RAM.

My personal experience is that when I use all of my RAM, and the system starts paging, the systems becomes utterly unusable. So I need to do whatever is needed to keep the RAM usage below the maximum (and adjusting swappiness to 10).

My question is:
Is the system usable while paging to a SSD?

I know this is very subjective, but I am talking about basic responsiveness.

---

### Post by pqwoerituytrueiwoq on 2013-06-09
it should be usable, but using a ssd for swap puts a lot of wear on it, however 4gb of ram should be plenty, 2gb would should even be sufficient, 1gb is sufficient for a basic user

---

### Post by kurt18947 on 2013-06-10
Sweet looking machine!  I don't see the maximum amt. of DRAM it'll hold but I suspect it's more than 4 GB.  Why not increase installed DRAM to 8 GB. or more?  Swap seems a bit archaic in this time of dirt cheap RAM (at least by historical standards).  Well, unless you want to enable hibernation.

---

### Post by chronos00 on 2013-06-11
Ultrabooks achieve their lightness and thinness with some sacrifices. One of those traits is that it is absolutely NOT customizable. It has fixed amount of onboard RAM, fixed perihperials, no DVD reader, and in this case, it even does not have an ethernet port (it comes with a USB adapter for ethernet connection, which I think is smart, given the little usage I actually give it).

Other manufacturers build several models; some with 4GB of RAM, some with 8GB. In this case, Acer only built these models with 4GB. I haven't seen any other manufacturer which has produced an ultrabook with so many amazing features squished into such a small form factor. That's why I am bearing the "low" amount of RAM.

BTW, not only this ultrabook has a SSD, but in fact it has 2 of them, packed in a single drive, arranged in RAID0. I have benchmarked it with ubuntu (disk utility), and got an incredible throughput of 1100 MB/s for reading, and 950 MB/s for writing. I still cant believe I am talking about an ultrabook...

I sound like an Acer representative hehe. I took my chances and bought the Aspire S7 391 already. Let me try it for a few days so that I see what is not working properly under Ubuntu. So far the brightness controls are not working and the RAID0 arrangment gave many problems for installation.

---

### Post by CaptainMark on 2013-06-11
If you're reluctant to create a swap partition on your SSD and if like me your laptop has an SD card slot which you rarely need to use you can always create a swap partition on your SD card and leave it permanently plugged in. You'd need to switch off the swap if you need to use the sd slot but I don't ever use mine really so it's never given me any trouble.

---

### Post by kurt18947 on 2013-06-11
> **chronos00 said:**
> Ultrabooks achieve their lightness and thinness with some sacrifices. One of those traits is that it is absolutely NOT customizable. It has fixed amount of onboard RAM, fixed perihperials, no DVD reader, and in this case, it even does not have an ethernet port (it comes with a USB adapter for ethernet connection, which I think is smart, given the little usage I actually give it).

Other manufacturers build several models; some with 4GB of RAM, some with 8GB. In this case, Acer only built these models with 4GB. I haven't seen any other manufacturer which has produced an ultrabook with so many amazing features squished into such a small form factor. That's why I am bearing the "low" amount of RAM.

BTW, not only this ultrabook has a SSD, but in fact it has 2 of them, packed in a single drive, arranged in RAID0. I have benchmarked it with ubuntu (disk utility), and got an incredible throughput of 1100 MB/s for reading, and 950 MB/s for writing. I still cant believe I am talking about an ultrabook...

I sound like an Acer representative hehe. I took my chances and bought the Aspire S7 391 already. Let me try it for a few days so that I see what is not working properly under Ubuntu. So far the brightness controls are not working and the RAID0 arrangment gave many problems for installation.

Thank you for your info,  I hadn't really paid attention to ultrabooks.  A few years ago I experimented with virtual machines.  I installed Ubuntu 11.10 (I think) as a host and Win 7 as a guest O.S.  Running Win 7 & an office suite used <900 MB. RAM.  You may find 4 GB. fine with a little care.  I installed HTOP to be able to see which programs were using what resources without the program using much in the way of resources itself.

---

### Post by chronos00 on 2013-06-11
> **CaptainMark said:**
> If you're reluctant to create a swap partition on your SSD and if like me your laptop has an SD card slot which you rarely need to use you can always create a swap partition on your SD card and leave it permanently plugged in. You'd need to switch off the swap if you need to use the sd slot but I don't ever use mine really so it's never given me any trouble.

This would be quite useful for hibernation, but for regular system paging, I think it will be MUCH slower than a SSD. Even with a Class10 SDs, the throuput is 10MB/s for writing, compared to 1000MB/s achieved by SSDs in RAID0.

This is interesting for hibernation, though, in situations when I have already used all my RAM, part of the swap, and I still want to hibernate.

---

### Post by Rebelli0us on 2013-06-11
I only use swap on my laptop because it's the only way to enable hibernation. Otherwise swap is not necessary. 

4 GB memory is plentiful, I even run Windows VMs on 4GB. 

If you add more memory on portable devices, you shorten battery life and increase hibernation/wakeup time.

SSD helps speed up boot up & hibernation, otherwise no great advantage  on notebooks.

If you have SSD, enable Trim in fstab -- **noatime,discard**,errors=remount-ro	0	1

also change scheduler, although some distros do it by themselves -- 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **elevator=noop**".
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **elevator=deadline**"

---

### Post by zemega on 2013-06-11
Putting swap on SD card does help, but the truth is, it depends on the car reader speed itself. Sandisk Class 10 achieve 30MB/s speed and higher, but if you put it in slow car reader (I know its internal car reader), it will still be slow. Worse case, the card reader is actually just an external card reader wired into a USB 2.0 port on the motherboard. You can still try to solder a really fast car reader to replace it, but its not worth it probably. So a cheap ultrabook probably skimp on this and gives you a slow card reader, so its not really helping you. Your best bet is just to call up Acer and ask whether that RAM can be upgraded or not. Or if you can order one with 8GB RAM instead.

---

### Post by chronos00 on 2013-06-13
The swap usage I am interested is for paging RAM. I will use ot for hibernation too, but I don't worry too much about hibernation's speed.

An SD card is hundreds of times slower than a SSD, which in turn is hundreds (if not thousands) of times slower than RAM. So I don't think an SD is usable for swapping (paging).

---

