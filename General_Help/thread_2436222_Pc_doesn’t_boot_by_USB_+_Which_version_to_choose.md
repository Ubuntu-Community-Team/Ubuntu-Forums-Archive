---
title: "Pc doesn’t boot by USB + Which version to choose"
date: 2020-02-02
forum: General Help
---

### Post by migascool123 on 2020-02-02
Hi, 

I’m having trouble installing lubuntu in my PC. The PC is old, has 512mb of ram and the date of bios is around 2003. And when I choose to boot from my usb flash drive, appears a message “invalid partition table”. Does anyone know how to solve it?

I’ve other question, that’s what the difference between the Desktop version and the Alternative version of Lubuntu.

Many thanks

---

### Post by guiverc on 2020-02-02
Invalid partition table would imply to me the data on the drive is corrupt, I'd be tempted to just create new partition table on your drive and start again AFTER validating your drive health, ie. drive problems could be the result of a failing drive, so wasting time on it doesn't make sense, [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)  Validate it's worth spending time trying to create new partition table & use it first...

The Lubuntu install media (I'll talk about 18.04 media here, see [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/) and drop down to 18.04.3 Bionic Beaver LTS (LXDE) is available firstly in Desktop 64-bit (called AMD64 as amd created the compatible (with 32bit) 64bit instruction set run today on intel & amd cpus) or Desktop 32-bit (Debian & Ubuntu refer to all 32-bit as i386; but a 686 level cpu is required).

The 'live' mode of the install media needs around 700MB to correctly run, yes it can run in less but performance will be hit, and some functions will act like they aren't running.  The installer when run on top of that requires more memory meaning you should have more than 700MB.

To allows systems with very tight memory (eg. 768MB) the alternate installer was created; it doesn't have a 'live' mode, so uses the debian-installer instead of `ubiquity` allow it to run on machines with 700MB of ram or less.  The alternate installer has no updates, so it was Ubuntu 18.04 LTS as it was back in 2018-April (ie. 18.04 as Ubuntu uses a *year.month* format) where as others have updates included.

I'd suggest increasing your RAM if all possible, you also didn't provide details of your CPU. I did test Lubuntu up to and including Lubuntu 19.04 (whilst i386 ISOs were available anyway) on laptops from 2005 & later, but only with 1GB of RAM.

Lubuntu 18.04 LTS is the oldest supported release of Lubuntu, as flavors have only 3 years of support (unlike main Ubuntu which has 5 years for LTS releases), your alternative is 19.10 which is available in amd64 (64-bit) only (Note: intel uses amd64 too; intel's 64-bit ia64 is EOL/abandoned as amd64 was backward compatible where as ia64 wasn't). Lubuntu 18.04 LTS is supported until 2021-April (ie. 3 years)

You didn't provide release info of what Lubuntu you tried; but you do need alternate (due to RAM syou have, but note updates will take much longer to download & install during install as it has many times the amount to download & install compared to the updated non-alternate installer).

---

### Post by migascool123 on 2020-02-03
Thanks for help @guiverc ! 
How can I verify the health state of my pen drive in Windows 10?
I’ve tried the Lubuntu 18.04 Alternate 32 bits, and you recomend this one, right?
The installation of the Alternate version is deferent than the Desktop version? I mean, the installation process.
My CPU is a Intel Pentium 4 1900 MHz
This pc was with no use during many years, and now I want to give it a “new life”. I will only use the PC sometimes, and it are going to stay always offline. So the support isn’t important to me because I will not make updates.
Thanks for help

---

### Post by CatKiller on 2020-02-03
> **migascool123 said:**
> My CPU is a Intel Pentium 4 1900 MHz

By my reckoning, that's [Willamette](https://ark.intel.com/content/www/us/en/ark/products/27430/intel-pentium-4-processor-1-90-ghz-256k-cache-400-mhz-fsb.html), which is 32-bit. You've missed the boat on being able to easily use Ubuntu with that, since 32-bit install images have been phased out. A few years ago resurrecting that machine for a bit would have been easier. 

A Raspberry Pi will give you a faster machine with more modern connections, while using *way* less power, and being much easier in general. 

Otherwise there are other distros that still provide 32-bit images, for now.

---

### Post by mörgæs on 2020-02-03
> **migascool123 said:**
> I will only use the PC sometimes, and it are going to stay always offline.

If it's not on the net you can use any kind of old Buntu. One of my all time favourites was 8.10.

---

### Post by migascool123 on 2020-02-03
Hi
I&#8217;ve some updates in my case: I&#8217;ve already downloaded the Lubuntu 18.04 Alternate 32bits. I&#8217;ve also a doubt about what option to choose doing the rufus configuration, if it is freeDOS or ISO, I choose ISO did I choose the right one?
When I put first the pen on the pc, it doesn&#8217;t recognize it and I have to create a particion in the windows discs manager, so the data was really corrupt... It could be by the several times that I take it of from computer or the bad job doing by Escher, because after I use Escher to create the iso, the pc doesn&#8217;t recognize it, but I think that was a normal process, because I was finishing creating a bootable pen. But know, I can enter the usb pen, and explorer it.
Am I in the right way?
Thanks

---

### Post by CelticWarrior on 2020-02-03
You need to also consider the possibility of that USB stick being about to fail. Etcher usually does a good job (runs in DD mode). With Rufus you may try also the DD mode. If it doesn't boot then there's a problem with that USB and/or the USB ports.

---

### Post by migascool123 on 2020-02-03
Thanks for help! Yes the usb drive could being about to fail. I know that Escher usually do a good job (was just because this reason that first I use escher), but the fact is that with escher I couldn&#8217;t open the usb stick, and the Rufus I can open the pen and see the files. I used iso mode, when Rufus ask me.

---

### Post by CelticWarrior on 2020-02-03
In Rufus ISO mode you need to also select MBR/BIOS for your old machine.

---

### Post by migascool123 on 2020-02-04
> **CelticWarrior said:**
> In Rufus ISO mode you need to also select MBR/BIOS for your old machine.

Yes, I choose this options because they were the only ones that I can select

---

### Post by guiverc on 2020-02-04
I've a pentium 4 *heater* on besides me.  Spec wise I record it as
[I]hp dx6120mt (mini-tower, pentium 4 dual core, 3gb, winfast clone of nvidia 7600gt)
[/I]which I only semi-recently upgraded the RAM from 1.5 to 3gb. I have no idea what speed it is, I only record CPU, ram & GPU.

I'm using it for QA-testing (QA=*Quality Assurance*) Lubuntu 18.04.4 which is due for release on Thursday (6-Feb-2020; thus I'm somewhat busy & may not have noticed your prior reply). It's one of my test rigs that tested up to Lubuntu 19.04 (it's x86 only now; and this 18.04.4 release will likely be it's last use for QA-installs).

I can't speak to the various pentium 4's; I used to have a couple but kept this one as it used SATA & PATA drives.

Yes the alternate installer is very different; it uses the 'debian-installer' instead of Ubuntu's standard `ubiquity` installer; it's used to save RAM. The debian-installer was primarily used for installing on servers (which are text-mode only often), though may not be used for any 20.04 release.  The new 18.04.4 images do not include any 'di' or alternate images; alternate images aren't updated.

I have tested using many pentium M (2003-2005) laptops, and a few pentium 4 boxes (now only 1), but I haven't done any testing on any box with less than 1GB of ram in a long time.  Thus your situation in regards RAM I cannot advise on.  I'd be tempted to use something like 'openbox' or a simple window manager; though I realize this won't likely mean much to you.

---

### Post by migascool123 on 2020-02-04
Thanks your help @guiverc ! I know this could be a silly question, but if I buy a socket of RAM how can I verify if the socket is compatible with my sockets and motherboard? And how can I configure it in the BIOS?
How different is the installer of the Alternative version? It only have command line, right? I&#8217;ve researched on internet, but I didn&#8217;t found any video or site with a installation with alternative version, could you explain me how does it proceed?
P.S. - I&#8217;m a really beginner on the Linux world!!
Thanks for help!

---

### Post by CelticWarrior on 2020-02-04
Compatible RAM will be very hard to find and if you find one it'll be expensive comparatively.

You may check at the motherboard manufacturer's website for type a maximum RAM supported. Also stores like crucial.com and memoryc.com can help you.

But if you ask me it's a waste of money for littler to no gain.


EDIT:

If you can find RAM for that it'll probably be more expensive than a Raspberry Pi, a more capable little computer and way more energy efficient than your old machine. So, yes, some things are better left to retrocomputing enthusiasts or museums.

---

### Post by mörgæs on 2020-02-05
Please run ```
sudo lshw -C memory
``` and post the output in CODE tags. It will tell all we need to know about memory.

I expect that you will get extra memory modules cheap. High supply and low demand should give low prices.

---

### Post by migascool123 on 2020-02-06
Ok I will run that code! 
The installer of alternative version is intuitive or Do I have to deal with a line of code?
Thanks

---

### Post by CelticWarrior on 2020-02-06
> **migascool123 said:**
> The installer of alternative version is intuitive or Do I have to deal with a line of code?

The main difference is it hasn't a fancy GUI and at time you'll need to use the cursor keys, space bar and enter to navigate, select and apply options instead of mouse clicks. No commands are required though.

---

### Post by migascool123 on 2020-02-06
Thanks for awnser! When I try to install it I Update the thread!
Thanks for all who help me!

---

### Post by kevdog on 2020-02-06
I'll be the rude one here the forum -- 2003 device = Junk hardware.  Seriously you can get very cheap modern parts.  Don't waste your time what you're trying to do.  Even if you get things up and running the experience is going to be junk.

---

### Post by guiverc on 2020-02-06
My belated reply


I upgraded my RAM because in Dec-2018 x86 was finally dropped, so I started recycling some old boxes, some of the RAM I kept & was just sitting there - I re-discovered it & thus it was installed. Was I actually using the boxes I would have installed it much earlier, but for testing purposes I think the low ram could be a benefit for detecting issues users may encounter.  I wouldn't buy new, at recyclers they'd likely give it to you, or charge you maybe a dollar  (the recycler where I volunteered at was only interested in dealing with sticks of 2GB of more, we'd give away smaller; so 2x1gb [free] would still give you 2gb ram; we never tested ram we'd give away, so don't forget to memtest it yourself).


I only like providing official documentation in my answers, and sorry currently I don't have much with the debian installer. I only joined the Lubuntu team in the 18.10 cycle, which was after 18.04 and the creation of the last alternate CD so I never tested it.  I've used it heaps to install Debian, but never Lubuntu (*that I remember anyway*).  


I did find a *youtube* video on it (which looked okay the little I viewed, but without reviewing it I won't re-post). If you find documentation on it at *lubuntu.net* (**not an official Ubuntu/Lubuntu site**) I would trust it in this regards. The owner of that site was a co-creator of Lubuntu but has since left the project, so at least had some interest in the project years back, so whilst it's not up-to-date, the information you're after here doesn't need to be as *up-to-date* as it's *historical*.

---

### Post by migascool123 on 2020-02-14
Hi guys, I’ve already tested it on the pc, and there’s some evolution, but isn’t working yet! My trouble now, is after I choose the language of Lubuntu, in the menu that says: install Lubuntu, check disk, check memory,.... and when I click on install Lubuntu the screen freezes and does nothing! The only option that I can access is to check memory, that is ok! 
Does someone have an idea of what it could be?
Thanks!

---

### Post by mörgæs on 2020-02-15
Kevdog has a point. If you get a system running it will be slow, probably too slow for any practical use.

If you want to carry on anyway as a learning experience you could try Debian:
[https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890](https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890)

---

### Post by migascool123 on 2020-02-18
Yes you could have reason, the ram memory may not be enough to run the system. I will try raspberry pi for PC and Slax, these are the last tries! 
Thanks for help

---

