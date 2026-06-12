---
title: "Boot fails with overclocking error"
date: 2018-11-21
forum: General Help
---

### Post by thebeagle2 on 2018-11-21
I'm trying to reboot my Ubuntu18 desktop computer but it fails with a message saying
[INDENT]*Overclocking failed! Please enter Setup to re-configure your system.*[/INDENT]

So I do that but I'm not exactly sure what setting to change. I'm not currently doing anything to intentionally overclock. 

If boot from the BIOS I get a message that says[INDENT][I]Gave up waiting for suspend/resume device
/dev/sda2: clean, 318835/59039744 files, 17499728/236131328[/I][/INDENT]

I've tried booting with a few different settings but it always fails with the above messages. Does anyone have suggestions for how I can get my box up and running again?

BACKGROUND

The trouble started when I upgraded from Ubuntu 18.04 to 18.10 then rebooted and ran into this failure. Before that I had tried to set it up so that it would do upgrades without a reboot. I forget all of the steps I did for that, but I think I installed snapd. The reboot initially failed with a message about snapd not starting with canonical-livepatchd so, after reading that snapd is only for Ubuntu 14 and 16, I went into safe mode and did a sudo apt autoremove --purge snapd. That didn't help. I'm not sure if it hurt or not.

I'm running on an ASUS X99-A/USB 3.1 motherboard. And Intel Core i7-5820K CPU @ 3.3 GHz processor.
There is a BIOS setting call Ai Overclock Tuner that I have set to Auto.

---

### Post by Autodave on 2018-11-22
At this point, I would recommend that you do a clean install of 18.04.  If you can boot to the install medium, you will be able to copy and files you need to save to an external source.  If you cannot boot to the install medium, you will probably need to access the BIOS and then look for an option to reset to factory settings and go from there.

I rarely have any luck upgrading from one version to another: just not worth the hassle.  I only use the LTS releases and always do clean installs.

---

### Post by thebeagle2 on 2018-11-24
I'm afraid you might be right. I've been procrastinating this procedure. I haven't done a clean install since I bought the computer new in 2014, but maybe it's time.

---

### Post by CatKiller on 2018-11-25
> **thebeagle2 said:**
> 
There is a BIOS setting call Ai Overclock Tuner that I have set to Auto.

That is overclocking your computer. Turn it off for now.

The error message is saying that it's failing to boot from suspend, and that it's unsure how much of your filesystem is in good shape. Without overclocking, I'd boot onto a live cd or live USB and run fsck on the drive.

---

