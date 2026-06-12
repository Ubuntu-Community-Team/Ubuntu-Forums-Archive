---
title: "too much freezing/slow websites : what is the next web browser I should try?"
date: 2020-05-17
forum: General Help
---

### Post by anotherChris on 2020-05-17
I posted[ this thread recently ]("https://ubuntuforums.org/showthread.php?t=2443224")about Microsoft Teams websites freezing my browser/system.  I have also had issues recently with YouTube, Hotmail, and just now Google Maps froze everything.  This is too much.  A huge waste of time and very frustrating.

 I am using the FireFox browser that came installed with Lubuntu 20.04, which I have been using about 2 weeks or so.   I wanted to give FF a chance as I hadn't used it in many years, but now I want to try a different browser.

In one thread, someone suggested I use Brave browser for its Microsoft Teams compatibility, but I don't want to build my life around Teams, which I hate using.

In another thread, someone suggested that YouTube was slow because FF doesn't use hardware acceleration like Chrome.  So, I am wondering if I should try some Chromium derivative.  Maybe Brave, or maybe Vivaldi?

Does anyone have a browser suggestion that they think will solve a problem of Office365, YouTube, Hotmail, GoogleMaps all causing my system to freeze up?  This is really my issue, and not being able to use Tor or something.

---

### Post by Frogs Hair on 2020-05-17
Can you tell us about your hardware, memory,cpu,and graphics.

---

### Post by Autodave on 2020-05-17
Until you get your specs here, you can try *uBlock* add on for Firefox.  I have had a lot of luck with that.

---

### Post by CelticWarrior on 2020-05-17
> **Frogs Hair said:**
> Can you tell us about your hardware, memory,cpu,and graphics.

This ^^^ please, in order to properly evaluate the problem.

That said, recently you posted about an [ancient Dell Inspiron 1545]("https://ubuntuforums.org/showthread.php?t=2442637") and a much newer yet very likely [very limited Intel Compute Stick]("https://ubuntuforums.org/showthread.php?t=2443465"). Regarding the latter even [the current crop of those glorified media players]("https://www.intel.com/content/www/us/en/products/boards-kits/compute-stick.html") isn't good. The cheaper ones are crap and the the best that can be said about expensive one is "not bad". Not even the expensive one is for serious tasks.

So, if your question is still about either one of the aforementioned hardware your seriously need to tone down your expectations. The problem isn't the web browser, it's the websites. The internet of today bares little resemblance with what it was 15 years ago, it's requirements are simply too much for the computers that you already mentioned in your previous threads.

---

### Post by CatKiller on 2020-05-17
> **anotherChris said:**
> In another thread, someone suggested that YouTube was slow because FF doesn't use hardware acceleration like Chrome.  So, I am wondering if I should try some Chromium derivative.  Maybe Brave, or maybe Vivaldi? 

There's [a PPA](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html) that will give you a build of Chromium with hardware accelerated video decode. 

> **CelticWarrior said:**
> The problem isn't the web browser, it's the websites.

Exactly this. They're running arbitrary code on your machine, and there's no incentive to keep it lean since it's not *their* machine that needs to run it. There are extensions you can use that will limit the number of arbitrary programs from *other* sites, which will make your general browsing more pleasant, but bloaty programs like heavy websites run in a browser will require equivalently beefy hardware.

---

### Post by NM5TF on 2020-05-18
> **anotherChris said:**
> I posted[ this thread recently ]("https://ubuntuforums.org/showthread.php?t=2443224")about Microsoft Teams websites freezing my browser/system.  I have also had issues recently with YouTube, Hotmail, and just now Google Maps froze everything.  This is too much.  A huge waste of time and very frustrating.

 I am using the FireFox browser that came installed with Lubuntu 20.04, which I have been using about 2 weeks or so.   I wanted to give FF a chance as I hadn't used it in many years, but now I want to try a different browser.

In one thread, someone suggested I use Brave browser for its Microsoft Teams compatibility, but I don't want to build my life around Teams, which I hate using.

In another thread, someone suggested that YouTube was slow because FF doesn't use hardware acceleration like Chrome.  So, I am wondering if I should try some Chromium derivative.  Maybe Brave, or maybe Vivaldi?

Does anyone have a browser suggestion that they think will solve a problem of Office365, YouTube, Hotmail, GoogleMaps all causing my system to freeze up?  This is really my issue, and not being able to use Tor or something.


FireFox is not to blame for your problems....I use the same apps as you (Office 365, YouTube, GoogleMaps, Microsoft Teams, etc...) on my ancient (2007) dual CPU machine
with no problems....I also tried different browsers ( Chrome, Brave, Vivaldi ) but I ALWAYS come back to FF....

without any information about your hardware, you can't really expect to get help here...

do you have [COLOR="#FF0000"]inxi[/COLOR] installed ??.....if not[COLOR="#FF0000"] sudo apt install inxi[/COLOR] will install that...after install, open a terminal and key in

```
inxi -F
```

post the results here using code tags to make the output more readable...

this will tell us all about your hardware & drivers...we can go from there....

tommy

---

### Post by anotherChris on 2020-05-18
> **Frogs Hair said:**
> Can you tell us about your hardware, memory,cpu,and graphics.

Sorry.  I should know better...  I don't know the most efficient way to do this, but I ran a bunch of terminal commands and compiled the information...

Inspiron 1545 
2GB RAM 160GB memory
======================================
CPU
------------------------------------
Genuine Intel(R) CPU    585  @ 2.16GHz
1 physical processor; 1 core; 1 thread
------------------------------------
model name      : Genuine Intel(R) CPU    
                  585  @ 2.16GHz
cpu MHz         : 2161.105
cache size      : 1024 KB
cpu cores       : 1
Architecture    : x86_64
CPU op-mode(s)  : 32-bit, 64-bit
Byte Order      : Little Endian
Address sizes   : 36 bits physical, 
                  48 bits virtual
===================================
Motherboard
-----------------------------------
Dell Inc. 0G848F 
===================================
Storage
----------------------------------
ATA ST9160310AS
HL-DT-ST DVD+RW GT10N
Generic-Multi-Card
----------------------------------
disk model  ST9160310AS
partition table msdos
1 partition ext4
===================================
Graphics
-----------------------------------
1366x 768
Unknown
The X.Org Foundation
-----------------------------------
description: VGA compatible controller
Mobile 4 Series Chipset 
      Integrated Graphics Controller
===================================
Wireless Interface
-----------------------------------
BCM4312 802.11b/g LP-PHY
Broadcom Inc. and subsidiaries

---

### Post by sdsurfer on 2020-05-18
Also you might look at your connection: your Ethernet hardware speed, speed tests of your connection, etc. I see "Wireless Interface" but try hard wiring it, see if it makes a difference. I doubt  the problem is with the wireless, I use it all the time but it is definitely slower than hard wired.

---

### Post by sdsurfer on 2020-05-18
Also I just noticed you're using the default X.org video driver and the display is listed as "Unknown," see if there is one specific to your device. The problems I've had with browsers often trace back to the wrong video driver for the hardware.

---

### Post by anotherChris on 2020-05-18
> **Autodave said:**
> Until you get your specs here, you can try uBlock add on for Firefox. I have had a lot of luck with that.
Thanks.  I did try uBlock, and I think it helps.

> **CelticWarrior said:**
> This ^^^ please, in order to properly evaluate the problem.
Yeah, my bad. Sorry.  See above and below.

> **CelticWarrior said:**
> a much newer yet very likely very limited Intel Compute Stick... glorified media players isn't good... Not even the expensive one is for serious tasks.
Indeed.  I only use it to play movies on my wife's computer.  It is slow to get going using Netflix or Amazon via FireFox, but once it gets going, the movies play fine.

> **CelticWarrior said:**
> you seriously need to tone down your expectations. The problem isn't the web browser, it's the websites.
Okay.  I hear you, but I just upgraded from 17.10 running an outdated version of Chromium, and until YouTube really completely broke (couldn't use the Share or Add to Playlist functions at all) in the last few months, it was running much better than up-to-date FF on 20.04.  For example, I used to use Google Maps quite a bit.  Not as fast as I'd like, but worked perfectly fine.


> **CatKiller said:**
> There's a PPA that will give you a build of Chromium with hardware accelerated video decode. 
That looks interesting, but everything I do in Linux involves a steep learning curve for me, so I will try that if everything else fails first.


> **NM5TF said:**
> do you have inxi installed ??.....post the results here using code tags to make the output more readable...
```

System:    Host: ptr Kernel: 5.4.0-29-generic x86_64 bits: 64 Desktop: LXQt 0.14.1 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Portable System: Dell product: Inspiron 1545 v: N/A 
           serial: <superuser/root required> 
           Mobo: Dell model: 0G848F serial: <superuser/root required> BIOS: Dell v: A07 
           date: 05/13/2009 
CPU:       Topology: Single Core model: Intel 585 bits: 64 type: MCP L2 cache: 1024 KiB 
           Speed: 2161 MHz min/max: 1000/2167 MHz Core speed (MHz): 1: 2161 
Graphics:  Device-1: Intel Mobile 4 Series Integrated Graphics driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1366x768~60Hz 
           OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) v: 2.1 Mesa 20.0.4 
Audio:     Device-1: Intel 82801I HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-29-generic 
Network:   Device-1: Marvell 88E8040 PCI-E Fast Ethernet driver: sky2 
           IF: enp9s0 state: down mac: 00:25:64:3e:9d:33 
           Device-2: Broadcom and subsidiaries BCM4312 802.11b/g LP-PHY 
           driver: b43-pci-bridge 
           Device-3: Dell Wireless 365 Bluetooth type: USB driver: btusb 
           IF-ID-1: wlan0 state: up mac: 00:22:5f:bf:3f:a4 
Drives:    Local Storage: total: 149.05 GiB used: 7.74 GiB (5.2%) 
           ID-1: /dev/sda vendor: Seagate model: ST9160310AS size: 149.05 GiB 
Partition: ID-1: / size: 145.71 GiB used: 7.74 GiB (5.3%) fs: ext4 dev: /dev/sda1 
Sensors:   System Temperatures: cpu: 64.0 C mobo: N/A 
           Fan Speeds (RPM): cpu: 3800 
Info:      Processes: 142 Uptime: 1h 13m Memory: 1.90 GiB used: 774.0 MiB (39.7%) 
           Shell: bash inxi: 3.0.38 

```



> **sdsurfer said:**
> Also I just noticed you're using the default X.org video driver and the display is listed as "Unknown," see if there is one specific to your device. The problems I've had with browsers often trace back to the wrong video driver for the hardware.

Hmmm... I am pretty ignorant about that kind of thing; any ideas after looking at the above from inxi?


Thanks for all the help and advice above!

On another thread I posted, commenter Holger suggested this...

[QUOTE=Holger_Gehrke]One thing I did back when I had just 4 GB in my laptop was to limit the number of content-processes in Firefox ('Settings'->'General'->'Performance'->'Number of content processes') to two instead of four (might be set to 8 now, at least that seems to be the default). This will not stop it completely but should make it less frequent. Also the add-ons / extensions you use can have a serious impact on memory use. Switching from 'Adblock plus' to 'uBlock Origin' was one of the things which helped me a lot.[/QUOTE]

I don't know if this "fixed" my problem, but I did get through work today using the Microsoft O365 Teams website without any slowing or freezing.  I am going to keep using FF set up this way for a while to see if reducing the content processes seems to have definitely changed something.

However, I am still interested in any other comments/advice people may make.  Thanks!

---

### Post by anotherChris on 2020-05-19
> **anotherChris said:**
> I don't know if this "fixed" my problem, but I did get through work today using the Microsoft O365 Teams website without any slowing or freezing.  I am going to keep using FF set up this way for a while to see if reducing the content processes seems to have definitely changed something.

Well, today is froze again, and when it did, nothing was working.  Not Ctrl+Alt+T and not Ctrl+Fn+Alt+F2 or any other hotkey combos.  I had to hard-restart with the power button again.  Very disappointing.

---

### Post by sdsurfer on 2020-05-19
Off topic, but you can try REISUB (BUSIER backwards) next time.
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by anotherChris on 2020-05-20
> **sdsurfer said:**
> Off topic, but you can try REISUB (BUSIER backwards) next time.
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

Yeah, thanks.  Somebody recommended that, too, but I've got to write it down for my dumb brain sometime *before* the freeze.

---

### Post by JakcV on 2020-05-23
I have a similar laptop as your spec with slightly better Intel core 2 duo T8100.

I would say, normally I will open at most 3 tabs like Team, YouTube, Hotmail, and Google Maps. 2 tabs are better.
The spec does not allow to run these application smoothly. Team, Youtube will use up ~1GB of  RAM

---

### Post by anotherChris on 2020-05-25
> **JakcV said:**
> I have a similar laptop as your spec with slightly better Intel core 2 duo T8100.

I would say, normally I will open at most 3 tabs like Team, YouTube, Hotmail, and Google Maps. 2 tabs are better.
The spec does not allow to run these application smoothly. Team, Youtube will use up ~1GB of  RAM

It's frustrating because for a long time I was using Chromium on Lubuntu 17.10 on the same laptop, and it worked great for a long time, maybe years.  I could have like 15 tabs open in Chromium, no problem... [sigh...]

---

### Post by dragonfly41 on 2020-05-25
I have had a few freezes recently when parsing large files and I looked into the subject and came across this.

[https://github.com/rfjakob/earlyoom](https://github.com/rfjakob/earlyoom)

I think my issue is I need to buy more RAM.

Incidentally I often have many tabs open in Chromium but some (YouTube etc.) are resource hungry.  
I would install Stacer dashboard to monitor your resources.

---

### Post by JakcV on 2020-05-26
> **anotherChris said:**
> It's frustrating because for a long time I was using Chromium on Lubuntu 17.10 on the same laptop, and it worked great for a long time, maybe years.  I could have like 15 tabs open in Chromium, no problem... [sigh...]

Ya. I used this laptop since 8.04LTS. On old days, I can open quite a number of tabs. I use it as my development machine. The changing in IT cause all these website use more and more processing power, long time ago, JavaScript is only used for simple logic. 

My smartphone is more powerful than my laptop now.

---

### Post by GhX6GZMB on 2020-05-26
I gave up on FireFox quite some time ago. It used to be a nice browser, but has expanded into extreme bloatware. Also it has had a memory garbage collection problem from it's birth, which has not been solved yet. This leads to it locking up after some time (days to weeks) because it has filled up the allocated memory. This is both on Win and Ubuntu systems, BTW.

For the last two years, I've used Opera on both Win and Ubuntu. Lightweight, fast and stable. I can let it run for months without issues.

Just my $0.02

---

### Post by RabbitWho on 2020-05-27
Google maps used to work fantastically in Firefox, street view was so smooth, like a video game. The conspiracy theorist in me says they changed it on purpose to make their own browser look better.

I'd consider using another browser (not chrome) but there are certain add-ons on Firefox that don't have equivalents in Opera that I really can't live without

Anyway re. OP's stuff, a workaround is I am using the teams app for Linux, it works fine. I look fervently forward to being able to install it when a vaccine is found.

---

### Post by anotherChris on 2020-05-27
> **RabbitWho said:**
> Google maps used to work fantastically in Firefox, street view was so smooth, like a video game. The conspiracy theorist in me says they changed it on purpose to make their own browser look better.

I'd consider using another browser (not chrome) but there are certain add-ons on Firefox that don't have equivalents in Opera that I really can't live without

Anyway re. OP's stuff, a workaround is I am using the teams app for Linux, it works fine. I look fervently forward to being able to install it when a vaccine is found.


I didn't know, didn't even imagine, there was a Teams app for Linux.  Will check it out, thanks!  The only browser add-on I really, really want is a website translator.

---

