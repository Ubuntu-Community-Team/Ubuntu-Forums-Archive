---
title: "freezing problem possibly related to firefox"
date: 2006-12-06
forum: General Help
---

### Post by fhslacrosse13 on 2006-12-06
I have a problem with ubuntu 6.10 "randomly" freezing.  I'm not sure of the cause but it has happened about 5 time since I've installed ubuntu (earlier this morning).  I wish I knew a little more about linux so that I could give more info about the problem but I'm pretty much a noob to the linux world.

---

### Post by Wim Sturkenboom on 2006-12-06
Does it really freeze or just stops responding for a number of seconds? Had the same problem on my 6.06 system (corrupted screens and freezes up to 30 seconds with nv driver). Installation of the nvidia drivers solved the issue in my case.
It happend in (all) programs (firefox, openoffice, ....)

Can you post your HW specs and which driver your using for your video card?

---

### Post by sether_edwardo on 2006-12-06
It completely freezes.  I have to restart by holding in the power button.  I have a dell demension 8300.  My video card is a ati radion X1900 ( i think).  I've had the problem ever since I installed the OS.  It happened both before and after I installed the drivers for the video card.  Other than that I dont know of any other information I know to give.  I did realize that it happens with any program that I have up at the time.



Also, just wondering if anyone is having problems logging in.  I had to make a new username because my other one (fhslacrosse13) would send me to the redirecting page but then back to the login page.

---

### Post by monkeylytics on 2006-12-08
I'm seeing this problem as well. The Firefox application that I normally run is from a tgz file from Firefox's site rather than the Firefox that comes with my Edgy upgraded from Dapper. 

It will freeze my system hard enough times that I know using Firefox this way is a risk. I'm not sure if it's a plug-in problem or what. I'm trying to run it with the Firefox that comes with the distribution to see if it solves the problem, but regardless of the root cause, it's very disappointing for a Linux distribution to freeze like this. It's the first time this has happened since I've been using a Mozilla browser with Linux which is 4+ years now.

---

### Post by monkeylytics on 2006-12-08
I didn't have this problem with Dapper either. But there's something about Edgy and my Firefox that freezes it hard sometimes.

---

### Post by Brightrock on 2006-12-22
Same problem.  Any solution yet?  I'm going to have to give up my linux craze again for a few months pretty soon here.  That's the pattern so far.  I use Linux until it starts really slowing me down, then I leave for a few months and come back, and have fun checking out the improvements until it slows me down again, or I can't figure out/ fix something.  I'm not complaining, just explaining why I sure wouldn't want to be without Windows yet.

---

### Post by tjhanlon on 2006-12-29
Hi all,

First noob post - migrating to Edgy from OSX. I'm running a Compaq n610c laptop Intel Pentium M 2 GHz, with 1 Gb RAM, and the ATI 7500 card.

I've also been having problems with Edgy freezing - mostly with Evolution Mail, but also with Firefox. It's the 'fox that came bundled on the ISO. I get completely locked out (keyboard and mouse), and have to reboot the system by holding down the power button. 

Not sure if there's a fix yet, thought I'd throw my 2 cents in.

Thanks,

tjh

---

### Post by dnite on 2006-12-29
I used to have a problem like this with Ubuntu Edgy. Let me ask a couple questions...

1. When the system freezes, are you still able to move the mouse around, just not able to click anything and the keyboard is unresponsive as well?

2. Are you running compiz/beryl 'eye candy' ?

If you answered yes to both of those questions, turn off the eye candy and you shouldn't have any more random crashes. I've been random crash free since I stopped using compiz/beryl.

---

### Post by LosingMyPigeon on 2006-12-29
I also have experience this problem.  Very strange.  I'm running 6.10 on a couple boxes have NEVER had a problem.  Last night, on a fresh install, I had the Firefox freeze out my mouse and keyboard, locking up the system.  I had to power down.

To the new Ubuntu user who started this thread, please don't get discouraged.  There is something odd at the moment that will be resolved.  This distro is great.

---

### Post by jdpipe on 2006-12-29
Hi there

I'm getting these problems too. In fact, sometimes Firefox freezes the system (mouse cursor stops moving, with the circular 'hourglass' cursor, no keyboard response, no moving stuff anywhere on the screen), and sometimes it triggers a restart. Actually I have noticed Thunderbird has been causing same problem on occasions. Epiphany is a bit better but still crashes (but doesn't crash/restart the whole system).

Things I have done recently with my system:
(1) added new RAM. Have run 'memtest' from Ubuntu GRUB menu, no probs reported.
(2) installed Hauppauge PVR-350 card. Works OK, not sure if it (+software) could be causing probs?
(3) switched from VESA video drivers to SiS drivers by manually editing .conf file for xserver-xorg.

Other things might also have happened but can't think of anything else. Far as I can tell anything that causes a problem as severe as this must be a kernel bug, right?

JP

---

### Post by tjhanlon on 2006-12-29
Hi all,

Thanks again for the replies.

I'm less convinced that this has Firefox as it's root cause; tonight, Google Earth caused a screen crash.

Yes, the pointer freezes (no mouse, just trackpad) and the keyboard is locked out.

I'm wondering if there are memory problems causing this, but I noticed that the crashes only seem to happen when the pointer is in the upper right quadrant of the screen.

Yes, I do have Beryl installed, but the crashes/freezes are independent of the window manager. I thought that that might be a problem, so I'm just logging into the gnome Ubuntu session. I did try Xfce, but I uninstalled it. The freezes occurred before Xfce, so I'm not sure that's the problem.

I've heard a lot of great things about Ubuntu, and I'd like to stick with it. I'm wondering if a clean install might not be the best solution, tho...

More ideas much appreciated.

Thanks,

tjh

---

### Post by tjhanlon on 2006-12-29
> **dnite said:**
> I used to have a problem like this with Ubuntu Edgy. Let me ask a couple questions...

1. When the system freezes, are you still able to move the mouse around, just not able to click anything and the keyboard is unresponsive as well?

2. Are you running compiz/beryl 'eye candy' ?

If you answered yes to both of those questions, turn off the eye candy and you shouldn't have any more random crashes. I've been random crash free since I stopped using compiz/beryl.

No. complete freeze - nothing is responsive. No movement, no 'nuttin.

tjh

---

### Post by tjhanlon on 2006-12-29
> **LosingMyPigeon said:**
> I also have experience this problem.  Very strange.  I'm running 6.10 on a couple boxes have NEVER had a problem.  Last night, on a fresh install, I had the Firefox freeze out my mouse and keyboard, locking up the system.  I had to power down.

To the new Ubuntu user who started this thread, please don't get discouraged.  There is something odd at the moment that will be resolved.  This distro is great.

Thanx, I've heard great things about it. I'm really more curious as to what's causing the behavior.

thanx,

tjh

---

### Post by tjhanlon on 2006-12-29
> **jdpipe said:**
> Hi there

I'm getting these problems too. In fact, sometimes Firefox freezes the system (mouse cursor stops moving, with the circular 'hourglass' cursor, no keyboard response, no moving stuff anywhere on the screen), and sometimes it triggers a restart. Actually I have noticed Thunderbird has been causing same problem on occasions. Epiphany is a bit better but still crashes (but doesn't crash/restart the whole system).

Things I have done recently with my system:
(1) added new RAM. Have run 'memtest' from Ubuntu GRUB menu, no probs reported.
(2) installed Hauppauge PVR-350 card. Works OK, not sure if it (+software) could be causing probs?
(3) switched from VESA video drivers to SiS drivers by manually editing .conf file for xserver-xorg.

Other things might also have happened but can't think of anything else. Far as I can tell anything that causes a problem as severe as this must be a kernel bug, right?

JP

Well, I don't even get the waiting circular cursor. I intended to reply to the last few posters, but after typing my missive, the machine froze again, and I lost the message. So I replied to each one.

The freeze is independent of ac adapter/battery power.

Curioser and curioser

tjh

---

### Post by jdpipe on 2006-12-30
I have removed my additional RAM and haven't seen any crashes since then. The RAM was bought from a high-street electronics shop, and might have been the wrong spec or slightly incompatible in some way.

Another thing I was noticing was the very occasional dump of messages about something called 'APIC' to the text console (i.e. GNOME would exit, but Linux would still be running in text mode and displaying kernel messages about 'APIC'). My reading on this seems to suggest that this is a likely sign of hardware problems.

Sounds like it might be worth you trying to use some different RAM, maybe?

---

### Post by tjhanlon on 2006-12-30
It could be RAM... The motherboard on this laptop maxes out at a gig, and I have a 1 gb PNY stick. When Ubuntu loads, there aren't any memory warnings flags... 

Again, noob question, but how do I view the system logs just prior to the freeze? Is there a way to have those logs saved so that I can view them later?

Thanks,

tjh

---

### Post by jdpipe on 2006-12-30
I would nevertheless try using some different RAM if you can.

And regarding the logs, try using the GNOME 'System' menu, under 'Administration'->'System Log'. Whatever is in the log you should see there.

---

### Post by lucaslucas on 2006-12-30
Hi all,


I'm seeing this problem as well. I am running ubuntu 6.06. I run Firefox and it crashes, then I changed to mozilla and still crashes. I installed several version of firefox, but still got the same problem. I think that if it is making the same problem with different people it should be a kernel bug. 

It happens the same as this post:
"It will freeze my system hard enough times that I know using Firefox this way is a risk. "
But as I said it is not only firefox, but it seems to be net related software, it does not happen with VMWARE, Office, or other CPU or memory intensive appilcations.

It will freeze completely I have to reboot, no keyboard, no mouse, no remote login.
My computer is and AMD-athlon 64 X2, with 3GB of ram.

It is really disapoiniting, I changed from Fedora, but now I do not know waht to do?

Lucas

---

### Post by jdpipe on 2006-12-30
Lucas: you seeing any funny stuff in your system logs?
Fedora currently uses 2.6.18 kernel, Edgy has 2.6.17. I'm hoping that these problems will go away when we get a kernel update for Ubuntu but I don't know.
I would definitely try running with just one RAM stick and see if that fixed your problems. I have run the exact same installation of Ubuntu (via this USB drive) on lots of different computers and have only had this problem with the computer I'm on, and only when I added some new RAM. You have a lot of RAM (3GB) so perhaps it's not all the same type?

Cheers
JP

---

### Post by lucaslucas on 2006-12-31
JP, my RAM is all the same type, but I can check that, I hope is not a bug with the memory.

I did not find any funny stuff in the log. The problem is that I use the computer for work, so I can not play a lot because I need it!. I will send the log the next time it crashes.

Cheers,


Happy new year

---

### Post by tjhanlon on 2006-12-31
> **jdpipe said:**
> I would nevertheless try using some different RAM if you can.

And regarding the logs, try using the GNOME 'System' menu, under 'Administration'->'System Log'. Whatever is in the log you should see there.

DOH!

Yeah, nothing interesting in the system logs.

Just a lot of annoying freezes. On a perhaps related subject, OpenOffice Base wizard routinely causes a freeze - can't exit the wizard without closing the program at the end thereby effectively thwarting my ability to create a database.

Is this a hardware or OS issue? I'm beginning to wonder if, by changing the OS, these system hangs stay or go away. If they stay, regardless of the OS (which, on this dual boot system Windows [ugh!] doesn't seem to have any problems) then it's the hardware. If not, then (as I'm beginning to suspect) it's the distro.

tjh

---

### Post by jdpipe on 2007-01-02
I'm thinking it's an intermittent hardware problem of some kind. While I had the faulty RAM, it seemed that Windows XP also behaved badly. But perhaps it's a hardware problem that only surfaces with particular kernel versions -- not sure. As I said, I removed some RAM and my problem went away completely.

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

### Post by jdpipe on 2007-01-04
Seems as though this issue may have multiple root causes, perhaps. I believe my problems were in some way related to faulty RAM, but it's likely that APIC issues are also occurring with the current Ubuntu Linux Kernel.

I see that some people on the Net report APIC issues being associated with ethernet cards. This would explain why mostly the problems present themselves when Firefox is used.

If you have seen this firefox crash problem, please post here what ethernet card you're using. Perhaps it's relevant.

Cheers
JP

---

### Post by sarshet on 2007-01-08
I am having the same problem on my box. It used to run Windows XP without any problems, so I am not convinced it is a hardware problem.

I have only had the freeze when working in FireFox. I just tried bodzasfanta's suggestion and didn't solve the problem. First try of running FireFox resulted in a freeze.

Any other ideas? this problem simply renders the box useless! :mad:

---

### Post by VoodooSteve on 2007-01-08
I'm another who has had this problem. However, it only presented itself when I have used Edgy. I upgraded to Edgy from Dapper soon after Edgy came out last fall only to find firefox causing my system to crash. I downgraded back to Dapper and haven't had the problem since. I know others have had this problem while running Dapper so I'll have to agree with the idea of there being numerous causes to this problem. Last night I decided to upgrade to Edgy again hoping this problem had been solved... :-k

Edit: I just had my first freeze while browsing this forum. I'm considering downgrading back to Dapper...

---

### Post by jdpipe on 2007-01-08
VoodooSteve,

Can you post some info about your hardware: RAM, ethernet card, type of hard drives, etc? And whatever else seems relevant.

Given that this is only an intermittent bug for what seems to be a small number of users, we need to try to work out what the factors might be.

I am also running a system that I upgraded from a Dapper system, FWIW.

Cheers
JP

---

### Post by VoodooSteve on 2007-01-09
P3 1GHz, 256MB RAM, nVidia GeForce4 MX 440 64MB RAM Video card, 8GB Hard Drive, D-Link Ethernet manufactured by Realtek.

It's a pretty cheap and older system, and that might, at least for me, be the problem right there.

---

### Post by Megatog615 on 2007-01-09
Hmm... I also have this problem on an AMD Athlon 1333MHz with 512MB RAM and an NVIDIA Geforce MX 4000. I upgraded to the nvidia-glx-legacy drivers from nv and now I get an odd lockup problem that allows me to continue to move the mouse, but keyboard and anything other than moving the mouse is locked. The screen is also locked up. I've changed back to nv drivers to see if there is any difference.

---

### Post by tjhanlon on 2007-01-11
Hi all,

Problem is >>apparently<< solved - - I memtestered (is that even a word?) my RAM, and there were no problems. I installed opensuse, and had no problems. I then downloaded a clean copy of edgy's i386 ISO (the old one had significant install issues that I believe were related to setting it up in a dual boot system), installed it today, and...

No problems.

I winder if the problem for me wasn't an issue with the video driver (although the keyboard was locked out) or perhaps Beryl wasn't playing nice.

Anyway, much thanks for th good advice, and I'll probably be back when E17 starts doing strange things.

tjh

---

### Post by sarshet on 2007-01-11
I tried a clean install as well. It played nice for a couple of hours and then boom, again froze while browsing. For your information, I am running Edgy on an HP Pavilion 061, two video cards (Radeon RV250 If [Radeon 9000] and Radeon RV250 [Radeon 9000]). The network cards are RealTek RTL-8139/8139C/8139C+ and NetGear WG111 WiFi (v2). The WiFi card is connection to the Internet and the RealTek one is used for a separate LAN connection.

I have given up now. I am downloading Fedora to see if I have better luck with that one.

---

### Post by VoodooSteve on 2007-01-12
sarchet,

If you would like to stick with Ubuntu, try Dapper. I downgraded to that and the problem disappeared. Many of the bugs that exist on Edgy, including this one, are probably due to its shortened development from 6 months to 4 months. It lost time to the development of its predecessor which I find a lot more stable and bug free. Trying a clean Dapper install might be worthwhile since it only takes about half an hour.

---

### Post by mysticmarks on 2007-01-12
I've been reading everything I can about ubuntu freezing randomly. I haven't seen any responses that indicated a reason behind it. 
Amd Sempron +2000
ATI Radeon 9200
256 ddr
no dual boot, just ubuntu loaded.
I've noticed that it happens far more often browsing with firefox. It has done it from the initial install and updates. I now have the 9 beta 2 flash plugin. Both with and without, no difference. Without a recovery reboot i get a message about a temp file that doesnt exist. after recovery it ignores the error. i then enter root pass and reboot as the Ctrl-d continue option doesn't load up all utilities. The crash can be forced if you scroll very fast within synaptic pm, firefox, etc. Sometime the mouse stays responsive, sometimes not. ive tried to ctrl+alt+f1 to get terminal, no luck. Im wondering if it has something to do with ddr memory or being able to enable EEC. I cannot find any options to enable this within bios etc.

---

### Post by tjhanlon on 2007-01-15
Well, the freezes are back, but not as frequent as before. A friend suggested that the problem might be with the video drivers, but is that was the case, then why did edgy wait to freeze up again? I'm thinking that there might be some conflict with a process running in the background, but I can't find it. Nothing interesting in the system logs.

tjh

---

### Post by Megatog615 on 2007-01-16
I switched back to nv and it solved the problem. However, I'd like nvidia to work(for glx). I'll try it again after an apt-get dist-upgrade.
By the way, does anyone else have nForce2? This may be what's causing it, becuase I've heard nForce2 had problems with some hardware(my problem would occur on Windows too).

---

### Post by Boababa on 2007-01-21
I have the same problem.  The interesting thing is that the problem occurs in both Ubuntu Edgy and Windows (dual boot).  The crashes occur often, and, as far as I can tell, only when I try to scroll up/down a page while it is still loading.  I use Firefox 2.0.1 in Ubuntu, 1.5.0.9 in windows.  The only thing I've changed on my machine (dell 600m) just prior to crashes was my memory - i went from 512 megs of Dell's finest to a 1 gig Crucial stick.  This memory passes all tests.
I now try to wait for a page to fully load before scrolling around.  It's surprisingly hard to do.  :-)
-boababa

---

### Post by DrMega on 2007-01-21
I have Ubuntu Dapper (6.06 LTS) installed on both my machines at home. On one, I get fairly frequent freeze-ups when doing anything internet related. On the other, I get no trouble at all (touch wood, fingers crossed etc). Here's what I know:

---The machine that suffers with this issue---
AMD Duron 1.8GHz
512MB DDR2 memory
Radeon 7000 series gfx xcard (32MB AGP)
Ancient motherboard (which I'm sure has a bios problem)
Open source Radeon driver
Various browsers, of which FireFox is the most reliable.
Dual boot with Windoze XP Pro SP1
Ubuntu is on its very own ancient 10GB hard disk

---The machine that is OK---
AMD Sepron 3000+
1GB DDR2 memory
ASUS 9550 (based on ATI 9550 chipset) (128MB AGB)
ASUS K8V-MX motherboard
Propriety ATI driver (not sure which version)
Pinnacle 300i TV card (which I can't get working, but that's another issue)
FireFox 1.whatever
Dual boot with Windoze XP MCE SP2
Ubuntu is on a 100GB partition of a 300GB drive

Both machine access the internet via ethernet connection to a router (wired)

I have seen FireFox crash on the newer machine, but when it does, FireFox simply bombs out but I still have full control of the system.

On the older machine, I get some slight corruption of the the images of command buttons under Gnome, which points me towards a display driver issue. I tried KDE when I first installed Ubuntu, to assess which is the better desktop environment (I chose Gnome after much deliberation). What I found was that under KDE, when using FireFox, sometime KDE would restart the session, so same crash but at least it wasn't a full blown freeze-up.

After a crash, if I go back to the same web page, it will almost certainly crash again, leading me to suspect that it is something to do with the web page. Maybe something in a Flash or ActiveX object on the page? or maybe Ubuntu has an issue when it encounters a malform TCP packet?

Another clue steers me away from internet connections altogether. My newer PC is used as a media centre, connected to a TV (no monitor). I administer it from my older machine via remote login. I have had the freeze-up on my older machine while remotely logged into the newer machine. When this happens it is only the older machine that freezes, and the wife can continue to use the machine that was being remotely controlled at the time of the freeze.

Well, that's what I know. Sorry its an essay, but hopefully there's some good clues in there.

Oh and by the way, in case anyones wondering, the reason Ubuntu is on my media PC when I have a legit copy of Win XP MCE on there is quite simple. Windows crashed spontaneously on average twice per evening (sometimes much more). Like many Windows users, I was sceptical about Linux's multimedia capabilities but it got to the point under Windoze that it was either try another OS or kick the machine up and down the street in rage after it crashed for the nth time. I've never looked back since. Ubuntu is not "as good as" Windows, it is better by far. (and the wife agrees and she is a non-techy:)

---

### Post by CroEragon on 2007-01-21
I have freezing also, but since first install, with or without beryl and with or without ATI's drivers? I get complete hard freeze, but 95% of freezes it unfreezes itself after 5 to 15 minutes. I did lot of research and i narrowed down possible causes. It is probably conflict between x and my hardware. When it freeze nothing moves but if i type something while frozen it will be written after unfreezing. Same with mouse movement. Also may not be related, but i get "Cannot allocate resource 3 region of device...." right after choosing ubuntu in GRUB. I posted logs on forum, nothing in it.
Anyone have similar problem? Somebody suggested that it is old BIOS problem, but im unable to update and after reseting BIOS to default it messed up my GRUB, had to work 4 hours on it to get it back.

---

### Post by cactaur on 2007-01-21
I also get these freezes with Edgy. I've checked the /var/log/syslogs, and no consistent patterns are found there. I don't have any eye-candy installed, and these freezes are about as random as they come. Though they usually occur when I don't use the computer for a couple of minutes, but they're highly uncommon. Is there anything else I can do to help find the problem?

---

### Post by cactaur on 2007-01-21
Ok, I had another crash, and this was in my syslog:

```
Jan 21 14:29:41 localhost kernel: [17184117.756000] rix 255 (0) bad ratekbps 0 mode 6
Jan 21 14:29:41 localhost last message repeated 14 times
```

This message occurred right before I had to manually reboot. Hope it's some help.

---

### Post by mysticmarks on 2007-01-24
Well, after some researching on the forums, and alot of learning i resolved my random freezes. It definitely was a driver issue for me. I switched to the open source ati drivers and everythings great. I have beryl running with all the latest fixes and am very satisfied. im using the aiglx setup to run beryl and it is fine. The solve all was to get rid of the proprietary drivers and use the open source.

---

### Post by VoodooSteve on 2007-01-27
I am going to do a clean install of Kubuntu, Now, this problem occured to me when I was using Ubuntu 6.10, has anyone using Kubuntu 6.10 and Firefox had this problem?

---

### Post by DrMega on 2007-01-27
I read an article/bug report recently that the Radeon 7000 card is not well supported and can cause a freeze-up. I have a Radeon 7000 (with open source driver) on my machine that freezes. I have an ATI 9550 with propriety ATI drivers on another machine and all is fine.

In the machine that exhibits the problem, I've change the driver (in xorg.conf) from ATI to VESA and it seems to have fixed the problem, however now I get a monitor refresh rate that is torture on the eyes. The Radeon 7000 is an ageing, underpowered card anyway so I'm going to fork out about 30quid (about 55 dollars or 45 Euros) for a new 9550 and see what happens. Hey, if I can tell the wife I can't use my main machine until I get a new display card, saves me some ear ache.:)

---

### Post by deragon on 2007-02-08
Guys, I suffer from the same problem, but can reproduce it as will.  Check out [Bug #59857]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59857").

---

### Post by Orval on 2007-02-09
Same here. Since a day or 2 I get a complete freeze some 10 seconds after I launch Firefox. Swiftfox gives me the same problem, but I can surf the web using Konqueror.

I have an ATI 9200 using the open source drivers and I tried various options in xorg.conf, but the problem remains.

---

### Post by gracie on 2007-02-23
Has anyone solved this yet?  I am running kubuntu 6.10 and every time Firefox is used, the system freezes - allowing no action but to reboot with the Reset button.  Am using Konqueror now.

March 20, 2007  I've now discovered that the freezing problem disappears when the    .mozilla  directory in my home directory is deleted.  Something in it must have been corrupt.  I lose bookmarks of course and any personal settings, but at least Firefox is usable again!

---

### Post by zigx on 2007-03-01
hi guys unfortunately i dont think this is ATI specific... i have an nvidia card with the nvidia driver installed and it happens all the time. 

its basically one of the only things holding me back from making the switch to 100% linux.

i will see if i can find anything in my logs next time it happens.

---

### Post by zigx on 2007-03-01
> **deragon said:**
> Guys, I suffer from the same problem, but can reproduce it as will.  Check out [Bug #59857]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59857").

can anyone confirm this?  i have wireless as well...

deragon thanks alot for investing your time in tracking this sob of a bug.:KS

---

### Post by Orval on 2007-03-01
I just applied the new updates and now Firefox seems to be working OK again.

---

### Post by ububug on 2007-03-01
I had problems with Ubuntu 6.06 and 6.10 freezing and solved it by upgrading BIOS to the latest version. The thread about my problems is at [http://ubuntuforums.org/showthread.php?p=2230452](http://ubuntuforums.org/showthread.php?p=2230452)

---

### Post by zigx on 2007-03-01
> **Orval said:**
> I just applied the new updates and now Firefox seems to be working OK again.

i did the updates too and it JUST crashed my system.  will post output from logs.

---

### Post by zigx on 2007-03-01
well scratch that... my logs are empty for the crash... the timestamps are about 3 min after it crashed which means the data is from the restart. 

crap.



Here is some other data i can provide:


> zigx@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            11784  1 
rfcomm                 38936  0 
l2cap                  23300  5 rfcomm
bluetooth              48996  4 rfcomm,l2cap
speedstep_lib           4868  0 
cpufreq_userspace       4372  0 
cpufreq_stats           5892  0 
freq_table              4996  1 cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        6944  0 
cpufreq_conservative     7200  0 
video                  16644  0 
tc1100_wmi              7428  0 
sbs                    15776  0 
sony_acpi               5516  0 
pcc_acpi               13184  0 
i2c_ec                  5376  1 sbs
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
nls_utf8                2304  2 
ntfs                  108148  2 
fuse                   41864  0 
lp                     11972  0 
ipv6                  257632  8 
af_packet              21768  4 
wlan_wep                7168  2 
bt878                  11560  0 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
wlan_scan_sta          14208  1 
ath_pci                97312  0 
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
tuner                  53804  0 
bttv                  172532  1 bt878
video_buf              26372  1 bttv
ir_common              27652  1 bttv
compat_ioctl32          1536  1 bttv
i2c_algo_bit            9480  1 bttv
ath_rate_sample        15616  1 ath_pci
e1000                 126532  0 
v4l2_common            16384  2 tuner,bttv
btcx_risc               5384  1 bttv
tveeprom               15248  1 bttv
videodev                9728  1 bttv
nvidia               6827412  32 
i2c_core               22288  6 i2c_ec,tuner,bttv,i2c_algo_bit,tveeprom,nvidia
tsdev                   8256  0 
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
wlan                  205148  5 wlan_wep,wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               192080  3 ath_pci,ath_rate_sample
hw_random               6168  0 
intel_agp              25116  1 
agpgart                33456  2 nvidia,intel_agp
snd                    55428  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
evdev                  10496  1 
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
serio_raw               7300  0 
psmouse                40072  0 
pcspkr                  3072  0 
floppy                 60676  0 
rtc                    12596  0 
ext3                  138632  2 
jbd                    55700  1 ext3
ehci_hcd               32520  0 
uhci_hcd               23176  0 
usbcore               130304  3 ehci_hcd,uhci_hcd
ide_generic             1536  0 
ata_piix               10884  0 
libata                 73228  1 ata_piix
scsi_mod              141320  1 libata
ide_disk               17664  7 
piix                   10628  1 
generic                 5252  0 
thermal                14600  0 
processor              26028  1 thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability



> zigx@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)


---

### Post by zigx on 2007-03-01
also it might be important to note that last night's upgrades installed new versions of the following packages:
> 
firefox-gnome-support - 2.0.0.2+0dfsg-0ubuntu.0.6.10
firefox - 2.0.0.2+0dfsg-0ubuntu.0.6.10
when those packages installed i thought i saw a note about memory corruption and was assuming that fixed this said bug in this thread but it either was Not... or it didnt fix it.

im gonna try to turn on firefox-dbg symbols but i have no idea what im doing lol so if california blows up, i apologize.

---

### Post by tallinn on 2007-03-02
Same here, I did not have many problems before 6.10.  Now my system freezes dayli...
Any solutions?

---

### Post by scottness on 2007-03-02
I've had a similar problem with an Nvidia Geforce Go 7300.  I run into problems only when Beryl is running and I'm on my wireless connections.  The problems simply don't happen when either Beryl is off or I'm connecting by ethernet cord.  My wireless card is the Broadcom 1390 that has to use ndiswrapper to work.  I would really like these two to play together, but it isn't looking good.

Today, I reinstalled both the Nvidia driver and the wireless driver, but I had no change.  When I crash, I'm getting these messages in the log:
> sbevill-laptop gconfd (root-501: Resolved address "xml:readonly; /var/lib/gconf/defaults" to a read-only configuration source at position 4
sbevill-laptop gconfd (root-501: GConf server is not in use, shutting down.
sbevill-laptop gconfd (root-501: Exiting
sbevill-laptop kernel: [17180433.560000] <c01499a4> __report_bad_irq+0x24/0x80 <0149a9d>note_interrupt+0x9d/0x270
sbevill-laptop kernel: [17180433.560000] <f9595415>nv_kern_isr+0x2f/0x62[nvidia] <c0149323>handle_IRQ_event+0x33/0x60
sbevill-laptop kernel: [17180433.560000] <c0149448>__do_IRQ+0xf8/0x110 <c0105c89>do_IRQ_0x19/0x30
sbevill-laptop kernel: [17180433.560000] <c010408a> common_interrupt+0x1a/0x20 <f88586dd>acpi_processor_idle+0x220/0x3af[processor]
sbevill-laptop kernel: [17180433.560000] <c02d902a> schedule+0x48a/0xcc0 <c0102122>cpu_idle+0x42/0xb0
sbevill-laptop kernel: [17180433.560000] <c03f27a1> start_kernel+0x321/0x3a0 <c03f2210>unknown_bootoption+0x0/0x270
sbevill-laptop syslogd 1.4.1#18ubuntu6: restart.

I'm going to try the non-proprietary Nvidia drivers and see if the problem persists.  Otherwise, I guess I'll have to do without my eye-candy...unless there is another solution. :(

---

### Post by zigx on 2007-03-03
> **scottness said:**
> I've had a similar problem with an Nvidia Geforce Go 7300.  I run into problems only when Beryl is running and I'm on my wireless connections.  The problems simply don't happen when either Beryl is off or I'm connecting by ethernet cord.  My wireless card is the Broadcom 1390 that has to use ndiswrapper to work.  I would really like these two to play together, but it isn't looking good.

Today, I reinstalled both the Nvidia driver and the wireless driver, but I had no change.  When I crash, I'm getting these messages in the log:


I'm going to try the non-proprietary Nvidia drivers and see if the problem persists.  Otherwise, I guess I'll have to do without my eye-candy...unless there is another solution. :(

how did it go?

---

### Post by scottness on 2007-03-03
Haven't had time to try yet... Looking at the Nouveau site, it seems like it'll take some compiling (if its even usable yet...which I doubt it is), and I'm not real comfortable with that yet either.  I should have some time to play with it tomorrow afternoon.  I'll post here after I'm done.

That said, I've re-installed my wireless card drivers and my Nvidia drivers using the Envy script and the problem still occurs only when using both my wireless connection and Beryl.

---

### Post by Megatog615 on 2007-03-03
I have resolved the problem on my computer by uninstalling the nvidia driver from the repos and installing Envy. if you run a search on this forum you can find Envy. It is a software package that allows you to install the latest stable driver directly from NVIDIA's website.

I think the problem might be related to the VIA chipset in my computer. Does anyone else here have a VIA chipset from 1999-2001? In my case, it is *not* related to Firefox. It would freeze within 5 seconds every time a GTK application was launched.

---

### Post by zigx on 2007-03-04
> **Megatog615 said:**
> I have resolved the problem on my computer by uninstalling the nvidia driver from the repos and installing Envy. if you run a search on this forum you can find Envy. It is a software package that allows you to install the latest stable driver directly from NVIDIA's website.

I think the problem might be related to the VIA chipset in my computer. Does anyone else here have a VIA chipset from 1999-2001? In my case, it is *not* related to Firefox. It would freeze within 5 seconds every time a GTK application was launched.

i have envy installed... 

i want to try your fix, how do i remove the nvidia drivers that were installed by the repos?

---

### Post by zigx on 2007-03-04
for those who are getting the lockup while firefox is open problem, i have been using opera for now and its not crashing or anything... although i wish i were using firefox :)

---

### Post by FuturePilot on 2007-03-04
I'm using Firefox 2.0.0.2 on Dapper without issues. I'm also using Edgy on my laptop and I don't have any problems. Although I don't really use my laptop for browsing the internet, I've used it a little and haven't noticed anything with it yet.

---

### Post by Megatog615 on 2007-03-04
> **zigx said:**
> i have envy installed... 

i want to try your fix, how do i remove the nvidia drivers that were installed by the repos?
If you install Envy, it should remove the nvidia-glx package for you. If you still have the problem, then my original problem is completely unrelated to this thread.

---

### Post by airjrdn on 2007-03-04
I've tried 6.10 and 7.04, am running an ATI 9700 Pro (with whatever drivers install by default) and a wired connection (Intel chipset, not VIA - FYI to a prior post) and I get lockups when using Firefox as well.

---

### Post by robbr on 2007-03-05
At the risk of adding a pointless "me too" post I must also count myself among those that have had frequent random freezes.  It only appears to be when I'm running Firefox on Edgy.  I let Banshee 0.11.5 run for about 24 hours playing my music collection and had no issues at all.  Fire up (no pun intended) Firefox 2.0.0.2+0dfsg-0ubuntu0.6.10, surf for a while and at $some_random_interval later, total lock up.  Can't toggle num lock or caps lock.  I installed Epiphany just to test the Firefox-is-culprit theory and I'm about 1 hour 34 mins into the lets-see-if-this-causes-a-lockup test.

---

### Post by WATERWALLY on 2007-03-05
SOLVED:

I was having the same problem.

it was an IPV6 fault, turn it off and every thing is ok .

see theis site : [http://kb.mozillazine.org/Error_loading_any_website](http://kb.mozillazine.org/Error_loading_any_website)

ken:) :)

---

### Post by airjrdn on 2007-03-05
That link points to symptoms of sites not rendering, not entire system lockups.  There was another thread where users suggested IPV6 was the problem, and initially the user thought it had fixed the problem, but later reported it hadn't.

---

### Post by scottness on 2007-03-05
I seem to have found the solution to my problem...it was kernel related.  In the default Ubuntu kernel, the Nvidia driver and my wireless driver (using Ndiswrapper for a Broadcom 4311 card) were using the same IRQ, causing the system to crash.  Apparently that problem is fixed in later versions of the kernel.  Use at least 2.6.20 kernel and you should be able to use the wireless driver and the nvidia driver at the same time.  I was able to fix it by upgrading to the latest Fiesty Herd yesterday and have had no problems since then.  Here is a [bug report]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57355") and a thread from the [Nvidia forums]("http://www.nvnews.net/vbulletin/showthread.php?t=48327") that may help.  

This fixed my problem, but may not be appropriate for yours...but if you're having the conflict between your ndiswrapper and Nvidia drivers...and getting messages in your syslog like the one I posted earlier, this may be helpful.

---

### Post by zigx on 2007-03-07
how can i check my IRQs?

---

### Post by robbr on 2007-03-07
Well, I never did have another hard lockup when using a browser *other* than Firefox but was really not satisfied with that solution so dug a bit further and I think I've solved my particular issue.

It appears that Firefox for some reason doesn't play nicely with the default nvidia RIVA TNT2 driver for my video card.  After following the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=376481") I updated my driver, modified /etc/X11/xorg.conf, restarted X, have had no further problems.

I'm a happy bunny tonight ;-)

---

### Post by gldvxx on 2007-03-11
*my* random firefox freeze is as follows.. i can use the keyboard but not the mouse!  i have a solidtek usb mini-input keyboard with a built in touchpad.  i think my situation maybe more related to my hardware, but thought i'd add my scenario to the list just in case!  the freezing i experience is more like it's hanging, i can only move it sideways but it's very unresponsive.  

this freeze has happened to me twice today.  i just installed amarok and i was downloading songs from my [http://www.epitonic.com](http://www.epitonic.com) playlist (epitonic has a flash player customized for your account).  the "hang" occurred when i was using my trackpad's scroll feature in firefox.  the same situation JUST happened again when i was in firefox, scrolling.. and when i restarted i saw that the epitonic site had been open on another side of my cube (i'm running beryl so that's another factor to consider).

both times i was able to ctl-alt-f2 and restart gnome.  when i see the gnome login screen my mouse is still unresponsive.  i'm able to log in, and during that process, my mouse becomes active again.

next time it happens i'm going to try just unplugging and replugging it in (it's usb).

EDIT: oh yah, p4 3.4 GHz and nvidia 7300

---

### Post by zigx on 2007-03-13
there are lots of nvidia reports (me included).

If anyone has tips on how i can specifically debug my nvidia setup id  really appreciate it.

---

### Post by soul814 on 2007-03-15
ubuntu edgy
notebook: l2000
video card: ati 200m
ram: 1.5gbs
wireless: broadcomm 4318

------
Same problem as everyone, except my culprit isn't only firefox. I think it has to do with the fact my notebook has shared video and system ram. I freeze a lot quicker when I have beryl activated. When I don't I can freeze either by browsing the web in Firefox or multitasking when I'm doing an update. I also freeze when I'm copying over 2000 files (roughly 400mbs from one partition to another). Freezing as in everything locks up and I can't press ALT CTRL F1, CTRL ALT BACKSPACE, etc. Sometimes, either my mouse or my keyboard locks up first and then the rest.

-----

Windows XP -> I get random crashes and BSODs, so it's probably my hardware. Yet, I've run memtest for 5 hrs, 0 problems. prime95, 3 hrs right after the memtest and no problems. How strange =]

---

### Post by chartman on 2007-03-17
> **dnite said:**
> I used to have a problem like this with Ubuntu Edgy. Let me ask a couple questions...

1. When the system freezes, are you still able to move the mouse around, just not able to click anything and the keyboard is unresponsive as well?

2. Are you running compiz/beryl 'eye candy' ?

If you answered yes to both of those questions, turn off the eye candy and you shouldn't have any more random crashes. I've been random crash free since I stopped using compiz/beryl.

This is EXACTLY the behavior I see! But I don't understand what you mean by "eye candy"? Is this one of the options ins the beryl manager?

---

### Post by alexboia_ro on 2007-03-18
Hello, I am new to everything different from windows, but recently i decided to try out Ubuntu, as it seemed a good alternative.

I have an ancient AMD Duron 1300 MHz, 512 Mb RAM and a Nvidia G4 Mx440 video card.

I have the nvidia drivers installed.

I installed dapper and soon afterwards upgraded to edgy and I first had no problems. But after i replaced my mouse with anotherone (on USB), edgy started to freeze after running about 20 minutes. I could move the mouse and XMMS was also playing. I look in Xorg.0.log and i saw X was complaining about not beeing able to load WACOM driver from /dev/wacom for the input devices stylus, eraser and cursor. 

I don't have any idea about what these three devices are/do, but i presumed they are related to the mouse; so i went to /etc/X11/xorg.conf and after studying /dev/input i changed the "Device" option for each of these three devices with /dev/input/event1. I also changed the "Device" option for my mouse with /dev/input/mouse0. 
After that, I restarted X, and i couldn't see anymore errors (EE) in Xorg.0.log and edgy stopped freezing, at least for now. My computer has been running for the apst 12 hours and no freeze, yet.

So, I am asssuming that if there is an incopatibility between X's xorg.conf and the hardware, than it's very likely edgy will freeze. 

PS: What bothers my is that, altough, the mouse seemed to be the problem, i could move the cursor after my computer froze...
PPS: I run FF 2.0.0.2 before and after the crashes...

---

### Post by phido on 2007-03-18
> **chartman said:**
> This is EXACTLY the behavior I see! But I don't understand what you mean by "eye candy"? Is this one of the options ins the beryl manager?

Beryl/Compiz is the eye candy

---

### Post by macnod on 2007-03-27
> **Boababa said:**
> I have the same problem.  The interesting thing is that the problem occurs in both Ubuntu Edgy and Windows (dual boot).  The crashes occur often, and, as far as I can tell, only when I try to scroll up/down a page while it is still loading.  I use Firefox 2.0.1 in Ubuntu, 1.5.0.9 in windows.  The only thing I've changed on my machine (dell 600m) just prior to crashes was my memory - i went from 512 megs of Dell's finest to a 1 gig Crucial stick.  This memory passes all tests.
I now try to wait for a page to fully load before scrolling around.  It's surprisingly hard to do.  :-)
-boababa

I have the problem on a Dell Inspiron 8500. I think you're right about the scrolling business. And if I don't browse the WWW, I don't see the problem. So if I'm SSHing to another host or if I'm using Emacs to write Lisp code for factoring integers, I can go for as long as I need to without a freeze.

---

### Post by rplantz on 2007-03-27
I was having random freezes running feisty. It kept getting worse, so I booted into my Debian installation. Same thing. That's when I opened the case to see if something came loose, etc. And that's when I saw that the CPU heat sink fins were completely encased in dust. See my post here:

[http://www.ubuntuforums.org/showthread.php?p=2351274#post2351274](http://www.ubuntuforums.org/showthread.php?p=2351274#post2351274)

I admit that I've been getting feisty updates regularly, so this may be coincidence. But my system has been fine for three days now.

---

### Post by feight on 2007-04-08
Been a long time since I last posted on these boards. Went away from Ubuntu for a while, partially because of rt61 issues (still an issue for me in Fiesty). I've come back recently and decided to try out Fiesty because the feature changes were too hard to pass up.

I can say this honestly; once Fiesty is complete and most the bugs have been fixed it will be tough competition for Windows. The usual install chores required after an Ubuntu install to get media working has been cut to an absolute minimum. I had all the basic stuff running minutes after install and without typing a single word in a prompt.

Okay, enough kissy-face...

I seem to freeze - randomly but frequently - within a few minutes of loading up Fiesty. This occurred before installing anything beyond the base DVD install. Before and after installing the Nvidia binary driver and with or without even logging into to system (that's right, if I sit long enough sometimes the login screen does it).

Unlike many of the others my mouse does work, I cannot tell if my keyboard is working because the GUI does not respond whatsoever.

Any suggestions or information that might be useful to anyone in fixing this issue for me?

---

### Post by moueza on 2007-11-03
same problem underfeisty, suse10.3, but no problem under FC7

---

### Post by moueza on 2008-04-27
Solution: use Xen

---

