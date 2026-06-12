---
title: "system periodically crashes - caps lock blinks"
date: 2007-04-24
forum: General Help
---

### Post by ckellner on 2007-04-24
Approximately since the last update to feisty, my system periodically (typically after 3-5 hours) freezes. 
That is, no keys work anymore, and only caps lock blinks.

How can I go about finding the cause?
A quick look at the log files does not result in anything suspicious, but i do not exactely know what to look for.

---

### Post by thomasloo on 2007-04-30
I have the exact same problem on a IBM Thinkpad T42

Thomas

---

### Post by jleasure on 2007-05-02
same problem on an hp pavillion zv6007us, amd64 feisty.

---

### Post by KevinCLovesU on 2007-05-13
Add me on to this list, hp pavillion ze4600 with AMD Athlon XP,1.86 mHz, 192 mib RAM.

---

### Post by ckellner on 2007-05-13
I have the strong suspicion that this problem occurs only if I am connected using the wireless connection, not using lan.. i have a broadcom 4318 wireless chip,  what about others?

---

### Post by brenix on 2007-11-01
Ive had this happen to me twice now in the past 20 minutes. The computer will completely freeze up and the caps lock light will flash on and off. Im using a thinkpad t61p and it seems to happen when I am downloading heavily through my wireless...

Is anyone else running conky. I noticed after killing it, my computer wouldnt freeze anymore..

---

### Post by rwshoemaker on 2007-11-28
Same issue in Gutsy on HP dv8000 Pavilion laptop.  I am running an atheros pcmcia wireless card, have broadcom disabled.  Seems to happen when Firefox is running, perhaps using StumbleUpon.  Happened repeatedly since upgrade and clean install to Gutsy.  Have to kill power to reboot - no response from any key or touchpad.

---

### Post by willie_wang on 2007-12-11
aye, here too! happens only when running deluge... wondering if anyone else has this problem with deluge?

happened when i installed ubuntu and xubuntu gutsy.

---

### Post by josephpiche on 2007-12-12
When the caps lock blinks after a freeze, it is a kernel panic trying to tell you some piece of hardware is probably dead. If you are _sure_ it's not a hardware problem, then please look through bug reports and file one if needed.

---

### Post by _Zardoz_ on 2007-12-12
Same problem here. As far I can see it happens when I run deluge...

---

### Post by stunner on 2007-12-14
Same problem - Gutsy, HP DV8210 (Broadcom 4318).  Magic sysreq doesn't work, hard poweroff required.  Tends to occur when cpu usage hits 100% for an extended period of time (overheating?), seems to be related to wireless as well.

---

### Post by mous3 on 2007-12-15
I'm using a ProLink WFE-100 PCMCIA wireless adapter. I cant find it in device manager but I can see wireless connection. Upon trying to establish connection, it just crash the system. I'm not sure what chipset is ProLink using though. Its running on a laptop P4 1.9Ghz, 512MB RAM. I tried installing through windows driver but it doesn't seem to recognize the driver either.

---

### Post by ac7ss on 2007-12-16
Lets start with the standard  "Me Too".

A good diagnostic would be to Ctrl-Alt-f1 and let the machine run till it crashes. When it does, it dumps to stderr (the terminal) and you will get a better idea as to what is causing it.

---

### Post by stunner on 2007-12-16
Would if I could, but virtual terms haven't worked with fglrx for me for some time now :/

---

### Post by kvonb on 2007-12-19
-

---

### Post by willie_wang on 2007-12-21
It seems to be a problem when downloading large torrents of say over 4GB for me. all the rest of the torrents seem to download fine.

Switching to Transmission instead of Deluge seemed to help somewhat.

---

### Post by kvonb on 2007-12-21
-

---

### Post by stevoo on 2007-12-21
i had the same exact problem ...it would hang up periodically with no evidence why ...

at first i believed it was azureus, as it would only do it when i had it open, so i didnt start it for a while and i was wrong :( 

So another program was crushing my 7.10, as it started after upgrading the system. 
So after a lot of tweaking and uninstalling i found the error in ...ehh so long ago that i cant remeber which one was it ....

but it was one that i could edit the way my ubuntu looked, i think it was emerald theme manager, so if you have something like that, post up. 

That was non responsive with my feisty and end up crashibg it up ....:popcorn:

---

### Post by brenix on 2008-01-07
> **kvonb said:**
> I fixed my problem, it was a mangled filesystem.  I'd been having problems with SD cards and my camera batteries dying while copying files over.

Try doing a disk check, boot into recovery mode and type:

```
fsck
```

It should check and give you some info as well.

I recently reformatted my machine and the issue seemed to have gone away. Seems as if this may be why it was crashing. Though i'm still hesitant about it being large transmissions or overheating..looks like i'll wait and see..

---

### Post by FeralTitan on 2008-01-13
Same problem, I have a compaq.
I am certain this has to do with one of two things
1. Wireless 
2. Downloading torrents

---

### Post by bothapn on 2008-01-28
Ok.. torrents should not be able to cause this problem as they are run in userspace.
Now, networking could cause it. ACPI events can DEFINITELY cause it (thinking dual-core problem in kernel). My pc does exactly the same. 
I do however have a failing hdd (dmesg shows this).. BUT:
  - The failing hdd does not host any critical system partitions (such as /usr,/,/var etc).. so the system should be able to log data

My gut feelilng is that this is a acpi bug in the kernel with pc's that has a dual-core cpu. 
Now to get that damn error output...

---

### Post by stunner on 2008-01-29
Good info, however my system is not dual-core.  Of course, there may be more than one set of conditions that leads to this.

---

### Post by FeralTitan on 2008-02-03
From further research.

Libtorrent, causes a fault in the WiFi driver, which inturn crashes the system.This is with acpi turned off. To test this, start 3 or more large torrents at the same time (over 2 gigs each) . This problem occurs with any bittorrent client that uses libtorrent i.e. rtorrent, Transmission, deluge etc..

PS: With the acpi turned on the system crashes even quicker

---

### Post by sharpycore on 2008-02-10
I can report the same problem on 64bit Gutsy, bcm43xx chipset. It happens when I'm running Transmission torrents and although my computer has been overheating a little recently (I suspect dried up heatsink compound on the processor) it seems that people don't think this is a factor?
How do I go about turning ACPI off for a little more stability?

---

### Post by Magenga on 2008-02-17
I've got the same problem on a fresh new install of Gutsy on HP Pavilion dv5000 European Version.
Even if I've got a 64b, I preferred to install a 32b.

I had problems with the integrated bcm43xx drivers, since I've got a bcm4318, and I put on ndiswrapper, just like I've done on any other distro I've installed (I've been using Gentoo for a couple of years).

But I noticed that **if the wireless card has to manage lot of incoming connections**, due to aMule (I think could be my case) or Bittorent (as I read in the thread), kernel says "Goodbye cruel world".

For now, I can just manage to use a wired connection when I have to download and the wireless one to study.

I seriously think that the problem is in the **ndiswrapper** kernel module, but I can't manage to solve it.

---

### Post by Mercuzio on 2008-03-15
Me too, happens when I resume the laptop and it tries to connect to my wireless network. Also the caps lock key led sometimes (like know) just stops working. WTF???

IBM X31, Cisco Wireless 'B' mini pci card.

cheers.

---

### Post by gladstone on 2008-04-04
Add me to the list also...

Problem seems to be re-occuring while using DownThemAll w/ Firefox. Laptop w/ Intel 2200BG wireless here.

---

### Post by wodzu777 on 2008-04-10
I know that I should not post it here, but I have the same problem.

My system is gentoo on 2.6.24 with fluxbox only.
Sytem quite often freezes without a reason. It started today after some changes in the kernel- unfotunately don't remeber after what exact change...
But it does after e.g. screensaver works for a few minutes. And then only the blinking CAPS LOCK... :/
But I can honestly say that it is not connected with wireles card (disabled and module removed).

---

### Post by wodzu777 on 2008-04-16
Hi guys!
Its me again if you read this post :P

I found a solution .. probably. Have u got an Intel graphic card (an integrated one)? As I found somewhere that the latest intel driver is a bit doggy...
I downgraded the driver (to the previous version) and now everything seems to be ok... Also I changed the xorg.conf and added:
```
Option    VideoRam    128000 
``` in the "Device" Section  (maybe a bigger number set... )

Hope it will help ya.

Ave goodun!

---

### Post by Rinnan on 2008-04-16
@wodzu777

There have been a few updates, which version of the Intel driver are you running?  I'd like to try that as well.

---

### Post by gladstone on 2008-04-20
I'm also using an integrated Intel and would be interested in this, though I wonder if 8.04 will fix it?

---

### Post by wodzu777 on 2008-04-23
Oki guys.
Just checked what I have on my brilliant gentoo and found am using i810 driver- 2.2.99.903.
Also I got the "VideoRam" option (in xorg.conf) set to the maximum of the card, which is samin like "393216".
People mostly prefer changing the "i810" to "intel" in the xorg.conf, but I didn't. And it seems alright..
Hope this is what ur lookin 4..

Since I had changed that I have no problem with the kernel panic (blinking CapsLock).

And if u got an Intel wireless then use the iwl drivers (iwlwifi built in kernel since.. cant remember, but in 2.6.24 for sure ;) ) instead of iwp ones.

Take care guys- Im comming back to gentoo forum ;)

---

### Post by zxscooby on 2008-04-29
Im having the same problem with a broadcom card BCM94311MCG wlan mini-PCI with ndiswrapper . It only occurs while using wireless.

---

### Post by carl.davis on 2008-06-10
There hasn't been a post here in a while, does that mean everyone's issue was solved with the video ram setting?

I don't have an integrated Intel video card but do have:

iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25

I currently think this might be related to the wireless card since I used my laptop all day yesterday with Ethernet only and suffered no problems. Today on wireless it has locked up 10-15 times. I can seem to reproduce the problem almost every time after establishing a Cisco vpn session and then trying to rdesktop.

---

### Post by carl.davis on 2008-06-10
> **carl.davis said:**
> think this might be related to the wireless card since I used my laptop all day yesterday with Ethernet only and suffered no problems. Today on wireless it has locked up 10-15 times. I can seem to reproduce the problem almost every time after establishing a Cisco vpn session and then trying to rdesktop.

This does appear to be related to the wireless as I have plugged into Ethernet and haven't had any problems. The only time I get lock ups is when I am using the wireless.

---

