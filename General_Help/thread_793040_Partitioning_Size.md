---
title: "Partitioning Size"
date: 2008-05-13
forum: General Help
---

### Post by cancer10 on 2008-05-13
Hi

I have 15 GB HDD space and I want to install ubuntu. Please tell me how much space should I assign to what partition?


Thanx

---

### Post by kirios on 2008-05-13
5 GB should be fine for /. You need a swap partition (say 1 GB - depends on the amount of physical RAM) and the rest for /home. 

> **cancer10 said:**
> Hi

I have 15 GB HDD space and I want to install ubuntu. Please tell me how much space should I assign to what partition?


Thanx

---

### Post by cancer10 on 2008-05-13
what about 

/var
/tmp
/boot
/usr


???

---

### Post by kk0sse54 on 2008-05-13
> what about

/var
/tmp
/boot
/usr


??? 

That's part of the Ubuntu installation so if you install it on the 5GB that's where it will go along with /home unless you designate that somewhere else.

---

### Post by cancer10 on 2008-05-13
You mean the following 

/var
/tmp
/boot
/usr


will go automatically under / ??

if yes then should not I increase / from 5 GB to some more?

---

### Post by kirios on 2008-05-14
Yes. You can even place /home on the / partition in which case you'd only need two partitions (/, 14GB and swap, 1 GB). The advantage of a separate /home partition is that it makes life easier when you upgrade to the next Ubuntu release.

> **cancer10 said:**
> You mean the following 

/var
/tmp
/boot
/usr


will go automatically under / ??

if yes then should not I increase / from 5 GB to some more?

---

### Post by cancer10 on 2008-05-14
Wow. You guys have a lot of knowledge. Are you from windows background or linux?

---

### Post by kirios on 2008-05-14
Windows actually. Still a Linux rookie. :-) 

> **cancer10 said:**
> Wow. You guys have a lot of knowledge. Are you from windows background or linux?

---

### Post by cancer10 on 2008-05-14
> **kirios said:**
> Windows actually. Still a Linux rookie. :-)


oh same pinch :)


So from where do you download applications for your ubuntu?

I have heard that all applications for linux are free, so no need to involve in any piracy. IS it true?


Thanx

---

### Post by forestpixie on 2008-05-14
I personally wouldn't bother to do anything other than install to it if you only have 15Gb available as kirios has said. If it's unallocated space when you install point the partitioner at the empty space it will do what it needs to.

---

### Post by kirios on 2008-05-14
[https://help.ubuntu.com](https://help.ubuntu.com) - read the section on adding and removing software.   > **cancer10 said:**
> oh same pinch :)


So from where do you download applications for your ubuntu?

I have heard that all applications for linux are free, so no need to involve in any piracy. IS it true?


Thanx

---

### Post by kk0sse54 on 2008-05-15
Software is free for Linux and no it is not piracy. Pretty much all the software you will need will be available through Add/Remove Application removing the need to download programs and installing them yourself ( which you can but it's a lot harder than windows on this aspect considering that .exe doesn't work on linux).

P.S. yea I'm from Windows background still trying to familiarize myself with Linux. :)

---

### Post by cancer10 on 2008-05-15
ok since u have a windows background. I really need to know how do u set IPs and DNS server for your ISP in ubuntu which you used to set in windows from Control Panel > network connections > Right Click on your connection > properties > Internet Protocol (TCP/IP)


Thanx

---

### Post by kk0sse54 on 2008-05-15
> ok since u have a windows background. I really need to know how do u set IPs and DNS server for your ISP in ubuntu which you used to set in windows from Control Panel > network connections > Right Click on your connection > properties > Internet Protocol (TCP/IP)

sorry mate but I can't help you there since every install of Ubuntu I have done it has set up my internet up for me during the installation giving me a static IP. Although you should be able to do that kind of stuff under System>Administration>Network or maybe network tools.

---

### Post by cancer10 on 2008-05-15
> **C!oud said:**
> sorry mate but I can't help you there since every install of Ubuntu I have done it has set up my internet up for me during the installation giving me a static IP. Although you should be able to do that kind of stuff under System>Administration>Network or maybe network tools.


Strange but how does ubuntu knows your ISP's DNS servers? LOL

---

### Post by latna on 2008-05-15
> **cancer10 said:**
> Strange but how does ubuntu knows your ISP's DNS servers? LOL

It's part of the information which your machine obtains as part of a DHCP request. Are you saying that on Windows you have to edit this information manually? I've used dialup, dsl and cable internet without ever having to configure this information manually.

---

### Post by cancer10 on 2008-05-15
> **latna said:**
> It's part of the information which your machine obtains as part of a DHCP request. Are you saying that on Windows you have to edit this information manually? I've used dialup, dsl and cable internet without ever having to configure this information manually.

Thats Strange man. I have to add  the DNS settings everytime I format and reinstall XP on my machine.


Lucky you :)

---

### Post by fyo on 2008-05-15
> **cancer10 said:**
> Thats Strange man. I have to add  the DNS settings everytime I format and reinstall XP on my machine.


Lucky you :)

If it doesn't work automatically for you in Ubuntu, you can do the following:

1) Try refreshing the dhcp request manually. Open a terminal and type "sudo dhclient".

2) Enter the information manually, as you did in Windows, by opening System -> Administration -> Network.

As for how much you should use for Ubuntu, I would recommend just using a single partition for everything but swap. A good size for swap is 1-2x your memory (if you use less than 1x your memory, stuff like hibernate won't work).

---

### Post by latna on 2008-05-15
> **cancer10 said:**
> Thats Strange man. I have to add  the DNS settings everytime I format and reinstall XP on my machine.

How do you connect to your ISP anyway? You haven't mentioned that.

---

### Post by cancer10 on 2008-05-15
> **latna said:**
> How do you connect to your ISP anyway? You haven't mentioned that.

I have an ADSL connection. I use MTNL Broadband. If you are in India then you should know what MTNL BB is :)

---

