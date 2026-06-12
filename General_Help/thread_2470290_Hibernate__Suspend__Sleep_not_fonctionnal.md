---
title: "Hibernate / Suspend / Sleep not fonctionnal"
date: 2021-12-24
forum: General Help
---

### Post by mururoa-fr on 2021-12-24
Hi there,
I'm quite new to Ubuntu Desktop but not to Ubuntu or Linux.
My system is on Kubuntu 21.10 and is up to date.
Recently I bought a new laptop : Asus Vivobook. Brand new hardware with Intel i5.
So far so good but the next day I had my system frozen a few minutes after start. Very reproducible. It turn out that the WiFi card driver was unstable. rtw88_8821ce driver.
I try a few workarounds and ended in installing liquorix kernel.
So with Liquorix no more freeze and all is good ... except I cant neither suspend/sleep or hibernate.
I added a 8 Gb swap for the hibernation but no can do.
If I try to suspend the system freeze and stays powered on with screen displayed even if I close lid.
I did not manage to find usefull logs of that.
If I try to hibernate, the system is powerd off but after power on it just restarts like if I had powered off instead of hibernated.
Any tips or log level I can increase to see what happen ?
Oh forgot to say I have encrypted filesystem in case it can be related to that.

---

### Post by GhX6GZMB on 2021-12-24
Can't help you with Liquorix (first time I've ever heard of it, must be very exotic).

But hibernate is turned off by default on xUbuntu systems. Suspend ought to work, though.

Seems to me you're having a basic problem, and then loading another on top of it. Get the basic system running first.

---

### Post by mururoa-fr on 2021-12-24
There is no such basic problem, just the wifi driver is buggy on default Ubuntu kernel.
I should be back to Ubuntu kernel on 22.04 when the bugs will have been fixed.
But for now I have to stick with Liquorix or another kernel where the wifi is ok. With default Ubuntu I can use the laptop about 10 min before freeze.
I guess it's not related to Liquorix but I can try another kernel if it helps. What would help much more is to know where to find the logs or increase log level to understand what is causing freeze upon suspend.
I may start to use an external syslog server but not sure I will get more with it.

---

### Post by HermanAB on 2021-12-25
Err… instead of a different kernel I would just install a new WiFi driver. Granted, it is hard to do anything if the network isn’t working - you may need to run a cable till you got the WiFi fixed.

---

### Post by mururoa-fr on 2021-12-25
Ok, I can try, where can I find a new driver for my device ?
The device is : Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter

---

### Post by mururoa-fr on 2021-12-29
I've already looked @realtek and there is no Linux driver there. The driver for the device don't exist for windows 11 or Linux and is from 2017 !
Ubuntu driver is buggy for my hardware (at least) and ubuntu latest driver is 5.5.2.1 from ... may 2021 so I will get back the freeze bug if I switch back to ubuntu stock kernel.

---

### Post by mururoa-fr on 2021-12-29
Just tried to update the bios and suspend again.
It was somehow better. Suspend seemed to work then I press power again and all seems to come back ... but just freezed; nothing usable.
Here it is, suspend and then the next boot after hard shutdown and power on again :
```

ec 29 12:03:30 mururoa-VivoBook kernel: PM: suspend entry (s2idle)
Dec 29 12:06:15 mururoa-VivoBook kernel: microcode: microcode updated early to revision 0x88, date = 2021-03-31
Dec 29 12:06:15 mururoa-VivoBook kernel: Linux version 5.15.0-11.1-liquorix-amd64 (steven@liquorix.net) (gcc (Ubuntu 11.2.0-7ubuntu2) 11.2.0, GNU ld (GNU Binutils for Ubuntu)
 2.37) #1 ZEN SMP PREEMPT liquorix 5.15-13ubuntu1~impish (2021-12-22)
Dec 29 12:06:15 mururoa-VivoBook kernel: Command line: BOOT_IMAGE=/vmlinuz-5.15.0-11.1-liquorix-amd64 root=/dev/mapper/vgkubuntu-root ro quiet splash vt.handoff=7

```

---

### Post by mururoa-fr on 2022-01-04
Hi there,

I start another thread here since it's kinda slow and messy in an other one.
Ok so, I own a brand new vivobook S15 (X513EA).
So far so good but suspend / hibernate does not work on it.
I searched and searched around and found a way  to put the laptop in hibernate mode.
It just need to issue standard "echo disk > /sys/power/state" and the laptop goes smoothly into hibernation.
So far so good but I dont manage to configure that so it goes to hibernate when the lid close.
In logind.conf I set :
```

HandleLidSwitch=hibernate
HandleLidSwitchExternalPower=hibernate

```
In sleep.conf I set :
```

HibernateMode=shutdown
HibernateState=disk

```
but it seems that's no correct and/or complete since when close the lid the laptop try to suspend but fail and freeze so I have to press 10 seconds on power off and then power on to start it.
What did I missed ?

---

### Post by howefield on 2022-01-04
Duplicate threads merged.

---

### Post by GhX6GZMB on 2022-01-04
Look, you keep diddling around with liquorix, chocolatix, bonbonix and whatever.
[U]
Get the basic install running first!
[/U]
Preferably one that has a wide user base, eg, Ubuntu, Kubuntu, Lubuntu, Xubuntu, Mate etc. This gives the most helpful responses.

_Then_ the hibernation etc. can be fixed. But building on an unstable foundation wlll just not work.

---

### Post by mururoa-fr on 2022-01-05
> **ml9104 said:**
> Look, you keep diddling around with liquorix, chocolatix, bonbonix and whatever.


If you read the full thread you may notice I'm on Liquorix because the wifi driver freeze my laptop in less than 10 minutes each run on stock kernel. I'll go back to stock kernel as soon as driver will be updated.
But that's NOT the point now.
The laptop GOES into hibernate with Liquorix. I guess it would go into hibernate with stock kernel if it would run long enough to try.
So, you may not comment just out of subject.
And that's why I started a new thread wich was merged : to get out of this thread liquorix and wifi.

The question is : how to configure so that the laptop goes into hibernate when I close the lid ? I mean without sudo su -; echo disk > /sys/power/state but automatically.
OFC the default/stock/official Ubuntu config dont work as is. BTW I run up to date 21.10 Impish.

---

