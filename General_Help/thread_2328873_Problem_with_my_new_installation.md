---
title: "Problem with my new installation"
date: 2016-06-25
forum: General Help
---

### Post by alo12 on 2016-06-25
hello, i have installed the xubuntu 14.04.04 lts 64bit  to my system. First of all is the 64 bit the right choice considering my system specs? Secondly si was wondering if because if i should make any change in the additional drives because i have get a frozen screen (which force me to restart my system) a couple of times. Pleace check my sytem settings above 

2 Ubuntu 14.04 trusty 4.2.0-38-generic 64bit (el_GR.UTF-8, XFCE xubuntu), Ubuntu 4.2.0-27-generic
3 Intel Core i5 CPU 660 3.33GHz &#8214; RAM 2999 MiB &#8214; MSI P55-GD55 (MS-7589) - MSI MS-7589
4 nVidia G92 [GeForce GTS 250] [10de:0615] {nouveau}
5 eth0: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03) &#8942; wlan0: 0bda:8171 Realtek RTL8188SU 802.11n WLAN Adapter

---

### Post by RobGoss on 2016-06-25
Hello and welcome, If you already have Lubuntu installed on your system you should be able to see if your system is a 32-bit or 64-bit by going to the system settings there should be a** system info** or **Detail, **tab that will provide this information

If your system is in fact a **64-bit** you can also install **32-bit ISO** as well on that system and it should ran as any other distro. There are also lighter versions of you Ubuntu that my perform better if your machine is a older model, example [Lubuntu]("http://lubuntu.net/") or [kubuntu ]("http://kubuntu.org/")

You can also run this command:

```
[FONT=monospace]uname &#8211;m[/FONT] 
```


[LIST]
[*]If the response is i686, you have a 32-bit version of Linux.
[*]If the response is x86_64, you have a 64-bit version of Linux.
[/LIST]

Best of luck

---

### Post by grahammechanical on 2016-06-25
Your machine specifications are a lot better than those for my machine and I am running Ubuntu 64 bit with the Unity user interface that requires a more powerful video adapter than does Xubuntu.

Changing the video driver might fix the freezing problem. Nouveau is the open source video driver. Additional Drivers will offer appropriate Nvidia drivers. Do not try to install the very latest Nvidia drivers that can be downloaded from the Nvidia web site. You will find that Nvidia have dropped support for the GTS 250 from their newest video drivers.

The GTS 250 is a little bit more powerful than my GT 220 but they use the same Nvidia drivers. Additional Drivers will offer you nvida 304 or 340. Both are listed by the Nvidia web site as supporting the GTS 250.

Regards.

---

### Post by vasa1 on 2016-06-25
But> RAM 2999 MiBIt's puzzling that an i5 machine will have only 3 GiB RAM.

---

### Post by grahammechanical on 2016-06-25
Self-built using components from an existing machine. It keeps the initial upgrade costs low with the possibility of further hardware upgrades in the future.

Some of us cannot justify the costs of a new, top of the range store bought machine.

---

### Post by Impavidus on 2016-06-25
My laptop has an i5 processor and came with 3 GB ram. I first installed 32 bit Ubuntu, later installed 64 bit and upgraded the ram to 8 GB.

With your system you'll not see much difference in performance between 32 bit and 64 bit. Just continue with 64 bit. It's more future-proof.

Installing proprietary drivers for your nvidia graphics may help.

---

