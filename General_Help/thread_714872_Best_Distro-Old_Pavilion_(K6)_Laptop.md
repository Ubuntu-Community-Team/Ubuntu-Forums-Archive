---
title: "Best Distro-Old Pavilion (K6) Laptop"
date: 2008-03-04
forum: General Help
---

### Post by Ian-on-the-Trent on 2008-03-04
G'day all.

I'm trying to resurrect a HP N3478 Pavilion:
[INDENT][LIST]
[*]K6 (550mhz)
[*]196MB RAM
[*]6GB HDD.
[/LIST][/INDENT]
Microsoft ME was on it and my friend who owns the laptop said it was very unstable, quirky, and froze up a lot. DOH!

As I type this, I'm trying to install Zenwalk but am encountering all sorts of errors. The install continues with the caveat that the installation may not work. (Many, many fatal errors.)

I tried installing Ubuntu 7.04, 6.10, 6.06 but to no avail. Errors stating the disk couldn't be read. If memory serves me correct, I had a similar experience when I tried to install the above flavours of Ubuntu on an old Acer Travelmate 213T. Sadly, I ended up reinstalling XP on the laptop (it's slow but works like a charm.)

If possible, I really would prefer to install a flavour of Ubuntu largely because it's quite managable for a newbie (the owner). I'd call myself a post-newbie since I can plunge into things with a CLI.

Anyhow, I just stopped the Zenwalk install...too many errors. I'm now rebooting with a WIn98 disk to at least partition and reformat the HDD.

Does anyone have any experience installing a distro on a laptop like this? What are your recommendations. The owner is not looking for a project, this will basically be used tfor email, browsing, and wordprocessing.

Cheers.


-----------------------------------------------------------------------------
I have referred to: [http://ubuntuforums.org/showthread.php?t=435825](http://ubuntuforums.org/showthread.php?t=435825)

---

### Post by Fixman on 2008-03-04
> **Ian-on-the-Trent said:**
> G'day all.

I'm trying to resurrect a HP N3478 Pavilion:
[INDENT][LIST]
[*]K6 (550mhz)
[*]196MB RAM
[*]6GB HDD.
[/LIST][/INDENT]


If you have a good internet connection, I would reccommend you [Xubuntu]("http://www.xubuntu.org/get"), else you could try with [Puppy Linux]("http://www.puppylinux.org/user/downloads.php").

---

### Post by Ian-on-the-Trent on 2008-03-04
Xubuntu: download and burn an image?

What sort of systems resources does Xubuntu require? Can you still use firefox, openoffice etc?

---

### Post by Fixman on 2008-03-04
> **Ian-on-the-Trent said:**
> Xubuntu: download and burn an image?

What sort of systems resources does Xubuntu require? Can you still use firefox, openoffice etc?

You can use any Linux program, and has the same packages that Ubuntu.

---

### Post by Ian-on-the-Trent on 2008-03-04
Okee dokee. Downloading an image...1:06:57 to go. I'll keep you posted ;)

---

### Post by empthollow on 2008-03-04
> **Ian-on-the-Trent said:**
> Xubuntu: download and burn an image?

What sort of systems resources does Xubuntu require? Can you still use firefox, openoffice etc?

yep you can download and burn and image of xubuntu.  the system requirements are low, it is intended for older systems and is also user friendly as it uses the XFCE desktop.  and yes you can use firefox and openoffice.  In fact any app that you can use in the standard ubuntu distro is installable on xubuntu.

---

### Post by {BzF}~JOKesTER on 2008-03-04
Personally I Would Use Puppy Linux,

Puppy Linux Loads The Entire OS Into Ram On System Boot - Which Results In Huge Performance Gains - Especially In Older Systems - However In Order To Run Puppy Linux You May Have To Upgrade Your Physical RAM To About 512mb - To 1GB.

---

### Post by {BzF}~JOKesTER on 2008-03-04
OH I Almost Forgot!!!

Another Good Reason To Use Puppy Linux Over Another OS IS That You Only Have A 6GB Harddisk
Which Means You Will Run Out Disk Space Very Quickly - But In The Case Of Puppy Linux It's In RAM 
So There's No Need To Fret.

Another Thing - Older Hard disks Run Notoriously Slow - Meaning That If The OS Was On The HD It Will Run Extremely Slow.

---

### Post by Ian-on-the-Trent on 2008-03-04
I understand the speed issue vis a vis storing OS in RAM instead of retrieving it from old HDD. The only thing is the 196mb RAM in this puppy ain't gonna change. But that kernel of advice has been stored in my old RAM (the unit above my shoulders.) :)

---

### Post by Ian-on-the-Trent on 2008-03-04
A follow-up question:

I'm going to try installing Xubuntu 7.10 first. Is the following partition reasonable?
2.5gb - /
0.3gb - /swap
3.2gb - /home

---

### Post by Jerry N on 2008-03-04
On an old slow processor I have found that Xubuntu 6.06 provides much better performance than Xubuntu 7.10  or LinuxMint Fluxbox.  You could also try PCFluxBoxOS Tiny.  I have not yet been able to get a printer running in Xubuntu 6.06 and what little I have been able to dig up indicates that this is not an uncommon problem.  

I would expect DamnSmallLinux and Puppy Linux to both work OK on your machine although I am not sure about installing a printer with Puppy Linux - it uses that online CUPS thing.  

Jerry

---

### Post by Fixman on 2008-03-04
> **Ian-on-the-Trent said:**
> A follow-up question:

I'm going to try installing Xubuntu 7.10 first. Is the following partition reasonable?
2.5gb - /
0.3gb - /swap
3.2gb - /home

Unless you will change soon the OS, I recommend you to put / and /home together, and give swap at least 0.5 GB.

---

### Post by Ian-on-the-Trent on 2008-03-04
While I was waiting for the download of Xubuntu to finish I tried installing a public distribution of 5.10.  That also had a tremendous number of errors.  Could it be the HDD or other device.? Undertaking some basic diagnostics now.

---

### Post by eriqjaffe on 2008-03-04
BTW, you won't be able to install off the regular Xubuntu CD on only 192MB of RAM, you'll need the Alternate Install CD.

---

### Post by Ian-on-the-Trent on 2008-03-04
The info on the Xubuntu website said 128Mb RAM minimum. Is their claim hopeful?

---

### Post by Jerry N on 2008-03-04
I forgot to mention that when I installed XUBUNTU 6.06 on an old slow machine I used the alternate install disk.  It installed in about 1/4 the time required for XUBUNTU 7.10 (also alternate install disk).

It is sounding like you may have some serious hardware problems.  Maybe that was why WinME wasn't working right?  Of course with WinME, how do you really ever know if it is working right.  Kind of like the Chevy Vega or Ford Pinto of operating systems.

Jerry

---

### Post by Ian-on-the-Trent on 2008-03-04
Okay:
[LIST=1]
[*]FDISK the HDD and then reformatted to Fat32 
[*]Booted using WIn98 boot disk. Ran Hard Disk Mechanic Gold on drive. No errors.
[*]Rebooted using fresh Xubuntu 7.04 disk. Menu popped up, selected the usual, install started.
[*]Installation crashed 30 seconds later. Couldn't boot because of "I/O disk error.
[*]Tried again (twice) only this time a message regarding "checksum....sorry."
[*]Rebooted working box with Xubuntu CD, ran "check cd for defects"--no errors.
[*]Tried rebooting old laptop with Xubuntu CD but now getting "system errors". Is the CD/DVD pooched?
[*]Rebooted using Win98 boot disk. C: is empty hard drive, D: is ramdrive, and look, E: is the disk with Xubuntu on it and I can see the files/directories.
[/LIST]

What the heck is going on?  Can an installation be made from the HDD using files copied from Xubuntu (copied to a separate disk partition)?

---

### Post by Ian-on-the-Trent on 2008-03-04
> **Fixman said:**
> Unless you will change soon the OS, I recommend you to put / and /home together, and give swap at least 0.5 GB.

Actually, I was assuming that the distro might change hence I wanted to keep /home on a separate partition. Swap = 500mb.  2.5x RAM?  Is this correct?

---

### Post by Jerry N on 2008-03-04
Would you happen to have a Windows 95 or 98 full install CD you could try?  If you were able to install 95 or 98 that might tell you that there is something about the system that the Linux kernel doesn't like.  Have you been able to get a Linux Live CD to boot up?  A Live CD should boot in spite of problems with the HD but if it won't boot then something else is wrong.  Puppy, DSL, Gparted, and Knoppix all run as live CDs.  Knoppix with a 2.6 Kernel boots on the old AMD 300mhz K6 I have been playing with.  DSL uses a smaller older 2.4 kernel.

Jerry

---

### Post by Ian-on-the-Trent on 2008-03-04
Yes, I have Win98 disks and an Ubuntu 5.10 Live CD.  Thanks for your suggestion, I will try these now.

---

### Post by kerry_s on 2008-03-04
dude, ubuntu does not actually support the old stuff, they drop all the older drivers needed, for space. you should go for straight debian which do support old systems from the 90's.
here's the xfce4 iso, like xubuntu without the bloat.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

a custom install is actually the best, when it comes to low end systems.
i run a debian custom on 450mhz 256mb ram laptop from the late 90's. i use the net installer to install the base.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

that means when it gets to package selection i uncheck both.
after it's finished and ejects the disk and reboots.

i log in as root
apt-get install xorg what-ever-else

xorg is the X system or gui, you will need a wm to go with that. a common light 1 is fluxbox.
example:
apt-get install xorg gdm fluxbox rox-filer leafpad synaptic
reboot(ctrl+alt+delete)

log in as your user, open synaptic and continue getting what you want.

going custom you only install what you actually use, you pick what's installed, so it's up to you what fast and light programs you want.

i use jwm for my builds, that's the wm i prefer. pic->

---

### Post by Ian-on-the-Trent on 2008-03-04
Wow...I have to figure out half of what you said ;) I'm still pretty new at this.

---

### Post by Ian-on-the-Trent on 2008-03-04
> **kerry_s said:**
> ...
i use jwm for my builds, that's the wm i prefer. pic->

Okay, I understand what you're suggesting...I don't know what *jwm* is though. Nice desktop pics. 

[INDENT][INDENT][COLOR="DimGray"]*This is turning out to be a time consuming project. I was swapping my time for my friends home-smoked ham.  If I keep going the way I am, I'll end up with the entire hog.  Now that's not a bad thought.*[/COLOR][/INDENT][/INDENT]

---

### Post by Jerry N on 2008-03-04
> **kerry_s said:**
> dude, ubuntu does not actually support the old stuff, they drop all the older drivers needed, for space. 


I can get LinuxMint Fluxbox  and Xubuntu 7.10 to install and work on my old 300mhz K6 but they are slower than the seven year itch.  Xubuntu 6.06 works fairly well but I can't make it print.  Right this minute the old computer is running Knoppix 5.1 (Live CD) which is pretty slow but I did get it to run my Laserjet across the network.  I think I will try it in the "frugal install" mode where it just copies the CD to the HD, like you can do with Puppy and DSL.  

Jerry

---

### Post by kerry_s on 2008-03-04
> **Jerry N said:**
> I can get LinuxMint Fluxbox  and Xubuntu 7.10 to install and work on my old 300mhz K6 but they are slower than the seven year itch.  Xubuntu 6.06 works fairly well but I can't make it print.  Right this minute the old computer is running Knoppix 5.1 (Live CD) which is pretty slow but I did get it to run my Laserjet across the network.  I think I will try it in the "frugal install" mode where it just copies the CD to the HD, like you can do with Puppy and DSL.  

Jerry


jerry, try straight debian, you can see and feel the difference. if you go custom, it's even better, cause you decide how you want it.

---

### Post by MONODA on 2008-03-04
hmmm why dont you switch the sizes for /home and / ot just merge them

---

### Post by Ian-on-the-Trent on 2008-03-04
> **kerry_s said:**
> i run a debian custom on 450mhz 256mb ram laptop from the late 90's. i use the net installer to install the base.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

What is a net installer?

---

### Post by Ian-on-the-Trent on 2008-03-04
> **Jerry N said:**
> ...Have you been able to get a Linux Live CD to boot up?  A Live CD should boot in spite of problems with the HD but if it won't boot then something else is wrong. 

Jerry

Yes Jerry, I can boot from Ubuntu Live 5.10 CD. It's very slow mind you, but it has booted.  So I guess the DVD/CD drive is fine.  This laptop just doesn't want to install.

---

### Post by eriqjaffe on 2008-03-04
> **Ian-on-the-Trent said:**
> The info on the Xubuntu website said 128Mb RAM minimum. Is their claim hopeful?Xubuntu will run on 128mb of RAM (I've done it myself), but the LiveCD-based installer requires 256mb.  For low-memory installations, you can use the alternate CD.

A couple of other people have mentioned it, too, but you may want to go with a ground-up install, adding only what is needed to help keep the system fairly lean, especially with 128mb of RAM.

---

### Post by tdrusk on 2008-03-04
> **Ian-on-the-Trent said:**
> A follow-up question:

I'm going to try installing Xubuntu 7.10 first. Is the following partition reasonable?
2.5gb - /
0.3gb - /swap
3.2gb - /home

give the swap some more. .5 at least

---

### Post by Ian-on-the-Trent on 2008-03-04
> **kerry_s said:**
> 
a custom install is actually the best, when it comes to low end systems.
i run a debian custom on 450mhz 256mb ram laptop from the late 90's. i use the net installer to install the base.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)


Okay, downloading the netinstaller . I'll hopefully report back sometime tonight.

Until then, thanks all.  TTYS

---

### Post by Ian-on-the-Trent on 2008-03-04
Can you give "thanks" to more than one person?

---

### Post by kerry_s on 2008-03-04
> **Ian-on-the-Trent said:**
> Can you give "thanks" to more than one person?

of course you can.

the net installer installs from the internet, so you can get the latest stuff on a fresh install or you can do custom installs using it to only install the base system, then installing what ever you want on that.

a straight install of the net installer will give you gnome, like ubuntu with out the bloat.

for example with that disk you can install all versions of debian.
examples:

kde version,like kubuntu>
base install
apt-get install xorg synaptic kdm kdebase
reboot (press> ctrl+alt+delete)

xfce4 version, like xubuntu>
base install
apt-get install xorg synaptic gdm xfce4 iceweasel
reboot (press> ctrl+alt+delete)

fluxbox version, like fluxbuntu>
base install
apt-get install xorg synaptic gdm fluxbox rox-filer leafpad iceweasel
reboot (press> ctrl+alt+delete)

icewm version, like ubuntu lite>
base install
apt-get install xorg synaptic gdm icewm rox-filer leafpad iceweasel
reboot (press> ctrl+alt+delete)

etc...

the list go's on, the net installer is best if you want things your way. :)

---

### Post by Ian-on-the-Trent on 2008-03-04
This is confusing:
[LIST=1]
[*]Downloaded and burned the suggested netinstall image. Data verified correct.
[*]Cleaned lens of DVD/CD drive
[*]Started installation. It gets to a point just past analyzing hardware when an error message reports that an installation file cannot be installed and the message suggests to check the CD or drive for integrity.
[*]Hard boot.
[*]Repeated the above. Installation fails at the same point.
[*]Tried installing Xubuntu (first time after cleaning the lens). Installation fails, I/O Error on boot disk.
[*]Started installation of Win98SE.  Completed without any errors or hiccups (other than for some add-on peripheral drivers I didn't have the disks for).
[/LIST]

Summary of many attempts and time spent trying to get a Linux distro installed on the old laptop:
[LIST]
[*]Boots and runs like a very slow charm using the Ubuntu 5.10 live cd.
[*]Zenwalk 4.2, Xubuntu 7.10, Ubuntu 5.10, 6.06, 6.10, 7.04, Debian Netinstall failed.
[*]Win98SE installed without issues.
[*]Microsoft 1 -- Linux 0
[/LIST]

Any other thoughts or suggestions?

---

### Post by Ian-on-the-Trent on 2008-03-04
Just for a lark, I tried installing XP-Pro. No luck, many files weren't being installed/verified so I canceled the installation,

Now this is the weird part: one could easily say that there must be a hardware issue. Perhaps, but why did Win 98se install? Very strange.

---

### Post by empthollow on 2008-03-04
My first inclination is the hard drive but i had a computer where i tried to install an os multiple times with similar results as you and it was the processor that was bad.  I would suggest swaping the processor although it is probably not likely you have an extra k6 laying around so maybe swaping the hard drive is in order.  I would say if you can boot a live cd it is probably not the processor but there are already so few live cds that will run with that amount of ram and the processor may react differently to a live cd.  when my processor went bad i was able to run the windows installer fine but it would come up with corrupt file errors every time and in different spots of the installation.

---

### Post by CREEPING DEATH on 2008-03-05
If is was MS-WIN on it just got here:  [Goodbye Microsoft!]("http://goodbye-microsoft.com/")
It'll make the MS-WIN machine dual-boot, offering MS-WIN and the Debian Installer.  Boot into the Debian installer and either use the XFCE cheat code (I don't remember it off hand) or just install a CLI system, reboot, and 
```
#aptitude install xorg
#aptitude install xfce4 gdm synaptic
```
and go from there.
**Or** just install the full Desktop system, those specs will actually run Gnome on Debian.  You can install XFCE from Synaptic later and remove Gnome if you so desire.  XFCE is light and rather useful.
Any CD-ROM issues are negated by the use entirely of a network installer.
Use the Xubuntu disk to run Memtest for at least 1 full cycle first, to make sure the RAM isn't bad.

CD

---

### Post by K.Mandla on 2008-03-05
kerry_s's advice is very good; I would suggest either a command-line installation of Ubuntu or Debian, or perhaps something a little more daring. 

I have (access to) an old K6-2 450Mhz that I occasionally use for testing and experimentation. I've put about [10 or 12 different distros on there]("http://kmandla.wordpress.com/2007/09/03/meet-the-little-laptop-that-could/"), and tried to evaluate them fairly ( :roll: ). 

[Best results]("http://kmandla.wordpress.com/2008/01/05/video-25-second-boot-on-450mhz-k6-2/") were with Crux Linux, but it also definitely had the steepest learning curve. I don't recommend it unless you're accustomed to fixing systems at the code level. You must compile for that one.

But the tradeoff is astounding. Short of that, a simplified Debian or Ubuntu system should do the trick.

---

### Post by Ian-on-the-Trent on 2008-03-05
Wow...more great suggestions! Thanks all.

Beside trying to get some work accomplished (ya know the type that pays the bills) I've taken Creeping Death's suggestion to run a memory test and that is currently underway.  I'll try other suggestions after this one is completed.

Maybe the recycle bin is just around the corner....

---

### Post by Ian-on-the-Trent on 2008-03-05
> **K.Mandla said:**
> ...

[Best results]("http://kmandla.wordpress.com/2008/01/05/video-25-second-boot-on-450mhz-k6-2/") were with Crux Linux, but it also definitely had the steepest learning curve. I don't recommend it unless you're accustomed to fixing systems at the code level. You must compile for that one.

Phew...way beyond my knowledge and comfort level.

Would you know of a hard drive diagnostic tool. (I successfully ran Hard Disk Mechanic Gold but this software is fairly ancient.)  The hard drive is a Toshiba and unlike, say Western Digital, they don't offer any floppy-based diagnostic utilities.

---

### Post by Jerry N on 2008-03-05
For disk diagnostics I use Spinrite from Gibson Research ([www.grc.com](www.grc.com)) but the price is up to $89 now - probably more than your old computer is worth.  (I have 4 circa 1998 computers here all in running condition that I would just love to sell for $89 each.)  

For comprehensive memory tests you could try Knoppix if it will load (it runs as a live CD, like the Ubuntu 5.10 that you have been successful with but probably much slower).  I don't know if Knoppix has disk diagnostics or not.  It runs on my old K6 300mhz with 256mb RAM and it was a cinch to get a networked printer running.

I have tried a bunch of different Linux distributions on my old machines and have come to the conclusion that if the machine will be used stand-alone, ie no internet connection, Windows 98SE works best.  

Jerry

---

### Post by Ian-on-the-Trent on 2008-03-05
> **CREEPING DEATH said:**
> 
Use the Xubuntu disk to run Memtest for at least 1 full cycle first, to make sure the RAM isn't bad.


Ran memtest 3x from 6.06 disk (Xubuntu cd gave I/O boot error). No problems with RAM.

Contemplating next steps.

---

### Post by Ian-on-the-Trent on 2008-03-05
Well, I've had enough. Since it was to be a relatively small project for a friend the time I've been spending on it is crazy. In retrospect, I'm leaning heavily towards a wonky HDD that might be the culprit in the odd behaviour. Unfortunately, I don't have a working spare 2.5" drive.

Thanks to all for your help.  I've learned so much about other distributions. I have some other old boxes I'll now attempt to resurrect based on this knowledge.

Cheers,
Ian.

:popcorn:

---

### Post by Ian-on-the-Trent on 2008-03-05
> **Jerry N said:**
>  ... For disk diagnostics I use Spinrite from Gibson Research ...
Jerry


Although I've known about Spinrite for years, I've never used it nor met anyone who has.  Do you find it very effective?

---

### Post by Jerry N on 2008-03-05
> **Ian-on-the-Trent said:**
> Although I've known about Spinrite for years, I've never used it nor met anyone who has.  Do you find it very effective?

I have been using it since the early 90s but I used it a lot more back then than I do now.  It has multiple levels of testing and will try to repair bad sectors and return them to use.  With the hard drives we have now, the deepest level of testing can take a **LONG** time.  It's a great tool but I find that I need it very rarely now and most computer users would never find a need for it.  At the current Spinrite price of $89, you can buy a nice big new hard drive!

Back in the days of MFM and RLL drives, Spinrite was really great for optimizing a drive's interleave for best performance.  Been a long long time since I have had to do that!

Jerry

---

### Post by Caraibes on 2008-03-05
For older hardware, you should try Absolute:
[http://www.pcbypaul.com/absolute/](http://www.pcbypaul.com/absolute/)

---

### Post by Jerry N on 2008-03-05
> **Caraibes said:**
> For older hardware, you should try Absolute:
[http://www.pcbypaul.com/absolute/](http://www.pcbypaul.com/absolute/)

Downloaded it and tried to install it a few minutes ago - I got a message that my CPU is missing something and that I need to try a different kernel.  This is on an old Aptiva 300mhz K6 and I got that message on something else I was trying the other day although.  The Gparted and System Restore disks might have had a similar problem - they just stopped during the loading process.  Most distributions work though, many of them quite slowly.  Right now I am playing with Ubuntu 6.06.1.  Openoffice is intolerable but Abiword works fairly well.  I am going to try Dillo because it is much lighter than Firefox.

It is not really important that I make this old computer work with a Linux distribution.  I am just doing it to see if I can.   Ubuntu 6.06 saw the other computers on the network, a WinXP machine and a LinuxMint machine, right away as well as printing to the Laserjet shared on the WinXP machine.

Jerry

---

### Post by empthollow on 2008-03-05
you could try epiphany if dillo doesn't work out. it's the gnome web browser based on mozilla. i use it as my backup, it seems pretty light weight, i hear opera works pretty well too.

---

### Post by Caraibes on 2008-03-06
Then you could also try AntiX Mepis:
[http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)
But I think you would need an older version for a K6... Such as AntiX 6.5...

If not, you could try Fluxbuntu...

Or simply a "netinst" iso of Debian, and then add what you need (or a server iso of Ubuntu...)

---

### Post by eriqjaffe on 2008-03-06
> **empthollow said:**
> you could try epiphany if dillo doesn't work out. it's the gnome web browser based on mozilla. i use it as my backup, it seems pretty light weight, i hear opera works pretty well too.I recently tried out Opera 9.5b and have found it to be the fastest browser I've come across.  Well, the fastest **full-fledged** browser, I'm not considering uber-lightweights like Dillo and Links.  ;)

I had been using Kazehakase, but I just find Opera to be more capable and polished - that's not a surprise considering their relative ages and status, but I've been pleasantly surprised with how well Opera performs on my old clunker (366mhz Pentium 2, 128mb RAM).

---

