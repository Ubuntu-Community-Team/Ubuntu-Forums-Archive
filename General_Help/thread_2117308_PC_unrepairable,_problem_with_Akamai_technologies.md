---
title: "PC unrepairable, problem with Akamai technologies"
date: 2013-02-18
forum: General Help
---

### Post by fedine on 2013-02-18
Hello.

I have been using Ubuntu 12.04 for some time, since last May. I had also avast security, after clam-av, and chkrootkit on it, and was using regular ubuntu updates. 
It is just that beyond some point, it turned out it had been hooked up by fraudsters. One day I opened up the pc to see that I had at the boot option the options "previous linux versions" which included other versions of ubuntu, able to boot with different screen settings. By checking on the internet, I found out this is how you actually create a "honeypot", that is stealing and playing with somebody else's machine...whatever. It is certainly something I did not do myself.

Trying to update avast to find out what was going on was blocked and avast started running, initially going slowly and then very fast, obviously simply bypassing thousands or millions of files. Chkrootkit found nothing, or some minor problem that I do not even remember now what it was and certainly could not fix. Also, trying to install any new program was impossible, and even the new applications menu was showing up with irrelevant choices in the menus, meaning it was damaged.

Ok, then, I tried format with Ubuntu cd. One format, and on new installations I see an unknown (and unselected by me) program downloading from the internet, and I was unable to stop it by other means than switching off the internet connection. Since installing new programs and anything else was also impossible and untrusted, I tried a second format.

And here is what happened: I found myself with no option not only to INSTALL anything new, but even to BOOT from a LIVE-CD. That is, I put a new linux cd (ubuntu or other) in the tray, let it do its job and get the same infinite loop, some problem with IRQ, some lines I do not understand, and nothing else happening, no booting, nothing. And of course, the message may be tweaked and does not even have to provide any kind of real or useful piece of information on my machine.

How could this be happenng? Is there any way to recover my disks, when no linux (or even windows) OS can boot, not even live ones?


Also, I have been getting my connection redirected to Akamai Technologies, and in another pc (the one I am using right now) I have been seeing their name in the banner-blocking sections some tenths of time or more at a time. By a little check, they try to seem like a 'legitimate' company providing 'updates' for Windows and 'load balancing' for anyone asking for it. My question is where are our servers, pals? What are you doing in my pc, so many times, with no new programs, windows updates, or anything at all coming and going, but only some very basic browsing and offline work? How 'legitimate' could these people be?

---

### Post by dcstar on 2013-02-18
> **fedine said:**
> Hello.

I have been using Ubuntu 12.04 for some time, since last May. I had also avast security, after clam-av, and chkrootkit on it, and was using regular ubuntu updates. 
It is just that beyond some point, it turned out it had been hooked up by fraudsters. **One day I opened up the pc to see that I had at the boot option the options "previous linux versions" which included other versions of ubuntu, **able to boot with different screen settings. By checking on the internet, I found out this is how you actually create a "honeypot", that is stealing and playing with somebody else's machine...whatever. It is certainly something I did not do myself.
..........

All that is is the standard Grub boot menu that appears when you either press a particular key during boot or install another OS, it has **NOTHING** to do with any "Honeypot".

If your PC won't even boot from a CD then chances are you have a hardware issue, nothing more.

---

### Post by QIII on 2013-02-18
Akamai serves content to its customers, primarily advertising content.  It is perfectly legitimate.

[http://en.wikipedia.org/wiki/Akamai_Technologies](http://en.wikipedia.org/wiki/Akamai_Technologies)

If you have an ad blocker showing Akamai, then it is doing its job.

---

### Post by fedine on 2013-02-18
Well, I suppose simple booting is a normal thing, but what happened was that apart from the usual menus (I had Ubuntu 12.04 and winXP on the same machine), I got some "previous linux versions" when no previous linux versions were there installed by me. That is, there were some fake linux OSs there, with same appearance and different screen settings when booting on them. That is how people make honeypots, they create false images of OSs so that when someone gets in, they see so many things, they do not know what to do and they cannot do anything on that system, they are seen, but not able to be changing the system. Besides, the no-boot-from-live-cd problem appeared only after one format that enabled me to see an unknown program installed on a new machine with all clear, no hardware changed, nothing done on the machine. And before that, my pc was unable to install any new programs, so, it is obvious that this, too, cannot be a hardware problem but a machine badly tweaked. :)

Also, I found this about Akamai technologies [http://www.velocityreviews.com/forums/t306591-akamai-technologies.html](http://www.velocityreviews.com/forums/t306591-akamai-technologies.html), they seem to be creating problems to people with no reason, just getting in the middle of their connections. Could also involve doing any kind of illegal activity, like stealing data, internet connection etc., since it is obviously something that you cannot get rid of and that gets always in front you (I have been seen them for at least a year already without knowing of them before or needing/asking for any of their services).

---

### Post by sudodus on 2013-02-18
When a new linux kernel is ready it will be offered to install into your Ubuntu system. Then the previous kernel(s) will be available at boot (in the grub menu's previous versions submenu).

The reason they stay is that you might have some program that cannot run with the newest kernel, and you have the option to boot into the old kernel and run that program. After some time, when you know that everything works with the new kernel, you can remove the old one to save space on the hard disk using for example Ubuntu Tweak. If you don't remove old kernels there will be many of them occupying disk space. I usually keep the two newest kernels (the current one and one more) but I almost never need the old one.

---

### Post by fedine on 2013-02-18
So, you think that the 'previous linux versions' are older kernels? Which, by the way, I did not install myself on my machine, this is the problem. Also, each 'other version', was able to boot to a ubuntu OS, if chosen, and provide the same settings, files etc., only lower screen resolution, which I do not know why happened (of course, this is the least important).

In either case, whether they were older kernels or false images of my machine to fraud anyone seeing them, I did not put them there, and not only couldn't I remove them (apart from the part that there were many system files INACCESSIBLE to me even as root) or install anything new (which implies...what?), but I could also not even properly format my machine, since first time I did it an unknown program started downloading itself as soon as I connected to the internet, and second time no cd was able to boot at all, let alone install or play live, on my machine.

It seems that kernels is not the problem. It could be if I had done it myself, and upgraded my kernel, but I did not do that at all, and there is no legitimate reason to do it to somebody else's machine through the internet.

---

### Post by sudodus on 2013-02-18
What do you want? We, the guys who have replied in your thread are not worried by what you see. We see no sign of any corrupt data or any intrusion into the computer according to your description. On the contrary, getting new kernels is part of updating the operating system, where one important reason is to remove security holes as soon as they are discovered.

If you want help, please describe it with more details!
- Can you use the terminal window with command lines?
- Are there any particular programs you want to add or remove?
- Do you want detailed help to remove those old kernels?
- (Something else ...)

This link describes security issues in Ubuntu

[[COLOR="Red"]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by fedine on 2013-02-18
Well, perhaps I am not very clear on what has been going on.

I got to the GRUB loader, saw previous versions (all of them bootable) and left them there, but did not know how they occured. If by kernel updates, why does ubuntu keep them there? Besides, can an update (or many) give you a whole new 'Ubuntu version', still bootable? Why would it need to be there?

I tried to install new programs and even the available applications provided by Ubuntu were different (for example, books and magazines and some irrelevant small packages instead of normal programs). Besides, new installations were completely impossible. That.

I tried to format it and immediately got new **** auto-downloading itself.
I tried to re-format it and then, bloop! No OS at all, no live-linux, no installation.
As it is, it cannot read the cds, not boot frm hard disk, not run any live cd, nothing.

It does not seem something that could just be a result of usual ubuntu updates, and end up with a broken pc, could it? I mean, no OS can be installed now, there is nothing there.

---

### Post by Grenage on 2013-02-18
> **fedine said:**
> I got to the GRUB loader, saw previous versions (all of them bootable) and left them there, but did not know how they occured. If by kernel updates, why does ubuntu keep them there? Besides, can an update (or many) give you a whole new 'Ubuntu version', still bootable? Why would it need to be there?

Those are backups, and rather handy on the rare occasion things go south.  Most machines will have those.

> **fedine said:**
> I tried to install new programs and even the available applications provided by Ubuntu were different (for example, books and magazines and some irrelevant small packages instead of normal programs). Besides, new installations were completely impossible. That.

You will need to be specific.

> **fedine said:**
> I tried to format it and immediately got new **** auto-downloading itself.
I tried to re-format it and then, bloop! No OS at all, no live-linux, no installation.

If you formatted the machine, then nothing would 'auto-download' or boot, because there would be nothing to download, download to, or boot from.

> **fedine said:**
> As it is, it cannot read the cds, not boot frm hard disk, not run any live cd, nothing.

You probably have a defective CDROM, or a bad boot medium.

---

### Post by fedine on 2013-02-18
The cd-rom was the same I initially got, and the installation was working ok for some months.

I still cannot see any reason for ubuntu being so 'untidy', I mean, do you all get 'previous linux versions' as an option in your GRUB loader at start-up?
By saying "I could not install anything new" I mean exactly that, installation blocked few seconds after starting or not starting at all. And options of new programs not even normally appearing. I could do nothing in my own machine, this is what I am saying.
After the format, of course, I had a new and clear installation, or so I thought. Then tried to install a new program (I think it was skype), its installation was blocked few seconds after starting and an unknown program was downloading itself instead, which I tried to stop but that was impossible too. 

Problem is, I did not try one cd, but plenty, different OSs, all of them getting to the same loop, an irq problem related to reading hard disks, but I am free to suppose that the loop error messages could be false themselves, right? All cds tried were and are perfectably working cds, no problem with them.

---

### Post by sudodus on 2013-02-18
I think that you should run a live linux version, and not bother with any installation. There are several alternatives.

Knoppix [http://www.knopper.net/knoppix/index-en.html]("http://www.knopper.net/knoppix/index-en.html")

Tails [https://tails.boum.org/download/index.en.html]("https://tails.boum.org/download/index.en.html")

Webconverger [http://webconverger.com/]("http://webconverger.com/")

or Puppy Linux [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

When a new version is available you download it and make a new boot CD or USB drive, and you don't have to worry about more or less voluntary installation of software.

---

### Post by grahammechanical on 2013-02-18
> I still cannot see any reason for ubuntu being so 'untidy', I mean, do you all get 'previous linux versions' as an option in your GRUB loader at start-up?

Of course we do. You are worried about security. Are you not? Well what would you think of the developers if they did nothing about fixing security issues? Linux is under constant development. Hardware is being developed all the time. The Linux developers need to keep up with the latest hardware. The kernel is the small portion of code that everything else runs on. It must be kept up to date.

The first of these previous kernels was brought in when you first installed Ubuntu. From then onwards whenever the Linux developers released an update to the kernel the Ubuntu developers passed it on to us. And so we are kept secure. And that is the very thing that you are worried about.

There is a little bit of good news. Ubuntu 12.10 has an upgraded version of the Grub menu that should one day be put into 12.04. This newer version of the Grub menu puts all those pesky previous kernels into a sub-menu called Advanced Options for Ubuntu.

Regards.

---

### Post by fedine on 2013-02-19
I actually do not worry about kernel updates, although I thought that kernel updates are actually a special thing to do and it is not done automatically via the internet, but requires you to get a new kernel, get it to your system after having secured back-ups and get your system working with a new kernel. Perhaps I am not very well informed, I have never actually updated my kernel before, but I thought it cannot be done automatically anyway.    However, the 'previous linux versions' that I used to see are not necessarily different kernel versions, even if there are so many frequent kernel updates, I mean, there were at least 4-5 of them on my system, it is not something that just happens.    Still, my problem now is not 'linux versions' or new kernels, but a much different one. I tried to format my machine and the pc cannot even run a live cd with linux on it (or even windows for an installation), different linux distributions with perfectly working OSs tried many times. I get to an infinite loop that locks me out of my own system.   Does anyone know how this can be done?

---

### Post by eddier on 2013-02-19
You appear to be confusing a  Kernel update with a release update (e.g. ubuntu 12.04 to ubuntu 12.10)-this is not the case.

Between Ubuntu 12.04 and Ubuntu 12.10 there were several Kernel updates.

The kernel is in a constant state of change with improvements,additions and in some cases removal of obsolete code.

edie

---

### Post by kurt18947 on 2013-02-19
> **fedine said:**
> 

.............

 Still, my problem now is not 'linux versions' or new kernels, but a much different one. I tried to format my machine and the pc cannot even run a live cd with linux on it (or even windows for an installation), different linux distributions with perfectly working OSs tried many times. I get to an infinite loop that locks me out of my own system.   Does anyone know how this can be done?

I think I know what you're seeing, I've seen it myself on an old PIII laptop.  Are the lines of text scrolling by mentioning sr0 and not being able to read block  xxxxx or similar?  Thinking it was a bad CD,  I put that CD in a different machine and it reads perfectly.  I suspect you have an issue with an incompatibility between that one CD drive and your CDs.  It may have to do with the way CD-Rs are written or the way the ISO was built, I'm not sure.  I had an awful time trying to install Lubuntu on this one particular machine due to CD reading issues but Xubuntu installed fine.  It had nothing to do with any malware or hijacking or any of that.  We have been conditioned to blame any malfunction on somebody being out to get us.  Sometimes the explanation is much simpler, it's a hardware/software glitch.

---

### Post by sudodus on 2013-02-19
> **fedine said:**
> ... I tried to format my machine and the pc cannot even run a live cd with linux on it (or even windows for an installation), different linux distributions with perfectly working OSs tried many times. I get to an infinite loop that locks me out of my own system.   Does anyone know how this can be done?
I makes it easier for us to help, if you describe your machine, at least cpu, ram, graphics card/chip, wifi card/chip (if any). So please let us know :-)

---

### Post by fedine on 2013-02-20
I can only wish it were as simple as a hardware issue. 
But I have been using different cds, including windows cds, together with linux cds, even ones not created by me but bought by others, and perfectably working cds. It is that they all start working and then fall into the same loop. No sr0, nothing, or at least I do not remember anything like that. Besides, what is the probability that you have serious security issues in a machine (like no new installations allowed by you, programs unknown to you auto-donwloading themselves etc.) to the point that you have to format your machine and then, all-of-a-sudden, an 'unexpected' hardware issue appears?

No, it is not a hardware problem, with probability less than zero in infinite. :) 
And it seems it is totally unheard of in general. I mean, we talk about totally different things here, see? No kernel updates, no problem cds, nothing. These are trivial and custom, easily by-passed, but provide no clue to what has happened or what to do. :|

---

### Post by sudodus on 2013-02-20
If your computer won't boot from a good CD now, but used to do it earlier, there are only two alternatives.

1. You have changed something in the startup system (BIOS/UEFI).

2. Something has broken in the computer.

I don't think any internal malware is active, when you boot from a boot CD. There might be compatibility issues, some boot CDs won't work with some computers (and you may forget, which CD or computer you were using last time, when it worked).

If you want help, it makes it easier if you tell us some basic facts about your computer, to help us see if there might be something, that makes it difficult with Ubuntu 12.04: cpu, ram, graphics card/chip. If there are some other observations or facts, that might help us understand the problem (other than what you already described), please let us know.

"A good description of the problem is almost a solution"

---

### Post by fedine on 2013-02-20
It is an old pc, like constructed in 2004-05, Pentium 4, or so I think. P5GD2 deluxe mobo, nvidia graphics card with 256Mb RAM of its own, 1,5Gb memory modules (DDR2) (NOTE: before the formats, the memory check option at the GRUB loader provided me with false information on the memory that was hooked on the machine, that was easy to prove wrong when used a live linux cd later without formatting a did an original memory check with that). BIOS never updated all that time, I downloaded the latest version from the internet but hesitated, as I am not sure this is the problem and it could be a fatally wrong movement if (a) was done wrong or (b) was not involved in the problem that appeared, but further got it more perplex. 

So, I got in May 2012 the Ubuntu 12.04 OS, burnt it to a cd and all happy got it to work and did so for months. No problem, Ubuntu was there, cd was fine. Same cd used later for some partition re-creation, re-installation etc., but minor issues, just to play with my files and disk usage, no real problem there.

And then I got to the security problems, when pc stopped working altogether. Tried Ubuntu cd, same cd, once or twice to format the machine, I got it unable to see the disks. Some time later, it saw them and all was fine. But when I got to the internet, problems re-appeared and I decided to re-format. And that was it, Ubuntu was unable to install and every other cd I tried got stuck to the same loop, an irq#5 problem with IDE disk recognition and some other lines I do not remember, but a loop anyway.

As a matter of fact, as I write these lines, I actually think it CAN be a hardware problem, related with hard drive recognition, but two disks? A mobo problem maybe? Cos, first time I tried to format, it was unable to see my disks, but I got to the installation menu, where it says available space for installation and internet connection for updates etc., second time stuck to the loop, that I think means "unable to see hard disks". Could also be a bad cable connection on my part, I have to check that.

---

### Post by sudodus on 2013-02-20
> **fedine said:**
> ...

And then I got to the security problems, when pc stopped working altogether. Tried Ubuntu cd, same cd, once or twice to format the machine, I got it unable to see the disks. Some time later, it saw them and all was fine. But when I got to the internet, problems re-appeared and I decided to re-format. And that was it, Ubuntu was unable to install and every other cd I tried got stuck to the same loop, an irq#5 problem with IDE disk recognition and some other lines I do not remember, but a loop anyway.

As a matter of fact, as I write these lines, I actually think it CAN be a hardware problem, related with hard drive recognition, but two disks? A mobo problem maybe? Cos, first time I tried to format, it was unable to see my disks, but I got to the installation menu, where it says available space for installation and internet connection for updates etc., second time stuck to the loop, that I think means "unable to see hard disks". Could also be a bad cable connection on my part, I have to check that.

It looks like failing hardware. It is too early to tell where, but you can 'wiggle' the cables to the hard disks, the RAM cards and any PCI card (graphics etc). You can also try to get rid of dust, because that can cause too high temperature. Also check, that all the fans are running!

Another option is to try another CD, or another HDD, if you have spare parts.

Yes, it might be a mobo or processor problem, but with a little bit of luck, you might get your old companion up and running again :-)

***Edit***: If you have more than one RAM card, test them one at a time with memtest at the early screen of the Ubuntu boot disk.

---

### Post by kurt18947 on 2013-02-20
I've had drive controller problems, both IDE and SATA so yes, that's a possibility.  Especially with the mention of an IRQ address.  Older machines like older people have more glitches.

---

### Post by Habitual on 2013-02-20
> **fedine said:**
> Problem is, I did not try one cd, but plenty, different OSs, all of them getting to the same loop, an irq problem related to reading hard disks, but I am free to suppose that the loop error messages could be false themselves, right? All cds tried were and are perfectably working cds, no problem with them.All on the same CDRom device? You tried these on different computers? If they work elsewhere but not the affected system, you have a CDRom hardware issue, Period. IRQs? How can "same loop"s be a "false" anything?

"different OSs" doesn't say very much.
It very well could be a bad md5sum that somehow managed to install anyway...

[http://goo.gl/Rims](http://goo.gl/Rims)

OTOH: +2 for correct spelling of OSs and CDs!!! ;)

---

