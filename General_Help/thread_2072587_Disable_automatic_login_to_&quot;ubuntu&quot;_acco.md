---
title: "Disable automatic login to &quot;ubuntu&quot; account"
date: 2012-10-18
forum: General Help
---

### Post by han5vk on 2012-10-18
Hello, I have a liveUSB with ubuntu 11.10 on it. I have there my own account "Han" with a password, and there's also a basic account called "ubuntu". I have set a password there too, by some passwd command in terminal. The problem is, when I boot up the computer, It automatically logs in ubuntu account, without asking for password. When I Log Off, there are two options, Han & Other. When I choose Other, there username "ubuntu" and password, it logs in. The question is, how do I disable that automatic login?

---

### Post by apollothethird on 2012-10-18
> **han5vk said:**
> Hello, I have a liveUSB with ubuntu 11.10 on it. I have there my own account "Han" with a password, and there's also a basic account called "ubuntu". I have set a password there too, by some passwd command in terminal. The problem is, when I boot up the computer, It automatically logs in ubuntu account, without asking for password. When I Log Off, there are two options, Han & Other. When I choose Other, there username "ubuntu" and password, it logs in. The question is, how do I disable that automatic login?

Hi, Han.  This doesn't precisely answers your question but might be a very viable workaround to consider.  I was using the convenience of the LiveUSB for a while.  I found it very lacking in certain custom configuration options.  I was able to resolve all my configuration problems by installing Ubuntu on the USB drive as a normal install rather than a LiveUSB configuration.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by han5vk on 2012-10-18
Yes, but, how big Ubuntu is? I think more than 700mB for the iso..

---

### Post by apollothethird on 2012-10-18
> **han5vk said:**
> Yes, but, how big Ubuntu is? I thing more than 700mB for the iso..

Ok.  It'd take significantly more than 700MB.  I originally used a 4gig pen drive.  I later did the same with a 8gib pen drive.  I currently have it installed on a 16gig pen drive, using the other 8 gigs as a Windows data usb drive to transfer files between computers.

I believe the cost of a 8 gig drive is about 6 or 8 dollars.  I don't know if usb drives can be found anymore that is less than a couple of gigs.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by han5vk on 2012-10-18
Well, I have a 8GB drive.. 700mB for the .iso, 2+ GB for presistance and everything else for the data (about 4.5GB). But, I think that when I install it normally, it will need more space, and there will be very small for the data. So, how much do I need just for the system and some settings? /how big partition?/ 

And, also, I have one more question. Now, I have there a FAT32 partition (4.5GB) called HanUSB, and I want it to work like normal data storage which works in windows as well.. But, when I put the drive into windows system, it says it needs to be formatted. How do I fix that? 

Thanks.

---

### Post by sienile on 2012-10-18
As far as your FAT32 problem, I would copy the files off of it and format it in Windows, then copy the files back on.

As for system size... I put Ubuntu on an old 8GB internal HDD. I used 1.4GB for SWAP and the remaining 6.6GB for the system. After installing several apps and the GNOME Classic DE, I deleted all the package caches and had about 1.3GB of free space. So that's about 5.3GB system size.

---

