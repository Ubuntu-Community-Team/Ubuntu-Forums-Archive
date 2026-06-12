---
title: "Ubuntu desktop on Intel NUC keeps freezing intermitantly"
date: 2022-01-20
forum: General Help
---

### Post by uipojehdx on 2022-01-20
[COLOR=#D7DADC][COLOR=#000000]I  have installed Ubuntu 20.04.3 LTS [/COLOR][/COLOR][COLOR=#000000]([/COLOR][COLOR=#D7DADC][COLOR=#000000]5.13.0.27-generic) on my fanless Intel NUC 7i7BNB (i7-7567u cpu, 8gigs of  ram, and 250 gb samsung 970 Evo nvme, Dell S2721DGFA monitor set to 60hz). I keep on getting intermittant freezes  which mean I need to reboot the machine. They don't seem to be because  of temps (35c - 60c) or any particular activity - I can be surfing the web. I have updated to the latest bios.

[/COLOR]
[COLOR=#000000]Any ideas what could be causing it?[/COLOR]

[/COLOR]

---

### Post by TheFu on 2022-01-20
There are multiple places in the system where heat can be an issue. NUCs are well known for this problem.
I fried a NUC and it never worked again.  I switched to an ITX solution with good cooling and never worried about it again.

---

### Post by uipojehdx on 2022-01-21
I have been keeping an eye on the temps, but I suppose I could be missing something. It crashed yesterday once when the htop screen was still active, when all four cores were below 5% activity, so I am not sure its heat. I am using watch -n 2 sensors and both cores below 30c right now.

---

### Post by tea for one on 2022-01-21
I have a (similar) Intel NUC8i3BEH together with a Kingston nvme drive.
My device also has a fan (it is the taller NUC model - 51mm high). 
Following a few freezing incidents a couple of years ago, I found this [https://www.tekbyte.net/fixing-nvme-ssd-problems-on-linux/](https://www.tekbyte.net/fixing-nvme-ssd-problems-on-linux/)

I edited the relevant line in Grub by adding (in blue)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#0000FF"]nvme_core.default_ps_max_latency_us=0[/COLOR]"
```

It cured my problem although I do not fully understand the original problem nor the remedy.

Anyway, you have a different PC and a different brand nvme, so my comments may not be pertinent.

As a general observation, have you updated your Intel UEFI firmware and the Samsung nvme firmware?

---

### Post by uipojehdx on 2022-01-21
Thanks for the link to the tekbyte site, I think i might go there next. I was given that link on reddit I think too yesterday.

I have updated the bios for my specific nuc, so that should include UEFI firmware?? I have not done the Samsung nvme firmware, I need to look into that.

Another bit of info, I had an  issue installing linux to the machine where the installer complained  about a cd-rom issue, which was odd as I was using a memory stick. I had  the same error with two different memory sticks and two distro's both  mint and ubuntu.

I also realised  that one of the usb connectors (I have two which are on extentions from  the main unit as its in a fanless hd plex case, one extension is from  the board and one from the front usb port) was not working, so I  disconnected both usb extensions last night. I still have the two on the  rear, and I could still access the front if I take the lid off. Its  still early days but no crash since I have disconnected these. Time will tell...

---

### Post by tea for one on 2022-01-21
> **uipojehdx said:**
> Another bit of info, I had an  issue installing linux to the machine where the installer complained  about a cd-rom issue, which was odd as I was using a memory stick. I had  the same error with two different memory sticks and two distro's both  mint and ubuntu.

Can you add more info about this complaint? 
My guess would be something specific in your hardware set up? - the same error message following the use of two different distros and two different memory sticks?

> **uipojehdx said:**
> I also realised  that one of the usb connectors (I have two which are on extentions from  the main unit as its in a fanless hd plex case, one extension is from  the board and one from the front usb port) was not working, so I  disconnected both usb extensions last night. I still have the two on the  rear, and I could still access the front if I take the lid off. Its  still early days but no crash since I have disconnected these. Time will tell...

[COLOR="#0000FF"]fanless hd plex case[/COLOR] - I'm not familiar with this?
Discovering a non-functioning usb extension  - again possible hardware issue?

What is connected to the usb extensions?
Are the devices permanently connected?

> **uipojehdx said:**
> I still have the two on the  rear
Two extensions or two usb ports?

> **uipojehdx said:**
> Its  still early days but no crash since I have disconnected these. Time will tell...
Good news - progress made.

Freezing problems are difficult to solve but it is always a good idea to go back to basics.
Unplug everything possible (sometimes disable wired and/or wireless) and then add the peripheral devices in one by one. Test and retest.

---

### Post by uipojehdx on 2022-01-21
> Can you add more info about this complaint? 
My guess would be something specific in your hardware set up? - the same  error message following the use of two different distros and two  different memory sticks?


I can't be much more specific as it happened during installing, I tried ubuntu, then mint, then ubuntu again, in the end adjusting the partitions manually seemed to help and I could complete the installation.

>                             [COLOR=#0000FF]fanless hd plex case[/COLOR] - I'm not familiar with this?

[This ]("https://hdplex.com/hdplex-h1-v3-fanless-computer-case.html")is the case I am using. Originally the NUC was used as a Roon music server (I now use Ubuntu Server). I was about to sell it, when I decided to try it as my daily desktop as it uses MUCH less electricity that my normal desktop PC which is a gaming PC really.

> Discovering a non-functioning usb extension

Concerning the USBs, to fit the internals of the NUC into the HD plex case necessitates using two extension cables, the first is from one of the front USB slots and is an extender cable which you can connect to the rear of the new case. The second connects directly to the board, and then again to the rear panel, its this cable that I think is the culprit. 

> Good news - progress made

Yes, thank you! I have been using the PC all day today. htop is reporting 7.5 hours up time so far, so I am hopeful!!

---

### Post by tea for one on 2022-01-21
Your case is an attractive piece of kit (8 times the volume of my regular NUC).
Lots of ports and room for multiple drives.

Concerning the culprit cable, can you swap it with another?
It is sometimes difficult to figure out if the cable is faulty or the receptive parts where you insert the cable?

Anyway, 7.5 hours today without a freeze looks promising.

Best wishes

---

### Post by HermanAB on 2022-01-22
FWIIW, my NUC7 runs the latest Ubuntu reliably from power failure to power failure (every few weeks).  I should buy the poor little thing a UPS. Apart from power, there are zero issues with it. The NUC runs Motion for my security cameras, so it is quite busy.

---

