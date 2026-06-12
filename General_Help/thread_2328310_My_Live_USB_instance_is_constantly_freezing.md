---
title: "My Live USB instance is constantly freezing"
date: 2016-06-19
forum: General Help
---

### Post by xenon3 on 2016-06-19
I'm very often online with UBUNTU from an Live USB Stick, twice maybe 3 times a day my UBUNTU stalls (freezes), I cannot do anything anymore and loose data.

I thought maybe this comes from my WIFI connection, which itself is quite unstable, usually this is in the beginning after a boot, 4 maybe 5 times it goes offline / online, then its normal stable. Was worse when I had no extra space reserved.

Now I have 500 Mb reserved of which there is still around 5 to 25 Mb left (says UBUNTU this is variable, each time different).

But I tried the cable however this does not matter for the freezing.

What can be the cause of the constantly freezing OS each day?

---

### Post by oldfred on 2016-06-20
Just to see system specs, install inxi and run it. copy & paste output in code tags. easy to add with forums advanced editor and # icon.

sudo apt-get install inxi
inxi -Fxz

Should look like this:
oldfred's new SFF system with skylake i5-6500 and 16.04[URL="http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024"]
http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024[/URL]

---

### Post by RobGoss on 2016-06-20
Hello and welcome to the forum, It would help if you could provide the specs for your machine at this point we would just be guessing

---

### Post by xenon3 on 2016-06-21
I installed UBUNTU on internal SSD boot disk (under MSDOS called C: drive) now. Problem over, as in did not reoccur yet in a couple of days. System specs I would only give 2U in a private message by the way, I would be a sitting duck otherwise

---

### Post by ventrical on 2016-06-21
> **xenon3 said:**
> I installed UBUNTU on internal SSD boot disk (under MSDOS called C: drive) now. Problem over, as in did not reoccur yet in a couple of days. System specs I would only give 2U in a private message by the way, I would be a sitting duck otherwise

This is an open global community where we help one another. Reporting hardware specifications does not make one a "sitting duck".

 In some cases the live version will freeze depending on memory availability, graphics adapter and CPU.  This is often caused by hardware being outdated or blacklisted. If we do not know any specifications  then it is very difficult to help. For example If I open a terminal (ctrl+alt+t) and enter in:
```

lspci

```

I will get an output on the screen. In my case it is:

```

ventrical@ventrical-MS-7798:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation B75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
ventrical@ventrical-MS-7798:~$ 

```

so it gives limited information for helpers to postulate or derive a quick solution. Sometimes more information is needed (as with inxi suggested) but it never gives out passwords or any sensitive information where someone can hack your system.

Regards..

---

### Post by RobGoss on 2016-06-21
I have to agree with **Ventrical **these forums are here to try and provide help when needed, providing the specs for your machine is not a risk,  but it's your choice

---

