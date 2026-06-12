---
title: "Why external drive not show up in the Disks app?"
date: 2024-01-01
forum: General Help
---

### Post by Advait on 2024-01-01
See linked image below.

I'm using Ubuntu 22.04 on an AMD laptop. One of my USB connected external drives (Laxmi2TB) shows up in Nautilus and Gparted but not in the Disks app. Any idea why that is?

Laxmi2TB is mounted and I'm able to successfully read and write files to it.

My other 2 USB connected external drives (Ishvana2TB and Gopala2TB) show up in the Disks app in addition to Nautilus and Gparted.

All 3 external drives are plugged into the same powered USB hub and all 3 have blue lights at the connection. The hub is connected to my laptop with a USB-A cable.

This is a somewhat trivial issue, but I'm curious...

0-----------

[https://drive.google.com/file/d/1rYiJtjvuAk0CAIifSmpDQLPHLHed2PT8/view?usp=sharing](https://drive.google.com/file/d/1rYiJtjvuAk0CAIifSmpDQLPHLHed2PT8/view?usp=sharing)

(I tried to embed this image with [IMG] tags but that doesn't work.)

0------------

---

### Post by ajgreeny on 2024-01-01
My first guess would be the hub to which these disks are attached.
Have you tried a direct connection of the disk to a USB port instead of through the hub?

---

### Post by Advait on 2024-01-01
> **ajgreeny said:**
> My first guess would be the hub to which these disks are attached.
Have you tried a direct connection of the disk to a USB port instead of through the hub?

Yes, direct connection to laptop works, it shows up normally. My hub is about 3 years old, so maybe it doesn't work as reliably as before. I'll try moving connection and see if that makes a difference.

---

### Post by Advait on 2024-01-01
Strange... I got an email showing a reply from "shivanshi0613" but their reply doesn't appear in this thread. And I did a few refreshes on this page. Strange...

---

### Post by coffeecat on 2024-01-01
> **Advait said:**
> Strange... I got an email showing a reply from "shivanshi0613" but their reply doesn't appear in this thread. And I did a few refreshes on this page. Strange...

Not strange at all. That was a spam post from a spammer using ChatGPT in order to appear genuine, and which has been removed from public view. If the spam post text appears in your notification email, I suggest you treat the text as you would with any other ChatGPT "advice" - that is with lofty indifference. It is not helpful nor, indeed, relevant.

---

### Post by Advait on 2024-01-01
> **coffeecat said:**
> Not strange at all. That was a spam post from a spammer using ChatGPT in order to appear genuine, and which has been removed from public view. If the spam post text appears in your notification email, I suggest you treat the text as you would with any other ChatGPT "advice" - that is with lofty indifference. It is not helpful nor, indeed, relevant.

Interesting. I've never received UbuntuForums spam before. How can you tell it was spam? Some kind of automated detection? Or manual?

Now that I look closer at their message, is does seem trite and formulaic. Is there some quick way to identify spam? New user with very few posts?

In any case, I'm glad you guys are diligent about catching and preventing spam.

I'm now wondering what is the benefit of spamming UbuntuForums? Must be some benefit or they wouldn't bother.

---

### Post by dragonfly41 on 2024-01-01
[COLOR=#000000]```
The hub is connected to my laptop with a USB-A cable.
```

I use a multi port, multi SSD expander (Startech) but I connect via USB 3.0[/COLOR] [COLOR=#000000]. Perhaps try that? Near the motherboard.[/COLOR]

---

### Post by Advait on 2024-01-01
> **dragonfly41 said:**
> [COLOR=#000000]```
The hub is connected to my laptop with a USB-A cable.
```

I use a multi port, multi SSD expander (Startech) but I connect via USB 3.0[/COLOR] [COLOR=#000000]. Perhaps try that? Near the motherboard.[/COLOR]

I searched google and Amazon for "multi port, multi SSD expander" but saw various types of devices. Could you send me an Amazon link to exact device you're referring to?

Also, I'm using a laptop, not a desktop computer.

You think if I use a USB-C to USB-A adapter that will help? (That would cause me to plug into my USB-C port rather than USB-A.)

```
advait@advait-Bravo-15-A4DDR:~ $ lsusb
Bus 004 Device 002: ID 0480:0900 Toshiba America Inc MQ04UBF100
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 8087:0029 Intel Corp. AX200 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04f2:b648 Chicony Electronics Co., Ltd USB 2.0 Webcam Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
advait@advait-Bravo-15-A4DDR:~$ 
```

So I'm guessing the 2 USB 3.0 devices are my 2 USB-C ports...?

---

### Post by dragonfly41 on 2024-01-01
Not the best time for me respond since I am grappling with an unstable mouse which requires frequent use of Ctrl+F1. So I am in the process of juggling SSD's preparing for fresh installation  and then pulling assets from current unstable ship.


I am not suggesting that these external devices solve your problem but since I experiment a lot I find they offer flexibility.


I am guessing that your hub expander is USB 2.0 based and USB 3.0 is documented to have better performance.


> You think if I use a USB-C to USB-A adapter that will help? (That would cause me to plug into my USB-C port rather than USB-A.)


I am not suggesting that. I suggest an entire USB 3.0 usage for bandwidth reasons. Your port expender might be restricted to USB 2.0 only which might not be enough to cope with 3 SSD's concurrently.  Use USB 2.0 for devices such as mouse.


I have a Dell Inspiron 3268 tower, with various past failed laptops gathering dust.
I have:
10 port USB 3.0 expander (powered) which allows multiple devices to be connected.
These include


Startech 
[1] STARTECH  SDOCK2U33V  USB 3.0 Dual Bay SATA 2.5/3.5" HDD/SSD Docking Station
UNIDOCK33
This has one bay to take a 3.5" HDD and another bay to extract data from small 2.5" drives accumulated from old laptops.
[https://sgcdn.startech.com/005329/media/sets/UNIDOCKU33_Manual/UNIDOCKU33_manual.pdf](https://sgcdn.startech.com/005329/media/sets/UNIDOCKU33_Manual/UNIDOCKU33_manual.pdf)
This site shows examples of usage.
[https://www.amazon.co.uk/StarTech-com-Universal-drive-docking-station/dp/B00T0ZRAOK](https://www.amazon.co.uk/StarTech-com-Universal-drive-docking-station/dp/B00T0ZRAOK)


[2] 
Startech
Startech USB 3.0 expander
[StarTech.com 10 Port USB Hub with Power Adapter - Surge Protection - Metal Industrial USB 3.0 Data Transfer Hu b - Din Rail, Wall or Desk Mountable - High Speed USB 3.1 Gen 1 5Gbps Hub

[3] Caddies
ICY DOCK  MB882SP-1S-1B  EZConvert 2.5" to 3.5" Bay SATA HDD & SSD Converter


ChatGPT
Although use of ChatGPT is frowned upon by forum moderators (and in [forum posting guidelines]("https://ubuntuforums.org/showthread.php?t=2158945")) I do find it very useful to bounce off queries (prompts) as I plod through experiments.
For example opening PHIND.com I posed this query:
in browser:
     

> Is a USB 3.0 port expander hub, powered, advised when mounting three external drives to a laptop? If using USB 2.0 port connector to three external devices what circumstances might cause one disk not to be seen in Ubuntu Disks but seen in GParted? 
 
Your answer is in there. Tip: Use focussed prompts.

---

### Post by Advait on 2024-01-02
I checked and my powered USB hub (Anker) is USB3.

A 4 bay drive docking station looks very tempting. Time to start saving...

And to experiment I ordered a USB-C to USB-B cable to see if that makes a difference.

phind.com is pretty cool.

---

