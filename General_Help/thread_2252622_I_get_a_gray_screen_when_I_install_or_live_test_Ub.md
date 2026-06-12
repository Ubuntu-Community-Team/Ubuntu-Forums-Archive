---
title: "I get a gray screen when I install or live test Ubuntu 13.04..."
date: 2014-11-13
forum: General Help
---

### Post by Kevin_Dico on 2014-11-13
I get a gray screen when I try to install Ubuntu 13.04 on my pc. I tried using different flash drives, also tried the ftp and torrent versions of the download, but still I get the gray screen. The gray screen is just an empty gray screen with a white cursor that I can't interact with. What do I need to provide in this post to help me solve my problem? Please help. I want to try Ubuntu. Thanks.

---

### Post by coldcritter64 on 2014-11-13
> ... I want to try Ubuntu. Thanks.                 
Have you considered downloading either 12.04 (support till 2017) or 14.04 (support till 2019) ? 

13.04 is already "end of life", with no further support (security updates etc). Getting help here for an unsupported version can be hard also, threads often get locked on such questions.

---

### Post by Al1000 on 2014-11-13
Hi,

How old is this pc, and can you provide some specifications?

---

### Post by Kevin_Dico on 2014-11-13
> **Al1000 said:**
> Hi,

How old is this pc, and can you provide some specifications?


Hello!

These are the specs for my PC:

Mobo: Gigabyte Z87N-WIFI Bios Date: 01/26/2014 14:01: 53 Ver: 04.06.05
Proc: Intel(R) Core(TM) i5-4670 CPU @ 3.40GHz (4 CPUs), ~ 3.4
Mem: 8192MB RAM
DX: DX11
OS: Windows 8.1 64-bit (6.3, Build 9600)
GPU: EVGA Nvidia GTX 750 4018MB

Thanks! I hope you can help me...

---

### Post by Kevin_Dico on 2014-11-13
> **coldcritter64 said:**
> Have you considered downloading either 12.04 (support till 2017) or 14.04 (support till 2019) ? 

13.04 is already "end of life", with no further support (security updates etc). Getting help here for an unsupported version can be hard also, threads often get locked on such questions.

I did not know 13.04 is already dying, sorry. If this gets locked, I'll just start another thread. The reason why I wanted to use 13.04 is because I want to install Adobe ColdFusion 11 and start to learn it in Linux. 12.04 only supports ColdFusion10. Thanks! But 12.04 will work too! :)

---

### Post by coffeecat on 2014-11-13
We won't lock the thread until you have got the advice you need. Which, obviously, includes - don't use 13.04. :) 

If 12.04 works for you to be able to run that particular software, albeit an earlier version, then you are better off with that. It is supported until 2017.

I have no experience of Adobe Cold Fusion. Can you not run it on 14.04? What happens when you try to run 14.04 on that machine?

---

### Post by Kevin_Dico on 2014-11-13
> **coffeecat said:**
> We won't lock the thread until you have got the advice you need. Which, obviously, includes - don't use 13.04. :) 

If 12.04 works for you to be able to run that particular software, albeit an earlier version, then you are better off with that. It is supported until 2017.

I have no experience of Adobe Cold Fusion. Can you not run it on 14.04? What happens when you try to run 14.04 on that machine?

Haha, thanks. I will download the 12.04 now and hopefully I'll get past the gray screen this time. For ColdFusion 11, there is a list here: [http://www.adobe.com/sea/products/coldfusion-standard/tech-specs.html](http://www.adobe.com/sea/products/coldfusion-standard/tech-specs.html). I haven't tried CF on Linux, like ever, so I can't really tell. :/

---

### Post by yancek on 2014-11-13
If you have windows 8 also installed, if it was pre-installed it usually uses EFI to boot so you would need to install Ubuntu in EFI mode also.  I don't use EFI but from what I have read here this option should be available when booting the Ubuntu installation medium.

---

### Post by Kevin_Dico on 2014-11-13
> **yancek said:**
> If you have windows 8 also installed, if it was pre-installed it usually uses EFI to boot so you would need to install Ubuntu in EFI mode also.  I don't use EFI but from what I have read here this option should be available when booting the Ubuntu installation medium.

I will try to research on EFI boot. I built my PC so I bought a copy of Windows myself. :) Thanks!

---

### Post by Kevin_Dico on 2014-11-13
It seems that I can finally get past the gray screen with the 12.04. I still get the gray screen, but the loading screen shows up after a few seconds. Now my problem is that it is not detecting my Windows 8 on my SSD. It seems that it cannot detect an OS in an SSD? I'll try to create a partition on my HDD and see what happens. :(

---

### Post by Impavidus on 2014-11-13
It cannot detect an OS in hibernation. Using fastboot Windows 8 is always in some kind of hibernation. When you switch off fastboot in Windows 8 and completely shut it down, Ubuntu should detect it.

---

