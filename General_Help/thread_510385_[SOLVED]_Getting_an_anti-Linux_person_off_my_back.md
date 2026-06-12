---
title: "[SOLVED] Getting an anti-Linux person off my back"
date: 2007-07-26
forum: General Help
---

### Post by sci-fi guy on 2007-07-26
My dad can't seem to understand why I use Linux when it has so many "loopholes" (as he calls any inconvenience/lack of functionality when compared to Windows). Basically, if something does not work with Linux, he thinks that it is Linux's fault. The three biggest inconveniences I have that he attacks are:

1.   Linux does not work with WPA (I only recently found out about WPA-supplicant). So when I got wifi I changed the network's encryption to WEP, and my brother's computer started having chronic wifi issues, although my mom's computer took the change in stride (Both run XP). My dad blamed Linux. Fortunately, I found out about wpa-supplicant and changed back to WPA. I would bet much money that my dad has no clue what WEP or WPA are.

2.   He points out that I have no sound when running Ubuntu, but I do when i (rarely) run Vista. I come back with "Vista wouldn't give me sound either if the drivers hadn't been added by Toshiba". So he asks why Toshiba didn't supply drivers for Linux. He doesn't seem to understand the concepts of a monolithic kernel, volunteer-written code, or even drivers in general. So I say that Toshiba does not make Linux drivers. He responds with "That's a loophole", whatever he means by that.

3.   Some websites are IE-only (this has been an issue ever since I started using Firefox in Windows). He thinks that this is because IE is superior. :roll:  Correct me if I'm wrong, but don't the makers of those websites have to go out of their way to make it IE-only? The fact that FireFox is not allowed to visit those sites is looked at as FireFox's fault. When I say that FireFox is more secure, he doesn't understand why we need more security when we haven't had any problems (he also gets irritated when I run malware scans on my mom's computer because there *is* no malware because *we didn't install it.* ](*,) #-o

This is a guy who rarely touches a computer unless he is looking around on eBay.  And even that is rare.  He seems to suffer from all the misconceptions identified in the [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm") article. Especially in regards to the sound. "Why can't you get it fixed by talking to tech support or something? Why are you asking other people in a chat room? (I have never visited a chat room. I am in the forums.) What do they know? (another example of not understanding the concepts behind FOSS)"

He is driving me up the wall with his cyclical reasoning. I would like to be able to say that something does not work without him saying that Linux is flawed.

On a side note, would updating the kernel possibly fix my sound? I currently have version 2.6.20-16, it has updated once from automatic updates, and I am wondering if I can update straight to the latest version from kernel.org safely. And how to do it.

Sorry if I bored you or was not making much sense.

---

### Post by Steve1961 on 2007-07-26
I wouldn't worry about it.  Some people - mainly those who have little clue about any operating system - will always moan about anything that doesn't do things in the way they're used to.  As an IT tech I spend most of my working life fixing windows PCs for people and although I try and convert them to Linux in the process it's an uphill battle againts MS brainwashing and conditioning.

Anyway, afraid I can't help you with the sound issue, but you might want to look at the user agent switcher extension for firefox - [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by sci-fi guy on 2007-07-26
So that IE-only sites think that I am using IE?

---

### Post by reckless2k2 on 2007-07-26
ok....getting sound to work is a different issue and can possibly be resolved by posting your results after running "lspci -v" fromt he command line. 

as far as your father, i'm confused about whether this is your machine or whether you have converted everyone in the house to linux. if your father is so resistant to it, i'd suggest not forcing it on him. i don't force linux on anyone that does not have an open mind to it. i'm not sure of your situation but it sounds controversial in general and linux is the means to express it more fully. i don't know if your role in your house is the resident IT person or not either but some people want it their way and that's all. i'd suggest not stepping on toes or trying to prove a point because it will be fruitless. this is one of those life's lessons that not everyone is going to agree and there are those that want to infringe on your rights to freely express yourself while wrapping it in a disguise of something as rudimentary as a operating system choice. 

the community will support your interest and growth because believe me we have all been in the same situation as the "outcast" of the operating system world. rather than focusing on the weakness of linux, focus on the strengths of linux. it's like a debate. count the devices in your house or in the public in general that run linux. talk about the backbone of the internet. pixar movies totally linux. cell phones. tivo. the list goes on and on.

---

### Post by hessiess on 2007-07-26
thay are difarent, in many ways linux is superior to windows, espetialy vista junk

the websites that wont run in ff probaly depend on vbscript

---

### Post by reckless2k2 on 2007-07-26
"IE only" sites you mean sites that are driven by activeX will require IE yes. That's it. As long as you have your acrobat reader, flash, and java plguins then the rest should be ok. there might be some issues with certain odd flash sites but that is usually resolved by adding a certain plugin as well. you will not be able to circumvent activeX dependent sites though in linux.

installing a thing called wine and IE4linux does work to some degree though but it's a little buggy. you can try it. sounds like you need this site to complete your ubuntu experience:

[http://easylinux.info/wiki/Ubuntu:Feisty](http://easylinux.info/wiki/Ubuntu:Feisty)

---

### Post by Steve1961 on 2007-07-26
> **sci-fi guy said:**
> So that IE-only sites think that I am using IE?

Exactly, my bank's site refused to work with Firefox -unsupported browser message - but with this extension I can fool it into thinking it's IE6.  Then everything works fine.

---

### Post by stchman on 2007-07-26
> **sci-fi guy said:**
> My dad can't seem to understand why I use Linux when it has so many "loopholes" (as he calls any inconvenience/lack of functionality when compared to Windows). Basically, if something does not work with Linux, he thinks that it is Linux's fault. The three biggest inconveniences I have that he attacks are:

1.   Linux does not work with WPA (I only recently found out about WPA-supplicant). So when I got wifi I changed the network's encryption to WEP, and my brother's computer started having chronic wifi issues, although my mom's computer took the change in stride (Both run XP). My dad blamed Linux. Fortunately, I found out about wpa-supplicant and changed back to WPA. I would bet much money that my dad has no clue what WEP or WPA are.

2.   He points out that I have no sound when running Ubuntu, but I do when i (rarely) run Vista. I come back with "Vista wouldn't give me sound either if the drivers hadn't been added by Toshiba". So he asks why Toshiba didn't supply drivers for Linux. He doesn't seem to understand the concepts of a monolithic kernel, volunteer-written code, or even drivers in general. So I say that Toshiba does not make Linux drivers. He responds with "That's a loophole", whatever he means by that.

3.   Some websites are IE-only (this has been an issue ever since I started using Firefox in Windows). He thinks that this is because IE is superior. :roll:  Correct me if I'm wrong, but don't the makers of those websites have to go out of their way to make it IE-only? The fact that FireFox is not allowed to visit those sites is looked at as FireFox's fault. When I say that FireFox is more secure, he doesn't understand why we need more security when we haven't had any problems (he also gets irritated when I run malware scans on my mom's computer because there *is* no malware because *we didn't install it.* ](*,) #-o

This is a guy who rarely touches a computer unless he is looking around on eBay.  And even that is rare.  He seems to suffer from all the misconceptions identified in the [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm") article. Especially in regards to the sound. "Why can't you get it fixed by talking to tech support or something? Why are you asking other people in a chat room? (I have never visited a chat room. I am in the forums.) What do they know? (another example of not understanding the concepts behind FOSS)"

He is driving me up the wall with his cyclical reasoning. I would like to be able to say that something does not work without him saying that Linux is flawed.

On a side note, would updating the kernel possibly fix my sound? I currently have version 2.6.20-16, it has updated once from automatic updates, and I am wondering if I can update straight to the latest version from kernel.org safely. And how to do it.

Sorry if I bored you or was not making much sense.

Lets address each one of those points.

1.  Linux can do WPA.  As a matter of fact I do WPA2 on my home network.  I used to only do WPA since my girlfriend's XP laptop could only do WPA.  Now that she got a new Vista equipped laptop it supports WPA2.

2.  I have  Toshiba laptop and the sounds works perfectly.  Here is the fix if you have an SB450 HDA sound card.

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

3.  There are VERY FEW websites that must have IE.  I have not encountered one in a long time.  There are a few websites (M$ especially) that the formatting looks better in IE, but they still work using Firefox.

Site to your father about all the phishing, stolen passwords, hacked buffers, etc.  XP has had so many security vulnerabilities in the past they are too many to mention.  So you father thinks that security is a non-factor in today's computing age?

Are you running Feisty?  If so your Toshiba laptop should have an Atheros card.  My site will help you get your laptop set up right.  I can watch DVDs and play CDs, burn CDs and DVDs.  Play mp3 and rip CDs to mp3.  My laptop can do everything that an XP laptop can besides get viruses and spyware.

---

### Post by misfitpierce on 2007-07-26
Dont worry about what other ppl say or do about linux... If they like it or not is personal preference and not for you to worry about. Why dont you just show them what Vista takes ram wise on fresh boot and example at how linux is nowhere near that with Beryl etc on.

---

### Post by daveisadork on 2007-07-26
Load his computer up with viruses and spyware. That usually shuts them up. :popcorn:

---

### Post by stchman on 2007-07-26
> **daveisadork said:**
> Load his computer up with viruses and spyware. That usually shuts them up. :popcorn:

Yes, my dad just cannot believe that Linux is virtually immune to Windows shortcomings.  He says "there has to be viruses and spyware for Linux" or "how is Microsoft no able to deal with it".  Good question.

Wait until the original posters dad has to upgrade his entire PC to run Vista.

---

### Post by Gary.M on 2007-07-26
> **sci-fi guy said:**
> My dad can't seem to understand why I use Linux when it has so many "loopholes" (as he calls any inconvenience/lack of functionality when compared to Windows). Basically, if something does not work with Linux, he thinks that it is Linux's fault. The three biggest inconveniences I have that he attacks are:



You don't have a Linux/Windows problem, you have a relationship problem. The two of you aren't communicating properly... you can work on that, or just accept that's the way it is... your choice. I don't know how old you are, but believe me, there will be some time in your life when you will value your Dad for what he is, and develop a mature relationship with him... even later, when he's gone, you'll appreciate the stuff you shared with him, not the disagreements... C'est la Vie.

---

### Post by sci-fi guy on 2007-07-26
Thanks for all the replies. I have Linux on my current computer (laptop, so I can't simply buy a new sound card) and my old system that I gave to my elementary school-aged brothers (my Junior sister uses it occasionally) My Sophmore brother has his own laptop running XP, and my mom has XP also (my dad uses that one). I got this laptop as a graduation present, and am dual-booting Ubuntu (feisty) and Vista. And I am the resident IT person.

I have Wine and use it for StarCraft, but the User-agent switcher FF extension is working for me (thanks Steve!) Which bring me to another issue. I told him about the extension, and he was unhappy about it because it was "dishonest" to tell sites that I am using IE when I am using FF. He tried to compared it to using a fake ID to get alcohol when one is under 21.

Security is not an issue for my father because I handle the security.  He has no clue how much trouble Ad-Aware SE, Spybot, and ZoneAlarm keep my parents out of (and I installed them without permission, a very touchy issue with them) Citing phishing and such to him falls on deaf ears because he thinks that if his security is compromised, he would know about it. My family does not like any changes that they are not notified about because way back when SP2 was released for XP, SBC's browser quit working for a while there. So now they don't even trust Windows Update. Heck, even I have had bad experiences with graphics card drivers from M$ for a wide variety of systems.

I did not know about Linux's WPA support when I got the laptop. I had read many threads mentioning that WPA wasn't supported, but I did not think to see how old those threads where.

I can see the RAM difference plain as day (although that doesn't actually seem to translate to Vista being much slower, as I have never run anything more intense that Azureus or FF in it. But i would not serve any purpose pointing that out to him, because while Ubuntu uses ~240-50MB when idling and Vista uses ~600-700, my parents use XP, and that ate up 260MB until I made as many tweaks as I could w/out them noticing, and brought their usage down to 240MB. Also, a more properly maintained laptop I got onto recently used 150MB under XP (maybe it wasn't using SP2?).

Also, he wants to know why I Linux is a personal choice. Since all computers (that he knows of) come with Windows, he wonders why I put myself through the trouble of using Linux when it "doesn't work".

Finally, waiting until he gets Vista is going to be impractical, because the computer runs just fine as-is for it's current use: Web browsing and Solitare, with my brothers playing Battle for Wesnoth (which they learned of when I installed it on the Linux machine) and shockwave-based web games (they claim that my old Linux system won't run it, and to be honest, I have not seen any mention of support for Shockwave in the forums, just Flash.) when the other brother is on the Linux box.

And I am not going to intentionally going to go in search of viruses, because he might blame it on the fact that Linux and Windows are on the same network (that's what he did when I had the network running WEP and my brother was having issues.)

---

### Post by sci-fi guy on 2007-07-26
Oops, all that and I forgot to post the output. Here it is:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0a00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at f0b00000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Memory at f0a80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f0600000-f06fffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f0700000-f07fffff
        Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f0800000-f08fffff
        Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at f0d44000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=0b, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f0900000-f09fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 2000 [size=256]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0700000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at f0906000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=07, secondary=08, subordinate=0b, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 17
        Memory at f0905000 (32-bit, non-prefetchable) [size=2K]
        Memory at f0900000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 18
        Memory at f0904000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 18
        Memory at f0905800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by dasunst3r on 2007-07-26
Don't give up on Linux just yet.  He will wonder why your operating system is more responsive than his even on older hardware soon enough.

---

### Post by sci-fi guy on 2007-07-26
> **Gary.M said:**
> You don't have a Linux/Windows problem, you have a relationship problem. The two of you aren't communicating properly... you can work on that, or just accept that's the way it is... your choice. I don't know how old you are, but believe me, there will be some time in your life when you will value your Dad for what he is, and develop a mature relationship with him... even later, when he's gone, you'll appreciate the stuff you shared with him, not the disagreements... C'est la Vie.

You are right, we do have a communication problem, but I have a hard time explaining things in a way that he won't find objectable. In fact, this is our only major stand-off, and it starts with the standard "How was your day?" pleasantries. If I mention news about or troubles with Linux, he asks why I bother with Linux when Windows is sufficient...

---

### Post by sci-fi guy on 2007-07-26
> **dasunst3r said:**
> Don't give up on Linux just yet.  He will wonder why your operating system is more responsive than his even on older hardware soon enough.

Who's giving up on Linux? I just don't think I can sell it to him on performance at this point. My laptop (2 months old) and my old system (1.5 yrs.) have the highest specs in the house, with my parents computer (3-5 yrs.) taking up third and my brother's laptop dead last (2 yrs).

And I no, I am not using the systems' ages as indicators of performance. But my dad might

---

### Post by yabbadabbadont on 2007-07-26
Just politely remind him that you will probably be the one to pick out his nursing home in the future...  :twisted:

That should get him off your back.  :D

---

### Post by stchman on 2007-07-26
You have one of the ICH7 Intel sound cards.  My girlfriend has more than likely the same laptop as you.  You need to update ALSA.  To do this do the following:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

This did the trick on her laptop.  Have you been able to get the media reader and webcam on your laptop working?

If you want to prove to your dad that viruses and spyware are a real threat then disable the router firewall and the AV and AS on his PCs.  See how quick that open PC gets hacked.  When he comes to you complaining you can say "if there was a threat you would know about it".

Just don't talk about Linux to him.  I would figure he would want his son to be technically proficient.

My dad uses Vista on his laptop and does nothing but complain about Vista.  He states that "I paid for Vista" as his reason.

---

### Post by sci-fi guy on 2007-07-26
I think I tried that solution your script is based on before, and I lost my GUI. But I will try the script...

Edit: GUI still here, Sound still gone with Autodetect set in Sound Preferences

In regards to you question, no, I have not gotten the webcam to work. But the Media Card reader worked right away. Do you have an integrated Fingerprint reader, and have you got that to work?

I don't think that he wants me to be technically proficient in a relatively obscure OS. If I work in the tech field (which I intend) then I will need to be proficient in Windows (which I am anyways)

---

### Post by isecore on 2007-07-26
It seems your father needs to have his free tech-support revoked. 

I've met a few people who had similar delusions like your father - nosey people who knew nothing about the things they pretended to know about, and had the same weird circular logic and lack of sound reasoning or even the slightest shred of humility in the face of people who knew more than them.

Thankfully this is none of my relatives, but none the less I found that the solution is as simple as it is cruel - let them start dealing with their own crap. I stopped giving free tech-support to these people, and instead they themselves had to start learning about malware, viruses and the general crappiness of Microsoft-products. Instead of acting like a nice guy and protecting them from these things, I just stopped doing it.

Yes, it goes against my mostly kind nature, but some people don't deserve help. Especially not after they act superior and keep criticizing the one who they expect to help them with this. I mean, you don't start talking trash with your mechanic and act like you know everything about engines when in fact you couldn't tell the difference between a V8 and a turbodiesel? The mechanic would up and walk away immediately. Yet us computergeeks have to take this crap standing, and we're expected to do amazing things for free - especially for relatives.

Again, I'm happy that none of my parents or relatives are morons. But when dealing with this attitude I always do the same thing - no more free tech-support. Let them deal with the monkeys at Best Buy (or whatever local equivalent) and find out that they fubared their system and charged out of their *** for it. Maybe it'll teach them a little respect for people with more experience and deeper understanding.

I understand that this will be difficult since it's your father, but it seems that he needs some tough love.

---

### Post by stchman on 2007-07-26
> **sci-fi guy said:**
> I think I tried that solution your script is based on before, and I lost my GUI. But I will try the script...

Edit: GUI still here, Sound still gone with Autodetect set in Sound Preferences

In regards to you question, no, I have not gotten the webcam to work. But the Media Card reader worked right away. Do you have an integrated Fingerprint reader, and have you got that to work?

My girlfriends laptop doe not have a fingerprint reader.

On the script it refers to a web page, I recommend you also look at that page:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Look at the bottom of the page.  What model number is your laptop?

---

### Post by sci-fi guy on 2007-07-26
> **stchman said:**
> My girlfriends laptop doe not have a fingerprint reader.

On the script it refers to a web page, I recommend you also look at that page:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Look at the bottom of the page.  What model number is your laptop?

That's the page that I lost my GUI trying. My laptop's model number is an A205-S4587

Unfortunately for the "don't give tech support" technique, ZoneAlarm is a great product. For the past year I haven't cleared anything off of the system but tracking cookies.

---

### Post by stchman on 2007-07-26
> **isecore said:**
> It seems your father needs to have his free tech-support revoked. 

I've met a few people who had similar delusions like your father - nosey people who knew nothing about the things they pretended to know about, and had the same weird circular logic and lack of sound reasoning or even the slightest shred of humility in the face of people who knew more than them.

Thankfully this is none of my relatives, but none the less I found that the solution is as simple as it is cruel - let them start dealing with their own crap. I stopped giving free tech-support to these people, and instead they themselves had to start learning about malware, viruses and the general crappiness of Microsoft-products. Instead of acting like a nice guy and protecting them from these things, I just stopped doing it.

Yes, it goes against my mostly kind nature, but some people don't deserve help. Especially not after they act superior and keep criticizing the one who they expect to help them with this. I mean, you don't start talking trash with your mechanic and act like you know everything about engines when in fact you couldn't tell the difference between a V8 and a turbodiesel? The mechanic would up and walk away immediately. Yet us computergeeks have to take this crap standing, and we're expected to do amazing things for free - especially for relatives.

Again, I'm happy that none of my parents or relatives are morons. But when dealing with this attitude I always do the same thing - no more free tech-support. Let them deal with the monkeys at Best Buy (or whatever local equivalent) and find out that they fubared their system and charged out of their *** for it. Maybe it'll teach them a little respect for people with more experience and deeper understanding.

I understand that this will be difficult since it's your father, but it seems that he needs some tough love.

I have stopped giving free tech support.  I tell my girlfriend to not tell her friends that I will fix their computers for free.  I will give some free advice but that is about it.

If someone she knows casually wants PC help I charge.  After what Firedog and Geek Squad charge I deserve something as well.  Now my buddy does some lawn work and takes care of my lawnmower for me in exchange for me keeping his PC happy.

I agree with you that people who don't know about PCs should not spout off to people who know.

---

### Post by stchman on 2007-07-26
> **sci-fi guy said:**
> That's the page that I lost my GUI trying. My laptop's model number is an A205-S4587

Unfortunately for the "don't give tech support" technique, ZoneAlarm is a great product. For the past year I haven't cleared anything off of the system but tracking cookies.

Her laptop is a P205-S6307.  My laptop is an A135-S2246.

Her sound card is that Intel ICH7 and she has the Intel GMA950 card.  I have her sound and video card (1440x900) and 3D acceleration working properly.  People were saying install the 915 res package when all it needed was the xserver-xorg-video-intel package.

---

### Post by aysiu on 2007-07-26
Who cares what your dad thinks? Just use Linux and be happy. There's no point in arguing with him or trying to convince him into changing his beliefs. He seems pretty set in his ways.

---

### Post by sci-fi guy on 2007-07-26
> **stchman said:**
> I agree with you that people who don't know about PCs should not spout off to people who know.

One has no problem speaking up on a subject if they do not know how much they don't know.

---

### Post by Sayers on 2007-07-26
> **isecore said:**
> It seems your father needs to have his free tech-support revoked. 

I've met a few people who had similar delusions like your father - nosey people who knew nothing about the things they pretended to know about, and had the same weird circular logic and lack of sound reasoning or even the slightest shred of humility in the face of people who knew more than them.

Thankfully this is none of my relatives, but none the less I found that the solution is as simple as it is cruel - let them start dealing with their own crap. I stopped giving free tech-support to these people, and instead they themselves had to start learning about malware, viruses and the general crappiness of Microsoft-products. Instead of acting like a nice guy and protecting them from these things, I just stopped doing it.

Yes, it goes against my mostly kind nature, but some people don't deserve help. Especially not after they act superior and keep criticizing the one who they expect to help them with this. I mean, you don't start talking trash with your mechanic and act like you know everything about engines when in fact you couldn't tell the difference between a V8 and a turbodiesel? The mechanic would up and walk away immediately. Yet us computergeeks have to take this crap standing, and we're expected to do amazing things for free - especially for relatives.

Again, I'm happy that none of my parents or relatives are morons. But when dealing with this attitude I always do the same thing - no more free tech-support. Let them deal with the monkeys at Best Buy (or whatever local equivalent) and find out that they fubared their system and charged out of their *** for it. Maybe it'll teach them a little respect for people with more experience and deeper understanding.

I understand that this will be difficult since it's your father, but it seems that he needs some tough love.

Well my mom is nice and I help her. I'd stop helping her but then I'd get in trouble and I'd feel bad. She never says linux is bad but just doesn't want to learn it. My dad however used to think linux was great till he stopped smoking. Now I hate being around him. I could go into something deep about it but he's more than an *** now. It's hell being around him.

---

### Post by dasunst3r on 2007-07-28
As far as tech support goes for me outside my family and good friends, I charge:
[list]
[*]Parts (if used... that's pretty obvious)
[*]Gas money
[*]Fridge privileges and food while on the job
[*]A payment that the customer deems "fair," although I note how much they would be charged if I was n00b Squad
[/list]I typically get half of what n00b Squad charges, and that's enough to make me happy.  After all, they just saved a boofload on tech support and I get some money to save up on more stuff.

---

### Post by strabes on 2007-07-28
Your dad obviously knows nothing about computers or the internet. It just sounds like your dad is close-minded about things like this. I'd just say forget about trying to make him understand. He's a noob, like you said, all he does is browse ebay and play solitaire.

You should have gotten a dell so that everything works flawlessly out of the box.

Have you thought of installing beryl or compiz and showing him? How about uninstalling all the antivirus/malware software you have on their windows box and see how long it takes for their computer to become unusably slow. It took about 1 month for my parents' new dell computer to stop booting until I installed ubuntu on it. Now all I do for tech support is update it.

Your experiences with your dad sound like my experiences with talking to liberals.

---

