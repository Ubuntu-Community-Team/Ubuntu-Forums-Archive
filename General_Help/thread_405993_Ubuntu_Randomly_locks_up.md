---
title: "Ubuntu Randomly locks up"
date: 2007-04-10
forum: General Help
---

### Post by allforcarrie on 2007-04-10
My Ubuntu locks up at least once a day. I don't even have to be touching my computer for it to lock up. Example :  Today i was playing  xbox 360  and listening to some mp3's and Ubuntu locked up and needed a hard reboot.

any help is much appreciated.

---

### Post by Toadmund on 2007-04-10
Do you get the ' White screen of death', or do you get the vertical bars?
I get the WSOD once or twice a day, vertical bars twice in approx. 3 weeks.

I'd file a bug report but I'm lazy, or I assume feisty is still bugged down a tiny bit?

It's almost like my OS falls into a hole, I click to a new page and 'POOF' it diappears and turns white?
I have to do a hard reset.

This scares me because one day I was updating when I got vertical Ubuntu brown bars obscuring my screen, I had to hard reset and it forced me to do a fresh OS install, it frigged things up that bad, nobody could help me.
Linux is not supposed to crash, but it crashes on me everyday :confused: 
(that's just my luck.)

---

### Post by allforcarrie on 2007-04-10
nothing shows up at all, it just locks like my mouse and keyboard are unplugged. If i have music playing it keeps skipping like a scratched Record.

---

### Post by allforcarrie on 2007-04-10
[http://ubuntuforums.org/showthread.php?p=2431589#post2431589](http://ubuntuforums.org/showthread.php?p=2431589#post2431589)  Similar problem.

---

### Post by allforcarrie on 2007-04-10
it looks like alot of people are having the same problem i'm going to try installing swiftfox and ditching firefox.

---

### Post by FuturePilot on 2007-04-10
Are you using the Nvidia driver by any chance?

---

### Post by allforcarrie on 2007-04-11
nope, i have an ATI 9800pro with default ubuntu drivers.

---

### Post by pirothezero on 2007-04-14
I get the same thing. Nvidia 9755, abit ic7-g, I've been thinking it was hardware related and switched hard drives and ram and got it once after doing that. 

Not sure wtf.

---

### Post by yoasif on 2007-04-21
I have experienced  the same types of issues.

I'm using an nforce 410 board (Biostar Geforce 6100-m9), and have experienced the problems in both edgy and feisty, with vesa drivers, and nv, and the closed source nvidia drivers. 

I don't think it's overheating; my motherboard has a processor stepping feature, and it has happened at reduced processor speeds (and my machine is well ventilated).

For now, I am installing Windows :( but I will dual boot between the two to help diagnose this issue if there is any information that I can provide to help. 

I also tried it with SuSE 10.2, with the same results. However, and I am not 100% on this obviously, but the problem never seems to crop up in failsafe (single user mode). Obviously, this is a suboptimal solution, as I run things (squid, samba) that are not auto started in failsafe. 

Oh, and the screen goes all wonky (a pattern of the screen at crash, repeated multiple times across the screen, with white lines and a skew). 

If there is any information I can provide, or any tips anyone might have, I'd love to help out and write a bug report for it.

This occurring in SuSE makes me think it's some sort of kernel issue, and I'm surprised more people aren't experiencing it.

---

### Post by allforcarrie on 2007-04-22
still happening but swiftfox helped a little bit.

---

### Post by dawv on 2007-04-22
mine lockes up so often i cant even install it! you are a lucky fela

---

### Post by allforcarrie on 2007-04-23
i tryed editing xorg.conf yesterday and setting the default depth bow i get no x when i log in.

---

### Post by yoasif on 2007-04-23
> **allforcarrie said:**
> still happening but swiftfox helped a little bit.I turned off processor stepping in my BIOS (cool n' quiet is how my mobo refers to it), and all of my problems seem to have disappeared. I've had it running for about two days now.

Maybe there's some bug in the default processor stepping utility in Ubuntu?

Give it  a try, hopefully we can get enough info for a bug report. :)

---

### Post by allforcarrie on 2007-04-23
i'll give it a shot. turning the default depth to 16 crashed X and i had to edit xorg.conf from command linbe.

---

### Post by Journeyman on 2007-04-23
I had an issue with lock ups and realised it happened when it was idle for some time, and it turned out to be a power management issue in the bios, I disabled the suspend mode and all the other power management stuff and that fixed the problem

---

### Post by benner on 2007-04-23
mine locks up even when i'm using it so it isn't a suspend with me.  i installed the beta of feisty as soon as it came out and i think the freezes may have started after a kernel update.  i have an amd4200+ with ati x550 using fglrx.  no heat problems.  the machine is brand new and cool as a cucumber.

---

### Post by yoasif on 2007-04-24
> **benner said:**
> mine locks up even when i'm using it so it isn't a suspend with me.  i installed the beta of feisty as soon as it came out and i think the freezes may have started after a kernel update.  i have an amd4200+ with ati x550 using fglrx.  no heat problems.  the machine is brand new and cool as a cucumber.My machine never suspends either, I'm referring to processor stepping, which many newer motherboards have. It is known as [Cool'n'Quiet]("http://en.wikipedia.org/wiki/Cool'n'Quiet") for AMD, and [SpeedStep]("http://en.wikipedia.org/wiki/SpeedStep") for intel.

---

### Post by AndrewNi on 2007-04-24
I'm getting hard locks as well in 6.10, sounding a lot like what's been mentioned.

It's been working fine for months, but yesterday before I turned it off I got the kernel updates from a week or two ago so I believe it might have something to do with it.

I would see what was in the log but KSystemLog now doesn't load, and just shows windows that don't respond or repaint.

:confused:

---

### Post by connellr on 2007-04-24
Yoasif:  You're not alone, I have a similar setup and am experiencing the exact same problem.  Every time I have had the problem I have been using the computer ... I experiance the problem more frequently if I have Beryl or Compiz running, but even when I dont have any desktop effects enabled I experiance the problem.  I am running the NVidia Restricted Driver ... I did not notice problems before enabling that driver ... but running without nvidia drivers is just not an option here.  When the computer locks up the screen is mostly white with lines randomly displayed across the screen.

Hardware Profile:
Biostar Geforce 6100-m9 Motherboard
AMD Athlon 64 3400+ Venice
1GB PC3200 Memory

I have not checked into the Processor Stepping settings of the Bios yet, I will take a look at that, but I really think there is a software issue that needs addressed.  My hardware is running cool.  Its completely new equipment (so no dust problems).

> **yoasif said:**
> I have experienced  the same types of issues.

I'm using an nforce 410 board (Biostar Geforce 6100-m9), and have experienced the problems in both edgy and feisty, with vesa drivers, and nv, and the closed source nvidia drivers. 

I don't think it's overheating; my motherboard has a processor stepping feature, and it has happened at reduced processor speeds (and my machine is well ventilated).

For now, I am installing Windows :( but I will dual boot between the two to help diagnose this issue if there is any information that I can provide to help. 

I also tried it with SuSE 10.2, with the same results. However, and I am not 100% on this obviously, but the problem never seems to crop up in failsafe (single user mode). Obviously, this is a suboptimal solution, as I run things (squid, samba) that are not auto started in failsafe. 

Oh, and the screen goes all wonky (a pattern of the screen at crash, repeated multiple times across the screen, with white lines and a skew). 

If there is any information I can provide, or any tips anyone might have, I'd love to help out and write a bug report for it.

This occurring in SuSE makes me think it's some sort of kernel issue, and I'm surprised more people aren't experiencing it.

---

### Post by connellr on 2007-04-24
I have created a bug report that I believe applies to this problem.  You can view it and add any comments of your own here:
[https://bugs.launchpad.net/ubuntu/+bug/109643](https://bugs.launchpad.net/ubuntu/+bug/109643)

---

### Post by allforcarrie on 2007-04-24
i am using the ATI restricted driver on a 8900 pro so maybe its both drivers.

---

### Post by allforcarrie on 2007-04-24
[http://www.extrememhz.com/drag_CK8-p1.shtml](http://www.extrememhz.com/drag_CK8-p1.shtml) here is my board if anyone has suggestions.

---

### Post by yoasif on 2007-04-24
> **connellr said:**
> I have not checked into the Processor Stepping settings of the Bios yet, I will take a look at that, but I really think there is a software issue that needs addressed.  My hardware is running cool.  Its completely new equipment (so no dust problems).We have the same processor, and I also have 1GB of RAM.

Please try turning off the processor stepping feature, since I think that is what is causing our problems. From what I have experienced, I don't think it's the closed source nvidia drivers, since I am also using them currently, and it's working perfectly fine (not a single crash since I turned off stepping).

I also believe this is a kernel issue, since I was running the feisty beta for quite a while with no issues, and I don't think it was a power management util update that started causing the problems -- actually, it was an update to the nvidia-new drivers that forced me to update the kernel as well, when things started to get weird.

I believe this warrants a kernel regression if this is the cause of the problem (which I am now thinking is correct, since the problem occurs even with nv and vesa). 

The only thing I can think of now is how I can downgrade my kernel to find the regression -- if there are any posts on how to do this, I would be extremely willing to help track down this issue. 

So again, please try turning off cool'n'quiet. :)

I have submitted a related bug report at: [https://bugs.launchpad.net/ubuntu/+bug/109810](https://bugs.launchpad.net/ubuntu/+bug/109810)

Hopefully one of the assumptions are correct.

---

### Post by dagrump on 2007-04-24
I would like to chime in on this, my primary machine has, or had an issue of locking up ever since I upgraded my chip from an e6300 to an e6600. It seems to lock reloading pages in firefox, or if FF was open and i was doing something else w/FF open. I've tried several things to remedy this issue.  I replaced my cpu fan & thermal paste on sunday & reinstalled edgy, so far I have not had a lock up since. the cpu cooler was stock intel, which used plastic tabs to hold it in place I don't believe they truly kept the mating surfaces in contact & would allow the processor to overheat. I have not had the time test w/ more demanding loads, but I was having this issue with only firefox running.
My fingers are crossed, that this issue is over for this machine, &  I will try to reinstall feisty 
(removed for locking up every time I looked at it cross-eyed). My testbox has run feisty since herd 1 with very few issues, but my primary machine was a total joke. I have seen this issue blamed on everything from firefox to the core 2 duo processor to nvidia drivers. I'm not the sharpest knife in the drawer, but this seems to be a fairly common issue, & I'm sure some one has a better handle on this than I, but until this old pig starts locking up again, I had a hardware issue.

---

### Post by johanPO on 2007-04-25
I am having a similar issue. Firefox freezes my PC completely at some random point. It is alway when I try to click on link. Yesterday it was running fine for several hours and then all off a sudden dead. After a reset there is no information in /var/log/messages that could help. The link is also working, so it does not seem like a firefox only issue.

I have had 6.10 running several months and was rock solid once I turned off the DHCP. This weekend I did an upgrade to Feisty. Except for the usual trouble with the ATI drivers. It never works for me out of the box and I have to download the drivers from ATI and recompile the kernel. I am not using any Desktop effects. I did experiment with beryl, but it was too slow, and unstable so I decided to leave it until it for the time being.

---

### Post by Invius on 2007-04-25
*sigh* this is very disappointing, I too lock up, randomly, I have installed 7.04 release 3 times and still lock up, I saw the vista versus beryl video and was so excited, I even laughed at how they all ended with a blue screen and bill gates say 'uh oh'. yet I have not had a single crash, lockup, blue screen, or even annoyance since I have reinstalled XP,

My only complaint is that windows  doesnt make good use of resources like linux does so that I can have pretty desktop effects like beryl. I really wanted feisty to be my primary OS, I stayed up a total of 50 hours waiting for the fiesty release expecting it to be more stable than anything microsoft could hope to release and was really let down, has linux become so picky about hardware that it just will not run?

I don't know what to blame here, is it my ati radeon x300? the xgl server? the restricted ati drivers? the fact that it's pci express? is it the sound? my soundblaster live 5.1 didnt pump out sound out of all 4 of my speakers back in the slackware 6 days but it played fine out of the front ones. maybe the chipset? intel 82801GB I believe. maybe its the mainboard? I would accept that possibility in a minute, it's a crappy prebuilt, thats all I could afford, a dell dimension 5150, why crappy? wheres the ps/2 ports that would allow me to install opensuse?

I don't mean to bash or anything, but I see 'it just works' all over the place, it just didn't work untill I deleted ubuntu, uninstalled the crappy oem copy of xp home dell gave me (I swear I will never trust another OEM cd again after the hell that thing put me through.), and installed a pirated copy of xp pro (which never ever gave me trouble, go Windows Pirate Advantage.)

If you would like more intimate knowledge about my computer to attempt to solve my lockups, I will gladly risk my partition table a 3rd time to resize and make room for ubuntu (I have risked it twice resizing and then merging it) and try out some tweaks, but I would just like to say one thing before we go down that path.

I already have a plain boring desktop, and if I want to have something fancier, I can for the hell of a snail's pace install vista again, and have little more than what emerald is capable of, I only mention this because my lockups started after enabling 'desktop effects' which I assume to be compiz with its configuration stripped down to two options, and later, beryl. (yes it locked up with the default installation) and I am not willing to blame the restricted drivers, because unless they were installed automatically (I dont see how as sabayon formatted the partition for its install, so nothing from ubuntu was left over) I had even more frequent lockups after the fresh install.

---

### Post by allforcarrie on 2007-04-25
windows XP runs perfect so i am assuming its a software issue rather than a hardware issue like over heating.

---

### Post by Invius on 2007-04-25
> **allforcarrie said:**
> windows XP runs perfect so i am assuming its a software issue rather than a hardware issue like over heating.

Modern machines reboot when they overheat, my old computer did it when the cpu was overheating (the fan was running fine, I don't know why it was overheating, it caused me to get this machine), also, my webhosts machine runs freebsd, it had a cpu fan failure, it was restarting every 10 minutes for a week  before he finally noticed it, I watched my eggdrop die and come back over and over, and the messages showed unclean dismounts.

It has to be video related, why else would it be rock solid or atleast, more stable than running with compiz or beryl enabled? I am not sure how many people on this thread have either enabled, but if they do, I am sure they will find they are having to power their machine down alot less, or not at all if they disable them, or even run xorg without xgl/aiglx

---

### Post by Arcadian on 2007-04-26
> **yoasif said:**
> I have experienced  the same types of issues.

This occurring in SuSE makes me think it's some sort of kernel issue, and I'm surprised more people aren't experiencing it.

Hi All,

I've had exactly the same issue. Still am under Ubuntu. Was working slightly better in the Feisty Fawn release candidate I have to say.

Please see my post here [http://forums.suselinuxsupport.de/index.php?showtopic=38326&st=20#]("http://forums.suselinuxsupport.de/index.php?showtopic=38326&st=20#")

I'm using an NVidia GeForce4 MX420. Under SUSE (and KDE at the time) I found that when I was running FireFox or Thunderbird, things could suddenly lock solid. To Gnome's credit, when I ran that desktop it would freeze for about a second & then resume.

Switching back to the default NV driver, everything would work sweet, just a bit slower. After a bit of trouble shooting, I found that making my Nvidia card AGP 2x rather than AGP 4x things were solid.

I now have this issue under Ubuntu/Gnome, it freezes for about a second & then continues. Sometimes my networking is dropped (wireless) and I have to ifdown/ifup to get it running again. Really frustrating...!

I'm going to try the AGP 2x thing again to see if it helps any. Kind of annoying, because it perfectly fine right now (locked up once tonight), but I know it's going to happen again! Something in the back of my brain mentions NVAGP & AGPVART. Also, I expected to find a setting in "nvidia-settings" tool to change the AGP rate but didn't. Weird eh...

I agree, I think this is an AGP/Kernel issue. It's across distros, and happens with all versions of the drivers I've tried. As I said, the Feisty Fawn RC worked pretty damn good. I have real troubles when kernel upgrades come out, but I'm hanging out for the next one. It just may fix this, and my suspend problem!

Cheers,
Arcadian.

---

### Post by johanPO on 2007-04-26
The connection with the network is interesting. I used to have issues with that [http://ubuntuforums.org/showthread.php?t=302768](http://ubuntuforums.org/showthread.php?t=302768). Once I disabled DHCP, and gave my PC a fixed IP address, i had no problems anymore. Y
yesterday I did the same (deactivated DHCP) and tried to stress my machine by running azeurus, playing a DVD and surfing then net and I had no issues for my complete session. I will try to investigate this a bit more tonight.

Yesterday I had another day without lock ups. For me the solution seems to be to disable DHCP and go for a static IP address.

---

### Post by Arcadian on 2007-04-26
> **johanPO said:**
> The connection with the network is interesting. I used to have issues with that [http://ubuntuforums.org/showthread.php?t=302768](http://ubuntuforums.org/showthread.php?t=302768). Once I disabled DHCP, and gave my PC a fixed IP adress, i had no problems anymore.

Interesting... cheers johanPO, will give that a go tomorrow & let you know how I get on. There's a common thread here somewhere...(kernel? module?)

Cheers!
:)

---

### Post by jonom on 2007-04-26
I've been getting random lockups too. Ubuntu just stops. The mouse still works. 

It happened today as I was watching a video in firefox and everything stopped except for the audio. My system had only been on about 15 minutes. Other times it can be hours or days.

I've noticed a few people mentioned they were running firefox - could that be a correlation? I'm starting to keep track of what's running when it happens. I've had desktop effects running too, I've turned them off to see if anything happens.

My system:
amd64x2 3800+ (I just upgraded the cpu from an amd64 3000+ a few days ago, but it happened on that cpu as well.)
asus a8n-e mainboard
nforce4 ultra chipset
gt6600 ultra pcie video
audigy 2 value sound
2gig ddr3 ram

---

### Post by allforcarrie on 2007-04-26
is anyone else running Ubuntu or are you running Kubuntu or xubuntu?

---

### Post by KrazyPenguin on 2007-04-26
According to my post here:
[http://ubuntuforums.org/showthread.php?t=422957](http://ubuntuforums.org/showthread.php?t=422957)

The problem is with the internet/cpu frequency, at least with my intel.

The solution is to upgrade the kernel.

It took me 6 hours to crash my computer today, and that is after enabling compiz. (an hour later)

But the best solution for me so far was adding 'pci=assign-busses' to the kernel at boot.

And when my computer just froze about 10 minutes ago, when I logged back in my Network Connection icon was missing on my laptop. 
I clicked on a Firefox link just before this.  Also missing was my Power Managerment icon as well as skype and i think volume.
Clicking on the red Shutdown button didn't do anything.
So I went to a terminal and did 'sudo reboot' but when my computer rebooted again those icons were still missing, and I couldn't connect to the internet.
So I clicked on the "red shutdown button' again, and suddenly the power management button appeared, then a second later network manager appeared,
and then skype.

Wow.

So now I will try to compile the latest kernel which is suppose to have the patches for this bug, and then try to crash it again.

;-)

---

### Post by dagrump on 2007-04-26
I thought my issue was hardware, but NO, this box turns into a brick while loading pages in firefox or trying to use virtualbox, & I'd bet anything else. I reinstalled edgy (gnome) seemed fine till I installed virtualbox, then the lockups returned. I'm going to remove v.box & it's dependences, but i doubt that it will make much difference.
This is my hardware maybe there is a common thread some one will notice.
Abit AB9, intel E6600 core 2 duo, 2 gig ddr2 ram, sb audigy Z ?, geforce 7950 gtoc, & linksys wireless card,  (2) 74 gig raptors, (2) 250 gig sata 3.0 drives, lightscribe dual layer dvd burner, & a dvd rom drive.
This freeze issue seems to have gotten worse since i upgraded the processor, thats why I thought was heat issue. I totally stumped here so I hope something gets figured out, its not much good having hardware to run most things I would want to run, if something as simple as firefox turns it into an oversized ugly paperweight.
Getting a little ticked off at this point.

---

### Post by Jasonmrc on 2007-04-26
My comp has been having these 'lockups' or 'freezes' since I last updated. (Which was a week ago I think) Its very annoying because it will freeze when just browsing webpages with FF. At first I thought it was GAIM but it froze just as often without GAIM running, and just now it froze while running two FF windows (one having a java applet loaded) and working with GIMP. 

I have 504.4MiB and am currently using about 25% (only have one FF window open)

Its difinitely not because of overheating because i'll have it on for scarcely 15 mins and it will freeze. My mouse and keyboard go as if unplugged and the screen looks just like it normally would except the mouse can't move and any moving things freeze.

Anyone know what the problem is?

I'll try to remember to come back and edit this post every time I freeze.

Edit: 10 minutes before 12:05 AM EST I was using a java applet and then it crashed, I believe (my problem atleast) is a java based error that causes the computer to freeze.

P.S. Does anyone know a command for the terminal that shows all active IPs connecting to the computer?

Just froze, 7:45 PM EST
Again 8:40 PM EST Almost an hour after.
You guessed it 9:05 PM EST this time...
Yep, you know what happend 12:05 AM EST.

---

### Post by benner on 2007-04-26
i was only getting 10 minutes or so before locking up before.  last night i had none.  don't know why.  i found this but don't know what to make of it.  says it's a network card problem.

[https://answers.launchpad.net/ubuntu/+question/5157](https://answers.launchpad.net/ubuntu/+question/5157)

---

### Post by Arcadian on 2007-04-27
Hi All,

Here's where I'm at (still have the problem).

Have found that I can regularly reproduce the problem by loading this page in FireFox and rapidly moving the page up & down using the mouse & scroll bar. Locks Ubuntu up every time, multiple times... seems to settle down though. I also get problems at logout/shutdown, where it halts & constantly repeats the logout sound. I'm guessing this is an IRQ conflict type issue.

Here's what I've tried so far (no success)
Fixed IP didn't help
pci=assign-busses kernel option didn't help
Using default human theme with no font smoothing didn't help (just in case my theme's funny)

I'm now on to trying other kernel options, trying an NVidia driver module option or switching back to the default NV driver

Here's my config
Latest Ubuntu 7.04
Kernel 2.6.20-15-generic
Nvidia driver 1.0-9631
ASUS A7V333MX
Athlon XP 2000
512MB DDR RAM
Nvidia GeForce 4 MX420 AGP (WinFast)

I bet the settings I toyed with previously in SUSE (see one of my last messages here for the link) will work. This page [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-f.html]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-f.html") helped me a lot!

Have to say, if Joe User has to put of with this, it's not a good look! No wonder Ubuntu have put the Restricted Drivers Manager in & say it's not supported when using NVidia drivers.

Will keep you posted!

Cheers,
Arcadian.

---

### Post by magnus07 on 2007-04-27
some additional in this post..
[http://ubuntuforums.org/showthread.php?p=2546905#post2546905](http://ubuntuforums.org/showthread.php?p=2546905#post2546905)

---

### Post by Arcadian on 2007-04-27
Magnus07,

I don't want to speak too soon, but it looks like **YOU DA MAN!** :guitar: 

I've tried what you suggested in the linked post & have to say, I can't reproduce the problem anymore.\\:D/ 
I can have firefox, thunderbird, rhythmbox playing & scroll firefox like crazy without a single lock-up.

Here's what I changed this morning...
- I rolled back all previous changes & reproduced the problem
- I went to System > Administration > Network

My settings were like this...

Location: <blank>
Wireless Connection: Ticked, WEP, Fixed IP
Wired Connection: Unticked, DHCP
Modem Connection: Dashed (Not Configured)

I then took your advice & changed my settings to this...

Location: **Home**
Wireless Connection: Ticked, WEP, Fixed IP
Wired Connection: **Ticked**, DHCP
Modem Connection: Dashed (Not Configured)

...and found that for now, the problem has gone! :cool: 

So all I did was enabled my on-board NIC (even thought it's not connected) & give the network profile a name (click the floppy icon next to it to save a name & connection profile). I'm not sure which it is, or if it's both, but I'll check this later.

Now I think about it, this is what I *used* to have under my old Feisty Release Candidate, no wonder it worked!

So, there we have it folks. I think Magnus07 deserves a beer :popcorn: =D> or 10!

I'd be really interested to hear if
- Other people have a similar success with their network profile settings (I'd suggest enabling any device, even if it isn't connected to a network)
- If others with the problem are running AGP cards. Thinking about PCI-E for my next one!

I think it's interesting that the networking may cause this, because with the problem present, when it killed my network connection it takes a good few seconds to even launch a terminal window. From memory X is a network based GUI (if that makes sense), so this would figure. Would have thought the loopback would cover problems like this though.

Apologies for the long post everyone and GOOD LUCK! I'll post back again in a couple of days... (in case I've spoken too soon)

Cheers Magnus07!

Arcadian :KS

---

### Post by Arcadian on 2007-04-27
P.s. One other thing I've also done is disabled Network Manager & gone back to the tradition ifup/ifdown method of controlling my network interfaces. The reason for that is I found it was the only way I could get my RT2500 wireless card to talk properly (WEP) with the delivered Ubuntu driver (gave up on the serialmonkey one). It would just never connect with Network Manager, which is a shame because it looks really good. That "may" be another factor if this simple fix doesn't help. Maybe...

---

### Post by Arcadian on 2007-04-27
Bugger! :( 

OK folks, last one today.

Looks like I may have spoken too soon, I was able to lock it up again by giving Firefox severe scrolling grief. Same symptoms (loss of network, audio drop, total freeze).

However, I have to say, doing these things has made it a little more stable. Lockups were sporadic before, but now only happen when I push things.

pci=assign-busses added to the kernel boot options in /etc/boot/grub/menu.lst does seem to make things a little snappier too I have to say.:-k 

So, what I've just tried now is adding a line to /etc/X11/xorg.conf (in bold)

Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 420]"
    Driver         "nvidia"
**    Option         "NvAGP" "1"**
EndSection

As I've said previously, this worked for me under SUSE. And seems to be okay so far.

Will shut up now & report progress tomorrow!

Cheers All!

Arcadian :KS

---

### Post by dagrump on 2007-04-28
Well, the desktop box still turns into a brick, so I started playing with my laptop, get this firefox is open, virtualbox is running xp, beryl is running, & I've been messing with it for quite awhile now & no lock ups. I'm so damn confused, why does this little beast run fine & the more powerful box fall on it's face? 
Oh, this is a Toshiba satellite a105-s4397, I did up the ram from 1 gig to 2 gig.

---

### Post by Scotty562 on 2007-04-28
I'm having the same problems too on Feisty. I never had this problem on Edgy.  I have a HP ZX5000 Radeon 9600 moble, broadcom (firmware cutter), p4. 

I installed Feisty on my buddies Dell during the same time I upgraded and he also is having the issue. He listened to me talk of Linux's ability to rarely ever crash and here it is crashing every day multiple times a day.

It has me so frustrated I'm considering ditching ubuntu myself :(. Windows may not be perfect.... but....

Hopefully the next kernel fixes things...

---

### Post by johanPO on 2007-04-28
I am more and more convinced that this has to do with the network settings. I had the problem, then I went to static IP and no problems for two days. Today I decided that I wanted to  get the network manager to work properly. I commented out me /etc/network/interfaces so that it contains only.

# The loopback network interface
auto lo
iface lo inet loopback

I left my PC alone for a while. When I got back it had crashed completely. I logged in and after 5 minutes it locked  up. Restart, and I used the manual configuration, with static ip. Looking in the log I find the follwoing

Apr 28 12:26:08 johans dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Apr 28 12:26:08 johans dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Apr 28 12:26:08 johans dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr 28 12:26:08 johans dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr 28 12:28:06 johans syslogd 1.4.1#20ubuntu4: restart.

Lets see how the day goes. I have 30 minutes of uptime now....

---

### Post by A*p on 2007-04-28
Same here, everything is frozen, but I can still move the mouse cursor around the screen, it has happened a few times now, I cannot even goto another console to see what is misbehaving or to reboot, I am left with having to pull the plug :sad:  i have been having issues with my network so it could be related.  Not sure if it is worth trying to fix or just reverting back to edgy as I need my lappy for work.

---

### Post by woopud on 2007-04-28
Interesting.  I have this old Dell Dimension Plll, 733mhz with 512mb Ram.   This machine will run anything, at the moment it's running Feisty and has been up for eight days straight !   I also have this "home build" PC with a PC Chips A31G motherboard, AMD 3000 1.8ghx cpu, 512mb of Ram, this PC is very picky concerning Linux, I've tried installing Ubuntu several times but most of the times the Live CD freezes up, got it to install once but after 5 minutes, bam, lockup.  At the moment it's running PCLinux 2007 without any problems at all.   I have to mention that I also tried Ubuntu Hoary and Edgy with the same results.

Bert

---

### Post by AndrewNi on 2007-04-28
OK posting again because it locked up under an hour ago. I was listening to some music which also stopped, suggesting that it is indeed a complete lockup and not just the keyboard and mouse going odd. (Was unlikely anyway).

I have read through this thread and have noticed that I had installed VirtualBox not long ago and that's when this problem started. So I have removed VirutalBox and hope that it has something to do with it.

My network configuration has been absolutely fine (wireless + wired) for the past months and hasn't changed, so I doubt in my situation that it has anything to do with DHCP or stuff like that. I have, however, put the network location into the Networking part of GNOME in Edgy to see if that does anything at all.

I'm curious at the pci=assign-buses parameter, what does that actually do?

---

### Post by KrazyPenguin on 2007-04-28
> I'm curious at the pci=assign-buses parameter, what does that actually do?

It assigns the pci busses at startup.  Each one has a number and by assigning them, linux will not get confused and mix them up.  

Only use if you get the error in /var/log/messages

Just open that file and search for pci=assign-busses.

Also notice that "busses" has two 's' es.

Since I edited my kernel startup file I have had no locks ups, and I am also running Beryl   !!!
;) 

> I hope I didnt' just jynx myself !!!  :shock: 

Did any of you people experiencing lockups try this: 

> [http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)
Go half way down page and try each of those options one at a time.

Do you get the pci=assign-busses error in /var/log/messages???
(do a search, it is long)

Also see if you can crash it without connecting to the internet.

2 hours with Beryl today and I am still trying to Freeze my system.


Here is my stanza:
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=70d0a61f-7453-46d4-85ad-1373ef99813a ro quiet splash noapic nolapic pci=assign-busses
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Notice the 3 things added to the end of the kernel:
Seems noapic and nolapic are important here for some reason.

Good luck!!!


So make sure you edit your stanza.  I didn't do it at first and wish I did it sooner.
;-)

---

### Post by magnus07 on 2007-04-28
KrazyPenguin, I did your fix. Nope.
:-(

---

### Post by dagrump on 2007-04-28
I feel like a dog chasing it's tail. I've read till my eyes bleed, well not really but it feels that way. The money pit still locks up like fort knox w/ little pestering on my part. I don't have  any ideas where to go from here other then pull the goodies out, & create some kind of server. That's most likely way over my head, but I sure am getting no love from this hardware.
I stopped fighting  the desktop as I was finding success with my laptop & I came back w/ renewed confidence only to be crushed like a bug. I guess that's what I get for throwing money into more hardware than needed. If some one every get this pinned down, I'll fight it some more, but I think it's like my ( I know this p.o.s will work) xp box setting in a corner gathering dust bunnies. If not I'll break something, most likely my foot kicking to the curb. I shall return, but I'm having more fun making old crap run then fighting w/ this machine. I'll check back to see if things change.

---

### Post by allforcarrie on 2007-04-29
don't feel bad i have totally deleted Ubuntu since i posted this.

---

### Post by dagrump on 2007-04-29
I'm just moving this to the the back burner, as I said there is old stuff to play with & I'm not having any success with this.  this machine was first brought to life on a daily build of edgy in late Sept. of 06 it will submit yet.

---

### Post by yoasif on 2007-04-29
> **allforcarrie said:**
> don't feel bad i have totally deleted Ubuntu since i posted this.Did you ever try disabling cool'n'quiet?

Connell and I have a confirmed bug logged into launchpad with that specific issue, it'd be great if you could confirm.

Obviously it's up to you, of course. :)

For anyone else who is interested, see: [https://bugs.launchpad.net/ubuntu/+bug/109643](https://bugs.launchpad.net/ubuntu/+bug/109643)

---

### Post by allforcarrie on 2007-04-29
i dont have a cool and quiet option on my board.

---

### Post by dagrump on 2007-04-29
Well in order to preserve my sanity (some might question it's existance) & protect the ears of the innocent, the money pit box is be reduced to parts. I could not even get feisty to install on the stupid thing. The jmicron chip set is a pain in the butt, & I've been trying to justify a different mother board. Yes, I was attemping w/ the alt. install disk, & did verify it as good before starting. At the moment I have 2 machines running feisty that don't lock up. One does have a strange conflict if I install my dvd drive, but has no issue w/ the same drive in a usb enclosure, beats me I can deal w/ that as it gives some extra flexibility w/ that burner. I have a old gateway run xubuntu 6.06, I believe I'll see what it thinks of feisty. It w/ it's whopping 13.9 gig quantum fire hdd, & 412 meg ram. I'm using it right now, it likes dapper just fine. good luck getting this freeze thing straightened out but there isn't anyway I'm trying to fight it. The stupid machine wins, which sealed it's fate, it's off to the parts pile.

---

### Post by johanPO on 2007-04-29
On my PC I am seeing interesting effects with my WLAN. It seems to loose connection. In this session, I had to do ifdown and then ifup to get back. The router is working (my work PC with XP is right next to me)


Apr 29 21:17:25 johans kernel: [ 8510.547776] eth0: No STA entry for own AP 00:17:9a:f2:96:71
Apr 29 21:17:57 johans kernel: [ 8542.515737] eth0: No STA entry for own AP 00:17:9a:f2:96:71
Apr 29 21:18:29 johans kernel: [ 8574.482029] eth0: No STA entry for own AP 00:17:9a:f2:96:71
Apr 29 21:19:01 johans kernel: [ 8606.450376] eth0: No STA entry for own AP 00:17:9a:f2:96:71
Apr 29 21:19:33 johans avahi-daemon[5265]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 29 21:19:33 johans avahi-daemon[5265]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.100.
Apr 29 21:19:33 johans avahi-daemon[5265]: Withdrawing address record for fe80::201:36ff:fe0d:cdbc on eth0.
Apr 29 21:19:33 johans avahi-daemon[5265]: Withdrawing address record for 192.168.0.100 on eth0.
Apr 29 21:19:43 johans avahi-daemon[5265]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.100.
Apr 29 21:19:43 johans kernel: [ 8647.786151] wmaster0: Does not support passive scan, disabled
Apr 29 21:19:43 johans avahi-daemon[5265]: New relevant interface eth0.IPv4 for mDNS.
Apr 29 21:19:43 johans avahi-daemon[5265]: Registering new address record for 192.168.0.100 on eth0.IPv4.
Apr 29 21:19:43 johans kernel: [ 8647.793166] eth0: Initial auth_alg=0
Apr 29 21:19:43 johans kernel: [ 8647.793170] eth0: authenticate with AP 00:17:9a:f2:96:71
Apr 29 21:19:43 johans kernel: [ 8647.797466] eth0: RX authentication from 00:17:9a:f2:96:71 (alg=0 transaction=2 status=0)
Apr 29 21:19:43 johans kernel: [ 8647.797470] eth0: authenticated
Apr 29 21:19:43 johans kernel: [ 8647.797473] eth0: associate with AP 00:17:9a:f2:96:71
Apr 29 21:19:43 johans kernel: [ 8647.800158] eth0: RX AssocResp from 00:17:9a:f2:96:71 (capab=0x431 status=0 aid=2)
Apr 29 21:19:43 johans kernel: [ 8647.800162] eth0: associated
Apr 29 21:19:44 johans avahi-daemon[5265]: Registering new address record for fe80::201:36ff:fe0d:cdbc on eth0.*.
Apr 29 21:19:53 johans kernel: [ 8657.917794] eth0: no IPv6 routers present
Apr 29 21:19:53 johans ntpdate[27992]: the NTP socket is in use, exiting

---

### Post by jonom on 2007-04-29
I haven't had any lockups now for a couple of days. Hopefully this posting won't jinx things. 

I tried the pci=assign-busses setting and disabled desktop effects.

---

### Post by jonom on 2007-04-29
Ok, so it definitely seems to be related to compiz/beryl for me.

I had been running compiz, and after things had been running well the last couple of days thought I'd try out Beryl instead. Had the system lockup on me shortly after getting beryl up and running, while I was running Firefox.

---

### Post by ferd on 2007-04-30
I was having a similar problem. It turned out that I had enabled a slideshow on my KDE desktop and every time the slide changed the system would lock up. I am using an old slow processor and it couldn't handle the load. When I turned of the slideshow, the problem was fixed. :)

---

### Post by johanPO on 2007-05-01
I just had a complete crash. 

Yesterday I left my PC untouched and it run for 6 hours without any problems. Then I did a bit of surfing and it crashed. 

Today I decided to download the feisty CD and do a complete re installation. It took 5 minutes and the PC crashed. When it came up it had even lost it's time and data setting

and was at January 1st 2006, at 1.59.....

---

### Post by magnus07 on 2007-05-01
I lost few more days and went back to 606 LTS.
Works flawlessy.
Let me know is 704 gets better...

---

### Post by iopo on 2007-05-02
Hi everybody!

I have a great news: 24 hours without freezing!

I more or less followed the advices of Arcadian and Magnus07. The steps are:

- right click on "network manager" icon and check "disable networking"

- system -> preferences -> sessions and make sure to uncheck "network manager"

- system -> administration -> network. Make sure both "wireless connection" and "wired connection" are checked . To enable "wireless connection" you may have to edit the options first: click option, uncheck "enable roaming mode" and select a wireless connection. In my case, to avoid issues with WEP or other kind of encription I decided to squat my neighbor connection for a while! For the same reason, I left the configuration on DHCP, but apparently  this is having no effect.

Enjoy!

---

### Post by johanPO on 2007-05-02
Thanks but that did not do it for me. Can crash my machine almost at will... I do think that it is a network issue, but I do not know where. Starting to think about going back to 6.06. Any problems with that, that anyone is aware off?

---

### Post by dmz on 2007-05-03
Wanted to share my own experience.  At the same time feisty launched I built two near identical machines, one as a home server and the other as a development box in the office.

Same motherboard Abit NF-M2 with integrated Nvidia graphics, and same memory 2x1GB memory.  Both have a WD 250gb HD, the home machine being an older SATA drive, work using a new SATA2.  Home also has a second 500gb drive.

Work machine is completely solid, not a single problem.  Home machine lasts 48hours at most, before locking solid at random.

There is a small difference in the processors.  
  Home is an AMD 64 X2 4600+ stepping 2
  Work is an AMD 64 X2 5600+ stepping 3

I've been working through the suggestions to resolve this, but no luck.  Disabled the Nvidia drivers, no luck and the work machine is happy with whizzy desktop mode.  Disabled cool 'n' quiet in the bios, still crashes.  Trying without the network manager now.

This is really frustrating, most of all because there doesn't seem to be any clear understanding of the cause of the problem.  Given my position of having two such similar machines, if there's anything I can post to help diagnose let me know.

---

### Post by rysh on 2007-05-03
Hi 

I don't know if this helps. I used to have random lock ups also a lot on Debian and also had these annoying things sometimes on Ubuntu. I found out that when commenting out the DRI module line in xorg.conf completely let the problem disappear. But a side effect was that compiz, beryl and any other GL application would not run anymore. In that time i had an ATI Radeon 9550 card.

---

### Post by johanPO on 2007-05-03
Tried with the modification of xhosts.conf. No luck for me. I can still make this thing crash by generating a bit of network traffic.

---

### Post by connellr on 2007-05-03
View the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643)

I have found that either disabling Cool'n'Quiet in your bios, or disabling the powernowd service in /etc/init.d has caused all of my lockups to stop.

---

### Post by dagrump on 2007-05-03
It seems there are several threads dealing with this issue, it seems the issue is just going to continue being ignored. I've already vented & now I'm just trying plot my options. Oh this thing doesn't lock up if I don't use any form  of Nvidia driver.  I hate to start digging around in another distro to get a usable machine.

---

### Post by iopo on 2007-05-06
Hi guys.
it seems I spoke too soon: it started freezing again! Disabling wireless manager made my system way more stable, but didn't solve the problem.
Anyway, I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90243)

they suggest three things:

1- append acpi=force irqpoll to the kernel parameter

2- switch to the 386 kernel

3- download and install the rt2x00  CVS from here: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)  

I tried the first one and until now no freeze. I'll eventually give a try to option 3 as well, but I'm not sure how to implement it. Any idea?



edit: I tried the first suggestion and it still freezes. Now I downgraded to the 386 kernel and in the last few hours absolutely no problems!

---

### Post by dmz on 2007-05-07
Through patience, I've managed to identify one event causing my home system to hang, but it's odd.  I usually have aMule running at home, and I noticed on Saturday that whenever I restarted it, the first thing it did was complete a file.

I checked backed through the logs and there's a link, whenever a file completes the system hangs.  I tried building aMule from src, and got the same result at the next file, one locked up box.  I'm now trying the background amuled, instead of the gui version.

I'm making progress, but at a loss to understand how amuled could be crashing a whole system.

spec - Amd X2 4600, 2Gb, 250GB & 500GB, Feisty 64bit.

---

### Post by brianw0667 on 2007-05-08
Using Xubunto 6.10 my Compaq Evo N610c would start to lock up periodically after I installed a ralink wireless card.  It seemed to be when there was a problem with the communication with the router.  I have since installed Xubunto 7.04 fresh install (crashed my system as a result of deleting a partition that subsequently renumbered my Xubunto partition) and have not installed the wireless card yet.  I didn't get any lockups under 6.10 when not using the wireless card and I haven't had any using 7.04 yet (although I have only had it installed since sunday but I have used it for many hours in the last couple of days without a problem on wired network).

---

### Post by abc123456 on 2007-05-08
Ubuntu has cron set to run very through crontabs hourly,daily,weekly,monthly.
If they are running everything slows down.  Check under services and disable.  See if that helps.  You can always turn them back on and scedule for 0300.:popcorn:

---

### Post by johanPO on 2007-05-11
Have now done a complete new installation. I can just say, no improvement. It freezes, and it seems connected to the network somehow.

---

### Post by dagrump on 2007-05-11
Well, I tried to live w/ a xp install but I would rather live w/ the freezes. One week of evenings trying to get that dreck setup like I want it & I hadn't even dug into the registry yet to stop the ever present reminders. I have not installed Nvidia drivers yet or Beryl or anything else, so I'll see how things go this weekend. I must say edgy is a sight for my feeble old eyes, I know what I want, I know where it's at, & I know if I do my part most of the time it'll do it's. My test box & my laptop are still running feisty w/o a hitch, i have no idea what the issue w/ this machine is other than the jmicron chipset might have something to do with it as feisty refuses to install. But, all things considered this old box feels more like home than it'll ever feel like w/ that other bundle of goo. So I guess this means I don't have it in me give up on Ubuntu.  I will have clean log files if she locks up though.

---

### Post by allforcarrie on 2007-05-11
linux mint is based off feisty and it runs great.

---

### Post by Heptapus on 2007-05-13
My Ubuntu became very unstable when I tried using accelerated graphics (Radeon ATI 9500 or something like that graphics card).  I have just gone back to slow graphics and so far it has not crashed again

---

### Post by roastbeef on 2007-05-13
I think I may have fixed my problem.  At random intervals mouse movement would stop and it would appear as if the computer became completely frozen.  The screen was static (but otherwise without graphical glitches) and the only way to recover was to hard reboot.

I have a Wireless linksys card which uses the RT61 chipset - apparently (thanks to reading through some of the links here) the drivers for RT61 aren't perfect, which causes crashes.  Luckily I don't have to rely on wireless - I have a wired card as well for internet access.  

Anyway, I blacklisted RT61 by editing /etc/modprobe.d/blacklist and adding "blacklist rt61", then removed the modules from the kernel by using "modprobe -r rt61".

So far I haven't had a crash, but the most I've ran it since I've tried this fix was about 5 hours or so.  I will reply back if I find anything else, but I remain hopeful!  Sometimes it took a whole day for the crash to show up, so anything is possible.

---

### Post by dagrump on 2007-05-13
Well, I would have to say that my machine seems somewhat more stable running the "nv" driver than the ones from nvidia, I won't lay the blame at their feet as I have had a couple of lock ups, since reinstalling edgy. One was loading win98 in virtualbox w/ firefox open on another desktop. The other was using dvdshrink on a movie (small people are hell on dvds). I think firefox was open then also, so it could be related to my wireless card. If this is the case I would think it would of happened when edgy was in it's infancy not just within the last month or so? I'm still trying to locate one of the early edgy cds I burnt.  I imagine I overwrote them though as I'm cheap & use r/w cd & dvds to save money & to stop the pile from growing. I can't remember if they had the generic kernel or just i386 one. But anyway I can tolerate this for the time, but I hope some one gets it narrowed down, I'm not sure if doom3 & quake4 will run on the crippled driver I seem to have to use. Guess thats the next step. later.

---

### Post by forcesofhabit on 2007-05-14
I am having the same problem. Mine always locks up within a few minutes of being booted. I tried installing Mandriva One 2007.1 and it does the same thing... I too think it may be a kernel problem.

Puppy Linux has no problems, but I don't know how to access my Creative Zen player :(

Has anyone tried any distros besides XP that "just work"?

---

### Post by allforcarrie on 2007-05-15
Linux mint didn't crash for me.

---

### Post by brianw0667 on 2007-05-15
> **roastbeef said:**
> I think I may have fixed my problem.  At random intervals mouse movement would stop and it would appear as if the computer became completely frozen.  The screen was static (but otherwise without graphical glitches) and the only way to recover was to hard reboot.

I have a Wireless linksys card which uses the RT61 chipset - apparently (thanks to reading through some of the links here) the drivers for RT61 aren't perfect, which causes crashes.  Luckily I don't have to rely on wireless - I have a wired card as well for internet access.  

Anyway, I blacklisted RT61 by editing /etc/modprobe.d/blacklist and adding "blacklist rt61", then removed the modules from the kernel by using "modprobe -r rt61".

So far I haven't had a crash, but the most I've ran it since I've tried this fix was about 5 hours or so.  I will reply back if I find anything else, but I remain hopeful!  Sometimes it took a whole day for the crash to show up, so anything is possible.


I believe that is the driver I use as well.  I built it from source and installed it and that is when I started getting lockups.  I am pretty sure it had to do with error handling when having communication problems (may be wrong but that is the way it seemed).  I have not had a chance to rebuild under 7.04 yet.

---

### Post by dagrump on 2007-05-15
Well,I'm still running "nv" video drivers but if bittorrent is running & the screensaver loads she locks like a rock. So, some where in this kernel or the wireless driver is my best guess. I sure hate having my screensaver disabled, just to down load some distro I lost with my old usb drive. I'm  going to be working on that for awhile as most everythingI had  was just iso images on that drive.
I guess those of us with this issue are just SOL till they decide to do something & since feisty refuses to install on this machine for some reason I guess I'm really up the creek w/o a paddle. 
I guess I'll just shut off my monitor if I'm not right in front of it, & see if no screensaver  (disabled at the moment) = no freeze. The beast was up 33 hours w/o locking over the weekend but I wasn't downloading anything at that time.

---

### Post by roastbeef on 2007-05-19
So far I have not had a lock-up since I blacklisted rt61.  Hopefully I won't need to post again, but if I get a lock-up I'll reply here.

---

### Post by johanPO on 2007-05-19
That is interesting. It confirms my suspicion that this has to do with the network somehow. Unfortunantly for me I do not have the RT61, but an intersil based solution...
from lspci
06:06.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01). 
lsmod | grep rt61 gives nothing. From what I understand I have the prism54

prism54pci             13440  0 
prism54common          12288  1 prism54pci
mac80211              175364  3 rc80211_simple,prism54pci,prism54common

Maybe I should dig out my old linksys card, that I was using with the ndiswrapper a while. this had an irritating habit of dropping the connection and needing an ifdown/ifup treatment to get started again. Now I am having the same again but with different HW (that worked fine uner 6.06 and 6.10) but with the additional system crash

---

### Post by iopo on 2007-05-21
I confirm that linux mint is stable: I installed it three days ago and no problem yet!

That's kind of interesting since ubuntu and linux mint are 99% identical. As far as I know linux mint is ubuntu plus codecs, flash plug-in and java already present in the default installation, menus a bit different, beryl preinstalled. So basically nothing too essential.

The only think I noticed booting up in verbose mode is that ipv6 module is blacklisted. Any idea is this can really be the cause of the freezes in feisty? Do you know how to figure out the differences between the two systems?

---

### Post by ghell on 2007-05-21
I used to get this problem because my northbridge is dodgy (by the time I worked out it was my northbridge it was too late for an RMA on my ASUS P5N32-SLI SE DELUXE) so my memory controller doesn't work. I had to underclock my ram to 667 or lower the voltage to 1.95v and ditch the idea of 4-4-4-12 on my ram (which should support it) to make it stable.

In my case the problem also caused SLI not to work on windows and windows to crash just as often as the fedora and ubuntu boots.

From the posts about the BIOS, I expect this is an underlying problem with the motherboard / bios / memory etc.

If you are getting problems with ubuntu locking up try running memtest overnight, this illuminated the problems for me. If you get faults on memtest, it is likely that every time one happens outside of memtest your system will lock up.

---

### Post by johanPO on 2007-05-21
I could run the memory test without any problems so that did not seem to be the problem. Would have surprised me as my HW was running fine with 6.06 and 6.10.

The Ipv6 was also interesting... but blacklisting ipv6 did not solve the problem for me. 10 minutes of filesharing and my PC frooze. 

Maybe I should try linux mint

---

### Post by Angelbeast on 2007-05-23
I've been having this problem too. It was just once every two to three days but i just hd it happen three times in a row just as soon as i rebooted from the last one. Once every two to three days was at least fairly tolerable compared to every few HOUR with Win98 but thi is getting annoying. I hope theres some sort of fix soon.

---

### Post by hanzomon4 on 2007-05-23
Me too, this sucks because I keep losing data in firefox(bookmarks, passwords, such) when I'm forced to hard reboot the system. This started happing after I reinstalled Icewm-experimental, vmware-server, urxvt, and clamav. I don't know what the problem is but I can't afford the data loss. So far I've only lost stuff in firefox that can easily be restored.

What happens is that gnome apps stop responding but non-gnome apps, like urxvt, still work. Eventually I have to open a terminal and sudo reboot because the regular logout/reboot thing doesn't work, however the sudo reboot doesn't reboot the system and I can't do anything in the tty terminals... Hard reboot is the only option and once everything is back up firefox is screwed and now zsh history file is corrupted.

---

### Post by hanzomon4 on 2007-05-23
I checked my system log, and messages and found something that may explain the non-responsive gnome based apps
 
messages ```
gconf server is not in use shutting down
``` Here's the systemlog ```
May 23 10:36:54 eidokin gconfd (hanzomon4-6149): Resolved address "xml:readwrite:/home/hanzomon4/.gconf" to a writable configuration source at position 0
May 23 10:37:02 eidokin NetworkManager: <information>^IUpdating allowed wireless network lists. 
May 23 10:37:02 eidokin NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 23 10:41:28 eidokin gconfd (root-7696): starting (version 2.18.0.1), pid 7696 user 'root'
May 23 10:41:28 eidokin gconfd (root-7696): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 23 10:41:28 eidokin gconfd (root-7696): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 23 10:41:28 eidokin gconfd (root-7696): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 23 10:41:28 eidokin gconfd (root-7696): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 23 10:41:28 eidokin gconfd (root-7696): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 23 10:41:59 eidokin gconfd (root-7696): GConf server is not in use, shutting down.
May 23 10:41:59 eidokin gconfd (root-7696): Exiting
May 23 10:43:13 eidokin gconfd (root-8441): starting (version 2.18.0.1), pid 8441 user 'root'
May 23 10:43:13 eidokin gconfd (root-8441): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 23 10:43:13 eidokin gconfd (root-8441): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 23 10:43:13 eidokin gconfd (root-8441): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 23 10:43:13 eidokin gconfd (root-8441): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 23 10:43:13 eidokin gconfd (root-8441): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 23 10:43:43 eidokin gconfd (root-8441): SIGHUP received, reloading all databases
May 23 10:43:43 eidokin gconfd (root-8441): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 23 10:43:43 eidokin gconfd (root-8441): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 23 10:43:43 eidokin gconfd (root-8441): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 23 10:43:43 eidokin gconfd (root-8441): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 23 10:43:43 eidokin gconfd (root-8441): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 23 10:43:43 eidokin gconfd (root-8441): GConf server is not in use, shutting down.
May 23 10:43:43 eidokin gconfd (root-8441): Exiting
May 23 10:56:07 eidokin -- MARK --
May 23 11:16:07 eidokin -- MARK --
May 23 11:17:02 eidokin /USR/SBIN/CRON[18691]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 23 11:18:57 eidokin kernel: [ 2606.030954] /dev/vmmon[19291]: Module vmmon: unloaded
May 23 11:18:58 eidokin kernel: [ 2606.453374] bridge-eth0: down
May 23 11:18:58 eidokin kernel: [ 2606.453393] bridge-eth0: detached
May 23 11:19:00 eidokin avahi-daemon[5158]: Interface vmnet1.IPv4 no longer relevant for mDNS.
May 23 11:19:00 eidokin avahi-daemon[5158]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 192.168.252.1.
May 23 11:19:00 eidokin avahi-daemon[5158]: Withdrawing address record for fe80::250:56ff:fec0:1 on vmnet1.
May 23 11:19:00 eidokin avahi-daemon[5158]: Withdrawing address record for 192.168.252.1 on vmnet1.
May 23 11:19:03 eidokin avahi-daemon[5158]: Interface vmnet8.IPv4 no longer relevant for mDNS.
May 23 11:19:03 eidokin avahi-daemon[5158]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 172.16.187.1.
May 23 11:19:03 eidokin avahi-daemon[5158]: Withdrawing address record for fe80::250:56ff:fec0:8 on vmnet8.
May 23 11:19:03 eidokin avahi-daemon[5158]: Withdrawing address record for 172.16.187.1 on vmnet8.
May 23 11:36:07 eidokin -- MARK --
May 23 11:50:02 eidokin gconfd (hanzomon4-6149): Exiting
May 23 11:50:05 eidokin gdm[5243]: Restarting computer...
May 23 11:50:07 eidokin hald: unmounted /dev/sdb2 from '/media/_home1' on behalf of uid 1000
May 23 11:50:07 eidokin hald: unmounted /dev/sdb1 from '/media/_12' on behalf of uid 1000
May 23 11:50:09 eidokin init: tty4 main process (4570) killed by TERM signal
May 23 11:50:09 eidokin init: tty5 main process (4571) killed by TERM signal
May 23 11:50:09 eidokin init: tty2 main process (4573) killed by TERM signal
May 23 11:50:09 eidokin init: tty3 main process (4575) killed by TERM signal
May 23 11:50:09 eidokin init: tty1 main process (4577) killed by TERM signal
May 23 11:50:09 eidokin init: tty6 main process (4578) killed by TERM signal
May 23 11:50:12 eidokin avahi-daemon[5158]: Got SIGTERM, quitting.
May 23 11:50:12 eidokin avahi-daemon[5158]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.196.
May 23 11:50:12 eidokin NetworkManager: <WARNING>^I nm_signal_handler (): Caught signal 15, shutting down normally. 
May 23 11:50:12 eidokin NetworkManager: <information>^ICaught terminiation signal 
May 23 11:50:12 eidokin NetworkManager: <debug info>^I[1179939012.405040] nm_print_open_socks (): Open Sockets List: 
May 23 11:50:12 eidokin NetworkManager: <debug info>^I[1179939012.405101] nm_print_open_socks (): Open Sockets List Done. 
May 23 11:50:19 eidokin exiting on signal 15
May 23 12:04:36 eidokin syslogd 1.4.1#20ubuntu4: restart.
```

Vmnet has given me this problems before so I uninstalled it, however I don't see the usually errors that were present when vmnet was the known culprit

---

### Post by jonom on 2007-06-08
After the new nvidia drivers came out I thought I'd give beryl/compiz a try again and I still get the random lockups. It only happens for me when running beryl or compiz.

How's everybody else fairing?

---

### Post by allforcarrie on 2007-06-11
up because i reinstalled feisty today and this happened again.

---

### Post by Arcadian on 2007-06-20
Hi All, 

An update from me. Ever since I've done the following (and gone through all the kernel/glx updates) it's been pretty goof proof for me...:popcorn:

Adding a line to /etc/X11/xorg.conf (in bold)
Section "Device"
Identifier "nVidia Corporation NV17 [GeForce4 MX 420]"
Driver "nvidia"
**Option "NvAGP" "1"**
EndSection

I still have my WEP WiFi connection dropping out sometimes, but other than that, I'm fairly happy. For me it seems to be a problem of finding out what linux configuration works with my hardware. Doesn't seem to be fine straight out of the box.

Good luck to you all!

:KS

---

### Post by NickeM on 2007-06-20
I have had frequent freezes/lockups of my ubuntu machine, this started when i upgraded to feisty. I have discovered that when i run something cpu intesive my machine locks up.

For awhile i could not figure out what caused this, have tried the usual suspects, 3d drivers(nvidia), noapci (different boot options), new kernel etc. but to no avail.

But then i unplugged my atmel usb wlan adapter and ran on a regular internet cable connection, lo and behold no more freezes and crashes. I usually test this by running nexuiz at a high resolution or executing a heavy batch job.

I have filed a bug for this but no response from the devs so far, i think it either a bug in the wireless driver or in the usbcore. I have lately suspected usbcore, because there are so many with random freezes with different wlan adapters.
[atmel driver freeze bug report]("https://bugs.launchpad.net/ubuntu/+source/atmel-firmware/+bug/120800")

---

### Post by allforcarrie on 2007-07-01
up

---

### Post by yorkie on 2007-07-01
[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
I had same problem but now everything o`k actions taken 
got rid of firefox installed opera
disabled desktop effects
uninstalled skype
Don`t know which action solved problem but pc run fine over 2weeks
hope this is some help to you.

---

### Post by brianw0667 on 2007-07-02
Update.  I tried my ralink rt61 (pcmcia) card again and system started freezing.  I needed greater range so I purchased a usb dongle and router (trendnet pair) and I have not had any lockups since (been using for a few days now).  To get the dongle working (tew-424ub with its rtl8189 chipset using 8187 driver) I had to use ndiswrapper as the included drivers for the rtl8187 did not work and I have not been able to compile the downloaded drivers from trendnet yet (still working on that).  I think I might try ndiswrapper on the rt61 pcmcia card (since I know how to do it now, I did not succeed with the rt61 card since I had never used ndiswrapper before).  Background, I compiled the rt61 driver in 6.10 and used the supplied driver in 7.04 with the same problem.  It really looks like a driver source problem (since I compiled from source in 6.10 and used the already compiled in 7.04) to me (for my situation anyway).  Maybe there is an insmod option that I am missing which would solve the issue.  If I get the rt61 card working with ndiswrapper it would indicate definately that the driver source code is the issue (I know it works under XP but I have not used it for long in XP since I only use windows as a very last resort, basically to test functionality if I am having problems in linux since most vendors only reliable produce drivers for windows).

---

### Post by brianw0667 on 2007-07-13
Been using the rt61 driver with ndiswrapper and have had no problems.

---

### Post by stratman4300 on 2007-07-17
I was having this same problem, and had tried just about everything i found on this thread. 

My issue was that if i left my machine alone for more than two minutes, it would hard-lock. so i started piddling around in my syslog and found this.   

[I]Jul 16 07:44:51 DreamMachine gconfd (root-5494): starting (version 2.18.0.1), pid 5494 user 'root'
Jul 16 07:44:51 DreamMachine gconfd (root-5494): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 16 07:44:51 DreamMachine gconfd (root-5494): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 16 07:44:51 DreamMachine gconfd (root-5494): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 16 07:44:51 DreamMachine gconfd (root-5494): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 16 07:44:51 DreamMachine gconfd (root-5494): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4[/I]

Seems like this was always the message i got in syslog around the time of lock-up. Started thinking to myself, gconf should be installed by default right???   NOPE...  it wasn't.

so I ran a quick

*sudo apt-get install gconf*

problem solved........   i let it sit all night came back this morning and it was still running like a champ.

Hope this helps some of you.

Cheers!!

---

### Post by stratman4300 on 2007-07-17
yeah scratch that......  guess i just got lucky....    :(

---

### Post by maxrisc on 2007-07-25
Same here.  Mine was running fine until I installed the Broadcom firmware.  Now the system locks up randomly.

I am running on a Gateway 7422GX with internal WiFi mini PCI based.

If I shut down the WiFi NIC I don't experience lockups and halts.

---

### Post by stratman4300 on 2007-07-26
I just upgraded to Gutsy.......   Problem solved   :P

I like living life on the edge....   :D

---

