---
title: "Hardy Heron slow!"
date: 2008-04-27
forum: General Help
---

### Post by pkiula on 2008-04-27
Why is it that Ubuntu is getting slower and slower with every release? I have a Dell Latitude C840, which is quite a decent machine and used to run Win XP quite OK. I was recently running Ubuntu pre-HardyHeron (was it 7.xx?) and even that was slower than XP, but Hardy Heron is SLOW! What am I missing?

---

### Post by sports fan Matt on 2008-04-27
It was 7.10 Gutsy gibbon..Can you try running "top" in the terminal to see what is using your processor?

---

### Post by danwood76 on 2008-04-27
First make sure your desktop effects are off, this will slow you down somewhat.
On my two machines Hardy feels just the same as Gutsy (7.10) although looks a bit nicer and the new version of nautilus has quite a few good features.

It might be that you dont have enough RAM, I reccomend 1GB as a minimum for current day OS' especially as ram is getting so cheap these days.

XP is a very old OS, like 7 years.
Try running Vista and see what you think about the comparative speed then.

---

### Post by mrsteveman1 on 2008-04-27
Sometimes the code does get slower, its not easy to optimize things to prevent that from happening. A lot of the work done on KDE4 so far has been optimizing it substantially so that sort of slowdown doesn't happen.

Its worth noting that if you run Windows95 on a modern machine it would probably be lightning fast, though i highly doubt there are drivers available that would let you do so.

---

### Post by ludovicc on 2008-04-27
Can you post your /etc/hosts file, sometimes the upgrade process makes a mess in this file and that can slow networking which slows all applications (applications take 10 seconds to a few minutes more before stating). This happened to me in another upgrade. 

This is what my hosts file looks like:
```

127.0.0.1 ubuntu-desktop localhost
127.0.0.1 ubuntu-desktop.lappart ubuntu-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Skipster on 2008-04-27
I Run ubuntu on a very old laptop with minimal ram (512Mb) and a small processor (1Ghz) and I have no issues with performance.  ubuntu runs much faster than WinXP...

My guess is that you've got some config issues somewhere...  what are the specs on your machine? what does the output from top look like?

---

### Post by ghost_ryder35 on 2008-04-27
> **pkiula said:**
> Why is it that Ubuntu is getting slower and slower with every release? I have a Dell Latitude C840, which is quite a decent machine and used to run Win XP quite OK. I was recently running Ubuntu pre-HardyHeron (was it 7.xx?) and even that was slower than XP, but Hardy Heron is SLOW! What am I missing?
when i googled your comp i got
[http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,10000358,00.htm](http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,10000358,00.htm)
is that it
if you only have 256mb that will defintly slow things down very much
 
 
you should also turn off all started programs that you do not need
bluetooth
visual aid
ipv6
etc...

---

### Post by pkiula on 2008-04-27
Hi

Mine is a Dell Latitude with 1GB of memory already, and a Pentium IV processor. Windows XP ran faster. Gutsy was ok, slower than XP but fast enough to do stuff. 

Now the whole system is running INCREDIBLY slow! To open nautilus took me about 10-20 seconds, while on gutsy it takes me only 2-3! 

I don't have effects turned on at all -- never had them, never liked them. So, it is just the usual desktop that is slow. 

Gutsy had not read my nVidia drivers very well. I am using nVidia drivers from another thread for the display driver. The "opensource" or free nVidia drivers bundled with Gutsy sucked big time, and the official nVidia drivers would crash the machine, or make the desktop show up only in 75% of the screen. So that was a lousy experience but I sorted it out through some help in another thread. 

Anyway, what other settings can I change to make my Hardy Heron work faster?

---

### Post by daveofdave on 2008-04-28
I have the same prob, hp pavilion 453 .
 now admittedly I only have 256 ram but it ran gutsy really well - much faster than XP.
If I watch system monitor when  the pc's working on something there is ram to spare but the  cpu is going flat out, to the point where things can grind to halt completely.

any help gratefully received !

---

### Post by danwood76 on 2008-04-28
Basically the CPU will be maxing out writing stuff that would belong in your RAM on to your Swap (hard disk) which is a lot slower.
Best solution is to buy more RAM, you will be pleased with the performance increase going from 256MB to 1GB and it really doesnt cost much and is easy to install.

---

### Post by Candolle on 2008-04-28
Having the same problem here. Running an Asus T2 Celeron D 2.8Gz with 1GB of ram. It used to run Gusty (7.10) very well but doesn't do so well under Hardy Heron. It takes almost 20 minutes to start up and when checking the System Monitor it shows that the CPU is almost at 100% and most programs have become unusable. I noticed that Whiptail seems to be taking up 65% CPU. 

Could this be a problem with my hardware? Any suggestions are welcome!

---

### Post by mrsteveman1 on 2008-04-28
I'm starting to get the feeling something is wrong with the hardy kernel, they can fix it obviously but i've seen a few other kernel specific problems with hardy upgrades on users systems.

It would be nice if people could use latencytop to see why the system is so slow, but it isn't supported by 2.6.24 and likely will never be supported by hardy either. It was added in 2.6.25.

---

### Post by danwood76 on 2008-04-28
I dont think its the kernel specifically, I think its the upgrade process.
Some settings that are retained during the upgrade seem to give issues, a lot of people have done clean installs after having issues with an upgrade and their systems have been fine again.

I remember a similar thing happened when gutsy was released, though it wasnt as bad.

---

### Post by oboedad55 on 2008-04-28
> **danwood76 said:**
> I dont think its the kernel specifically, I think its the upgrade process.
Some settings that are retained during the upgrade seem to give issues, a lot of people have done clean installs after having issues with an upgrade and their systems have been fine again.

I remember a similar thing happened when gutsy was released, though it wasnt as bad.

I did a clean install, several actually, and have the same sluggish performance others have mentioned.

Peace,

---

### Post by danwood76 on 2008-04-28
Well Ive got hardy running on an old P4 system (pre northwood core ~2GHz) with 1 GB Ram and it runs very smooth, not slow at all. (no desktop effects)
I also have it running on my laptop, 1.7GHz Core Duo, 1 GB Ram and it runs really well with compiz effects on, and my desktop 3.6 GHz Core 2 Duo (OC'd), 2 GB Ram and its lightening fast (I wouldnt expect it to be any different)

I would have thought the memory footprint of GNOME has increased and all the machines Ive tested on have 1 Gig or over so maybe this is the cause of some people issues and others it could be configs.

A slow down can be caused by so many things thats its silly to think that its a bug in the system if people are running it on much newer and older hardware and getting good results.

@oboedad55
Your system should be more than capable of running hardy with no issues, have you tried switching compiz off and updating your graphics drivers? The 6200 is quite an old card and AGP is quite slow also, I would have thought compiz on this card would make your system slow down a bit.

---

### Post by defconoii on 2008-04-28
Well, this is a truly unforunate issue, it seems gnome/ubuntu is indeed getting slower and slower, and the only answer for that is poor coding and lazyness.  Its a shame kde4 is so much faster when more developers are working on gnome than kde.  Seriously the features are fine, and the quality of the code needs to be optimized/worked on. 
> **pkiula said:**
> Why is it that Ubuntu is getting slower and slower with every release? I have a Dell Latitude C840, which is quite a decent machine and used to run Win XP quite OK. I was recently running Ubuntu pre-HardyHeron (was it 7.xx?) and even that was slower than XP, but Hardy Heron is SLOW! What am I missing?

---

### Post by oboedad55 on 2008-04-28
> **danwood76 said:**
> 

I would have thought the memory footprint of GNOME has increased and all the machines Ive tested on have 1 Gig or over so maybe this is the cause of some people issues and others it could be configs.

A slow down can be caused by so many things thats its silly to think that its a bug in the system if people are running it on much newer and older hardware and getting good results.

@oboedad55

Your system should be more than capable of running hardy with no issues, have you tried switching compiz off and updating your graphics drivers? The 6200 is quite an old card and AGP is quite slow also, I would have thought compiz on this card would make your system slow down a bit.

My point, and I think that of others, is that Heron is slower than Gutsy. My fresh install was slower without compiz than 7.10 is with it.

---

### Post by punong_bisyonaryo on 2008-04-28
This problem is not with the upgrade process; we tried it with a clean install from the CD. It is also not a problem with the hardware. Of course a 256MB system is slow, but the question is why is it running even slower on Hardy. The point is in comparison. I have an SH6 Kohjinsha, it was lightning on Gutsy, but I can't help noticing the performance slow down in Hardy.

---

### Post by daveofdave on 2008-04-30
I hear what you're saying Dan, but gutsy was really fizzy quick even with my meager 256 ram and heron is really quite often grindy to the point stoppage !

Can there really be such significant difference in ram demand between gutsy and heron ?

I have the system monitor applet running and it goes off the scale when I use the scroll wheel.

Me, I think there's a bug, If not I shall probably return to gutsy.

---

### Post by danwood76 on 2008-04-30
> **punong_bisyonaryo said:**
> Of course a 256MB system is slow, but the question is why is it running even slower on Hardy.

Because the memory requirements have gone up.

If you want something faster look at using something other than GNOME, something like XFCE is much lighter and should run a lot faster.

Also I heard of people having memory usage issues in gutsy.
If I look in hardware monitor now I can see that firefox is using 500 MB of RAM atm, I have quite a few tabs open but I bet firefox 3 has larger memory requirements that firefox 2.

---

### Post by mrsteveman1 on 2008-04-30
ffx3 uses less ram

---

### Post by danwood76 on 2008-04-30
Really?
My mistake.

---

### Post by pythonusr on 2008-05-01
I haven't seen a HUGE slowdown, but one is apparent.

Also, Firefox uses much more RAM and CPU on my system, I don't know what you're talking about, mrsteveman1.

---

### Post by mrsteveman1 on 2008-05-01
in ffx2 i used to have to close the browser to regain the 600mb of memory it would eventually use, and lots of things were slower.

in ffx3 i can leave it open pretty much as long as i want and abuse the hell out of it with 50+ tabs open and once i close those tabs the memory comes back and is freed up. It's also quite a bit faster at just about everything, and its only a beta.

Now i will grant you that the linux version is in fact slow for some reason at the moment, especially scrolling web pages while compiz is enabled, which is painfully slow. But on OS X and Vista ffx3 is very fast. I've had it open for a few hours now and its only using 100mb of ram.

---

### Post by elvinatom on 2008-05-01
I must agree with it: Ubuntu is slow. But only the startup of applications. For example let's say I got a 1GHz P3 with 512MB: In XP you start IE6 - takes 0.5sec; In Ubuntu you start Firefox - takes 5-10sec. With MS-Office/OO.org and some other programs it's the same. That is because (from what I understand) the libraries for these programs are loaded on system start under Win as opposed to Linux it's on application start. Why this isn't being worked on I will never know. Doesn't seem to be an option. MS came up with that at Win95 times - quite a while ago.

---

### Post by skymera on 2008-05-01
Yeah i agree.
Ubuntu is slow.

I've noticed since 7.04, Ubuntu is getting slower and slower.
MY specs have gone up since then,i have more RAM and a better video card.

Im only using Ubuntu purely because of familiarality.
I'd much rather use Arch if i'd have the time.

---

### Post by domz76 on 2008-05-01
> **pkiula said:**
> Hi

Mine is a Dell Latitude with 1GB of memory already, and a Pentium IV processor. Windows XP ran faster. Gutsy was ok, slower than XP but fast enough to do stuff. 

Now the whole system is running INCREDIBLY slow! To open nautilus took me about 10-20 seconds, while on gutsy it takes me only 2-3! 

I don't have effects turned on at all -- never had them, never liked them. So, it is just the usual desktop that is slow. 

Gutsy had not read my nVidia drivers very well. I am using nVidia drivers from another thread for the display driver. The "opensource" or free nVidia drivers bundled with Gutsy sucked big time, and the official nVidia drivers would crash the machine, or make the desktop show up only in 75% of the screen. So that was a lousy experience but I sorted it out through some help in another thread. 

Anyway, what other settings can I change to make my Hardy Heron work faster?

I also experienced slowness issues with hardy until i discovered that changing the network configuration from 'manual' to auto (DHCP) speeded things right up. Ubuntu seemed to dedicate all its resources in trying to resolve the incorrect IP address and gateway etc.

---

### Post by GnuSense on 2008-05-10
Like Candolle I found that whiptail was eating every cycle that wasn't otherwise disposed of, "sudo killall whiptail" made my system much more reponsive.  See if it works for you.  

```
apt-cache show whiptail
Package: whiptail
Priority: important
Section: base
Installed-Size: 96
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Alastair McKinstry <mckinstry@debian.org>
Architecture: i386
Source: newt
Version: 0.52.2-11.2ubuntu1
Replaces: newt0.10, newt0.21 (<< 0.21-4), whiptail-utf8
Provides: whiptail-provider, whiptail-utf8
Depends: libc6 (>= 2.7-1), libnewt0.52 (>= 0.52.2), libpopt0 (>= 1.10), libslang2 (>= 2.0.7-1)
Conflicts: whiptail-provider
Filename: pool/main/n/newt/whiptail_0.52.2-11.2ubuntu1_i386.deb
Size: 35304
MD5sum: ceab1595e45b0547dbe5edb9298aa29f
SHA1: 60d4b8c73d452af0ce72f32488f63e2ae61bf419
SHA256: d695b8b85a44adb23bd080d81c1c3624fd1b218b3482e101227238e61af94b5b
Description: Displays user-friendly dialog boxes from shell scripts
 Whiptail is a "dialog" replacement using newt instead of ncurses. It
 provides a method of displaying several different types of dialog boxes
 from shell scripts. This allows a developer of a script to interact with
 the user in a much friendlier manner.
```

---

### Post by jaims on 2008-05-11
Hi there

I have found that if I disable the 'enable roaming' checkbox in the System/network dialog, as I use an static ip for eth0, my (new flaming) hardy heron works very very slow:
- when booting, from the logon screen till gdm is fully loaded, it takes ages.
- when opening a new app from the menu

If I enable roaming, it works fine... but then I have no inet at all (my home configuration is based in static ips).

I think that this is a bug. 
This stuff had always worked right in previous ubuntu versions.

I'm using a sony vaio vgn tz27gn, btw.

By now I think I will configure 2 network profiles:
- a dummy one with 'enable roaming',
- and the good one with the static ip and stuff (roaming disabled)

This way my laptop will boot at a normal speed; and I'll be able to use the internet switching network profiles.

The only thing I have to be careful of is to switch to the dummy profile just before shutting down of my laptop. If I don't, next time booting is going to be painful again...

Hope it helps, in case anyone has the same problem.
And hope to hear anything about it, if anyone happens to know :-)

---

### Post by FakeOutdoorsman on 2008-05-11
The standard Ubuntu installation does seem a bit sluggish for my hardware, but a custom install is very responsive.  Who says you have to install Gnome, KDE, or XFCE?  I often just get the "alternate" Ubuntu installation disc and choose a command-line only install.  Once the command-line system is installed I build up from there.  It's a great learning experience and lets you cut out the fat.  Currently running Openbox as my Windows Manager.

[Ubuntu Installation on Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") (good examples)
[Lightweight Gnome]("http://ubuntuforums.org/showthread.php?t=298835")
[urukrama's Openbox Guide]("http://urukrama.wordpress.com/openbox-guide/")

Also check out K.Mandla's [Howto: Set up Hardy for speed, v1.0]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/").

---

### Post by lazychris2000 on 2008-05-29
I have a Latitude C840 (see specs [here]("http://www.angelfire.com/wv/xmorgan/C840/C840-hardy.html")) and have absolutely no problem with it, with the exception of the nvidia drivers (see note on specs page).  I would _definitely_ recommend upgrading to the latest BIOS and upgrading the memory.  When I went from 512MB to 1GB of RAM, I noticed a huge improvement in performance.  The disk thrashing from writing to the swap file dropped pretty dramatically, as well.  When I ran XP Pro on this machine, it was like riding a slug through molasses, going uphill, but after putting hardy on, I have had no problems and it is pretty fast.  I have also used dapper, edgy, feisty, and gutsy on here and the difference in performance is minimal.

---

### Post by InuY4sha on 2008-09-05
Hi guys,
same problem here: I'll try to describe
A) WHAT IS SLOW:
 - After login screen, loading of the desktop environment
 - Opening any application
 - Writing anything on the shell (this applies also to the non graphical shell I get with CTRL+ALT+F1)

B) HOW IT'S SLOW
 - Top doesn't identify any process eating up the CPU
 - Moving/resizing/minimizing windows (with/without) graphical effect is damn fast (so I guess it's not an X problem...)

C) THE MACHINE
 - Athlonx XP 2.5GHz + 2GB RAM + 2 GB swap
 - [COLOR="Red"]ATI All in wonder 9800 pro[/COLOR] (NOT using any restricted drivers stuff)
 - Nvidia nforce2 mother board chipset
 - Clean install [I hate upgrades..]

[COLOR="Red"]I also changed the /etc/network/interfaces[/COLOR] accordingly to my needs and if I remember well it worked fine before doing this change (well I did a couple so I could not tell for sure).. gonna try with "enable roaming" from the nework manager, and eventually with reinstalling it and let you know

In red I emphasized what imho could be relevant points to have a look at.

I'll let you know as I progress with tests...

---

### Post by _emanuele on 2008-10-28
I just upgraded to hardy heron 8.04. My computer is very slow. I cannot change the resolution of the screen (before with gutsy was perfect). The sound is not good!!! I cant play DVD anymore. Need seconds just to scroll a simple web page (with 2GB RAM and CPU Dual core AMD +5000) or to open the termial. If I unplug the network cable or I loose internet connection the system freezes and i need to restart. Is it worth having hardy heron and Ubuntu in general???. It is true that Ubuntu its free (this was the reason I start to use Linux - few minths ago), but every time we need to spend hours to tweaks it and make it run nice. I am thinking to go back to Windows (it is true you will paid it, but then it is ready to be used).

Need to know how downgrading to Gutsy!! Do I need to reinstall everything?

Many thanks
E.

---

### Post by danwood76 on 2008-10-28
You probably have the xgl xserver installed and/or not the correct graphics drivers.
You need to remove xserver-xgl using synaptic, you dont need it anyway, and install your graphics drivers through the hardware drivers manager.

Also its a bit of a pricky thing to slate an OS whilst your trying to get help!

---

### Post by Dark9204 on 2008-10-28
I think you should reinstall your OS. My experience with ubuntu is that it is really fast.

---

### Post by _emanuele on 2008-10-28
> **danwood76 said:**
> 
Also its a bit of a pricky thing to slate an OS whilst your trying to get help!

I am trying to resist and keep with the open source. However sometime its difficult especially when time is money (and with my experience I need loads of time to make Linux run efficiently)!!!

Thanks for the suggestions. I am trying now.


e.

---

### Post by cariboo on 2008-10-28
To prove that ubuntu is slowing down with each release have a look at this:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=10](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=10)

That being said. I'm running Interipd and according to bootchart it takes 27 seconds to boot, which is about 3 seconds faster tha Hardy, and as far as firefox being slow to start this is how long it take firefox to start:

```
time firefox

real	0m0.190s
user	0m0.040s
sys	0m0.032s
```

My specs:

Motherboard: MSI K9NGM2
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Ram: 2Gb
Video apdapter, sound and network onboard
Hard drives: 250Gb IDE and 160Gb SATA

The 250Gb has Vista Utilmate Editon and Intrepid Ibex installed. The 160Gb is empty at the moment.

Jim

---

### Post by Crick on 2009-07-07
> **InuY4sha said:**
> Hi guys,
same problem here: I'll try to describe
A) WHAT IS SLOW:
 - After login screen, loading of the desktop environment
 - Opening any application
 - Writing anything on the shell (this applies also to the non graphical shell I get with CTRL+ALT+F1)

B) HOW IT'S SLOW
 - Top doesn't identify any process eating up the CPU
 - Moving/resizing/minimizing windows (with/without) graphical effect is damn fast (so I guess it's not an X problem...)


I had a very similar problem to this and could not for the life of me work it out. Applications took forever to load, slow to load the desktop environment, etc.

Editing my hosts file solved it for me. The post by PmDematagoda (#4) did the trick. Maybe this will work for you?

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by InuY4sha on 2009-07-07
> **Crick said:**
> I had a very similar problem to this and could not for the life of me work it out. Applications took forever to load, slow to load the desktop environment, etc.

Editing my hosts file solved it for me. The post by PmDematagoda (#4) did the trick. Maybe this will work for you?

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Thanks man! appreciated! I don't remember if I solved the problem or reinstall the OS... but it's good to know for the next time it happens!
Cheers

---

