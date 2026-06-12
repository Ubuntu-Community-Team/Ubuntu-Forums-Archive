---
title: "Buying a new computer specifically for Ubuntu, need advice."
date: 2008-02-18
forum: General Help
---

### Post by Sick_of_present_tech on 2008-02-18
I intend to invest in a brand new, albeit, cheap computer, either at whalemart or best buy, specifically for installing Ubuntu on it. What should I look for? What is the best, cheap/easiest computer/s to install ubuntu on? I'm talking what would present the least problems for a cheap computer. Thanks!

---

### Post by aysiu on 2008-02-18
What country do you live in?

It's possible you could buy a computer with Ubuntu preinstalled.

---

### Post by Sick_of_present_tech on 2008-02-18
> **aysiu said:**
> What country do you live in?

It's possible you could buy a computer with Ubuntu preinstalled.

The united states. Thanks. What cheap computer/s come with Ubuntu preinstalled?

---

### Post by aysiu on 2008-02-18
> **Sick_of_present_tech said:**
> The united states. Thanks. What cheap computer/s come with Ubuntu preinstalled?
You have at least three options:
[Dell with Ubuntu preinstalled](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)
[ZaReason](http://www.zareason.com/shop/home.php)
[System76](http://www.system76.com/)

---

### Post by Sick_of_present_tech on 2008-02-19
> **aysiu said:**
> You have at least three options:
[Dell with Ubuntu preinstalled](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)
[ZaReason](http://www.zareason.com/shop/home.php)
[System76](http://www.system76.com/)

You mean to tell me when I talk to a sales person at dell they will give me the option of having Ubuntu installed instead of windows? I wonder why i've never heard of this before? it must be a relatively new thing. Nonetheless it's awesome!

---

### Post by merlinDwizzard on 2008-02-19
Personally, I cannot believe how well my acer does with ubuntu. It came with 512mb of ram,, but I stuck a 1gig stick in it and now it friggin cruises. I gave around 650 bucks for it brand new. wireless worked out of the box,advanced desktop effects, no problem. I have to run windows for school but thats all done in virtualbox. One server 2003 virtual machine and two client xp virtual machines, all networked together. Something to look into.

---

### Post by Sick_of_present_tech on 2008-02-19
> **merlinDwizzard said:**
> Personally, I cannot believe how well my acer does with ubuntu. It came with 512mb of ram,, but I stuck a 1gig stick in it and now it friggin cruises. I gave around 650 bucks for it brand new. wireless worked out of the box,advanced desktop effects, no problem. I have to run windows for school but thats all done in virtualbox. One server 2003 virtual machine and two client xp virtual machines, all networked together. Something to look into.
 I appreciate the advice. Where did you buy your acer system? Whalemart? best buy? Circuit city? Did you add the extra memory because it was running ubuntu applications too slow with only 512?

---

### Post by NightwishFan on 2008-02-19
Thank you very much for the links.

---

### Post by merlinDwizzard on 2008-02-19
I got it at Compusa, i added the extra memory for the purpose of the virtual networking and mostly because I'm a gearhead(lol). Nothing is ever fast enough for me in stock form. Just a personal hangup i guess. But, the additional ram only cost me around 70 bucks. That was all before compiz was discovered by me. But, I have a friend with a little lower grade acer with 512 and he runs compiz with no problem. But I still mess with him when he's showing it off. I say things like "I think I smell processor" and stuff like that just to mess with him. (lol)

---

### Post by Sick_of_present_tech on 2008-02-19
I saw a compaq presario at staples today for 399$. It had windows vista with all that 'media center' software installed. Is this kind of software difficult to purge? In fact, is windows vista difficult to purge from a compaq presario and to then replace with ubuntu, or could I actually install Ubuntu alongside vista?

---

### Post by Aetherfox on 2008-02-19
You can do both. Although the method for dual-booting with vista is a little different than xp. That dell computer mentioned above is a good choice for running ubuntu at a cheap price.

---

### Post by JonUK76 on 2008-02-19
Wiping Vista is easy. You would just tell the Ubuntu installer to use all available space for the installation. It will wipe the drive and do a clean install of Ubuntu.

Dual boot is an option. Its usually just a case of resizing an existing partition to make room for the linux install (easy using Gparted on the LiveCD for example). The Ubuntu installer should detect the presence of Windows and set up a boot menu for you. I say should, I had a lot of difficulty with my latest install, as Windows would not start after I installed Ubuntu. I had to mess about with GRUB to get it working. But on other PC's its been trouble free.

---

### Post by Sick_of_present_tech on 2008-02-19
> **JonUK76 said:**
> Wiping Vista is easy. You would just tell the Ubuntu installer to use all available space for the installation. It will wipe the drive and do a clean install of Ubuntu.

Dual boot is an option. Its usually just a case of resizing an existing partition to make room for the linux install (easy using Gparted on the LiveCD for example). The Ubuntu installer should detect the presence of Windows and set up a boot menu for you. I say should, I had a lot of difficulty with my latest install, as Windows would not start after I installed Ubuntu. I had to mess about with GRUB to get it working. But on other PC's its been trouble free.

would I need to partition even on a brand new computer with 160 gigabytes of free space? I use external hard drives too, so space is not an issue on my computers.

---

### Post by JonUK76 on 2008-02-20
> **Sick_of_present_tech said:**
> would I need to partition even on a brand new computer with 160 gigabytes of free space? I use external hard drives too, so space is not an issue on my computers.

If you wanted to dual boot both OS's from the internal drive you would. Although theres a lot of free space its most likely the disk is going to be set up as a big Windows (NTFS) partition ( perhaps with a second recovery partition?). Linux uses a different file system (Ext3)  so you would have to shrink the main partition to make room for it.

---

### Post by merlinDwizzard on 2008-02-20
No, it's not hard if you format the entire Hdd and install ubuntu. It completely (and I do mean completely) wipes it out. The only thing you may consider is the fact that the os is pre-installed, take the time to make a factory back up disk. This is pretty a pretty common feature on computers with the operating system pre-installed. that way' if you change your mind' you can always go back(After that, once you wipe the disk, you will have a clean slate. No matter what os was on it).

---

### Post by Sick_of_present_tech on 2008-03-02
I'm Wondering if someone can leave instructions on how to install it with leaving vista and one for wiping out vista completely. I ask because I am not sure which method I will be using yet and I might as well learn both. Thanks.

---

### Post by steveneddy on 2008-03-02
I have a System76 laptop that works great.

Although I bought the top of the line with all of the bells and whistles, the entry level models are economical and well dressed with options out of the box.

And, preinstalled.

[www.system76.com](www.system76.com)

---

### Post by Sick_of_present_tech on 2008-03-02
> **steveneddy said:**
> I have a System76 laptop that works great.

Although I bought the top of the line with all of the bells and whistles, the entry level models are economical and well dressed with options out of the box.

And, preinstalled.

[www.system76.com](www.system76.com)



It's nice but I want a desktop computer specifically for the fact that I want to connect a 24 inch monitor to it and feel better doing that with something that is not latched to another monitor already. How are their desktop units? Anyone know?

---

