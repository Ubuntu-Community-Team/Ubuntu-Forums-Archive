---
title: "System Load Monitor !"
date: 2007-04-09
forum: General Help
---

### Post by Kizilbas on 2007-04-09
I activated the System Load Monitor to see the amount of CPU, MEM & SWAP the computer is currently using.

I have no knowledge of linux OS and I want to know what exactly 'SWAP' is and what it is used for.

Also I want to know if I can alter, adjust or change my memory for linux in anyway

I bought my computer back in 2002 so the memory were about 256MB, in reality I have 256MB. I have a SiS graphics. Is there a way to devote MOST of my RAM to my Linux system to ge a better performance? Because I'm running Firefox now, running System Load Monitor, The notes thing, & traffic monitor.

So the usage is like below:

122MB of 186MB used it says, can I go to BIOS settings and change my Graphics sharing size etc to get my RAM focused on the OS; Xubuntu.

+I don't use high graphics requiring programs or games so I want to boost my RAM hardware wise. i.e. from BIOS by making graphic size usage lesser etc..

sorry for my bad English

thanks

---

### Post by DoubleQuadword on 2007-04-09
Think about the SWAP space as the system Virtual Memory. This indeed, isn't the 'exact' definition but surely will give you an idea.

Normally, this space is provided by creating an extended partition which holds the Swap space. The size regarding that partition should be from 1.5 to 2.0 times your actual Physical Memory and it's formatted differently from others.

> **Kizilbas said:**
> Also I want to know if I can alter, adjust or change my memory for linux in anyway

You can extend the Swap Partition using **gparted**, although I've never tried to do so.

> **Kizilbas said:**
> can I go to BIOS settings and change my Graphics sharing size etc to get my RAM focused on the OS; Xubuntu.

If you know how to manage your BIOS configuration do so. That is up to you to decide.

> **Kizilbas said:**
> sorry for my bad English

There's no need to apologize, nobody's perfect. :)

Also, - if you're interested - try reading more about this matter; for example, here: [http://www.faqs.org/docs/linux_admin/x1752.html](http://www.faqs.org/docs/linux_admin/x1752.html)

Regards.

---

### Post by Kizilbas on 2007-04-09
Thank you very much DoubleQuadword :) That's some useful information. I forgot the name of **gparted** and you reminded me now.

In the BIOS I changed graphic sharing settings (my graphic card is old and shares from physical RAM), and now I have a little more RAM first I had 186MB RAM. Now its 242MB RAM.
I'm going to buy RAM get a new soundcard and graphic card(I have no audio-sound at all on the computer so that'll probably fix it -- I'll need to buy a graphic card so it wouldn't share or 'steal' from my physical RAM :p. I'll leave these settings for BIOS now, because everything is working fine.

I have 541mb swap space, do you think it is enough for a Xubuntu DoubleQuadword?

---

### Post by DoubleQuadword on 2007-04-09
You're quite welcome. I'm glad to help whenever I'm able to. :)

Regards.

---

### Post by DoubleQuadword on 2007-04-09
> **Kizilbas said:**
> I have 541mb swap space, do you think it is enough for a Xubuntu DoubleQuadword?

Indeed, that's fairly enough considering you've now 242 MB of 'clean' RAM for your system. (Even 512 MB would be enough).

Now, for **gparted** you can install it by typing:

```
sudo aptitude install gparted
```

This works for Ubuntu, but I think it should work on Xubuntu too. Also, you can set up how you want to partition your disk(s) when installing the OS or, at least, when installing Ubuntu (which comes with **gparted**).

There's also a 'Live CD' version of **gparted** ([http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)). It's useful when you need to perform 'superficial' modifications to your partitions without having to unmount them.

Regards.

---

### Post by Kizilbas on 2007-04-09
Wow DoubleQuadword many great thanks and best wishes for you ! :)

Since I threw windows in the bin I could increase xubuntu's partition to the maximum.

If I increase the size of the already configured partition of my Xubuntu OS, would it format it? Or does gparted have an option to keep the files?

---

### Post by Kizilbas on 2007-04-09
I have an important question for you;

my password for my account is like 4 example: OOOuuu, so its 3 uppercase and 3 lowercase. My sister needs to access the computer too so I made the password simple (she is too lazy) 

How can I create a new account, that let's her use the browser, browse pictures/documents etc but restricts installing programs?

so on my computer I will have 2 accounts

first acc will be mine, e.g. home/kizilbas
second acc will be my sister's 1 e.g. home/Lara

---

### Post by DoubleQuadword on 2007-04-09
> **Kizilbas said:**
> Wow DoubleQuadword many great thanks and best wishes for you ! :) 

You're quite welcome, and as I said previously, I'm glad to help (and be helpful) whenever I'm able to. Best wishes for you too. :)

> **Kizilbas said:**
> If I increase the size of the already configured partition of my Xubuntu OS, would it format it? Or does gparted have an option to keep the files?

To be honest, I've never tried to extend a formatted partition, but I remember reading in another thread, (within this forum), that **gparted** is able to do so. Anyway, I would recommend you to read the **gparted** documentation:

* [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm) .
* [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php) .

Regards.

PS: If you want to search for that thread: I think someone was asking about how to resize a NTFS partition without losing data.

---

### Post by DoubleQuadword on 2007-04-09
To create and set up new and existing user accounts go to: System >> Administration >> Users And Groups.

Regards.

---

### Post by Kizilbas on 2007-04-09
From the profile I select 'unprivileged' but I hope that wouldn't restrict her from viewing images, using firefox browser, using gaim messenger.

---

### Post by DoubleQuadword on 2007-04-09
There's no need to remain sticked to a profile, you can modify user privileges in the "User Privileges" tab in the same window.

Regards.

---

### Post by Kizilbas on 2007-04-09
Thanks for all your precious time and support DoubleQuadword.
You teached me a lot of things today, and yet its the first day I started using linux.

May [img]http://christianbbs.net/jesus-sign.gif[/img] bless you DoubleQuadword [img]http://christianbbs.net/jesus-cross.gif[/img]

---

### Post by DoubleQuadword on 2007-04-09
You're absolutely welcome. I'm very glad that I was helpful to you. May God bless you too. :)

Best regards.

---

