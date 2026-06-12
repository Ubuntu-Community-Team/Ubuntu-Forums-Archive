---
title: "Is it just me, or is Edgy the worst Ubuntu release ever?"
date: 2006-10-28
forum: General Help
---

### Post by qkmbr22 on 2006-10-28
Well let me start by saying that the upgrade from 6.06 completely failed, even though my 6.06 installation was fairly fresh and almost completely unmodified from the original install. It screwed up that installation, so i decided to just burn a copy of Edgy to a CD and install a clean copy.

Edgy doesn't display any boot up screen at all. I turn on my computer and for about a minute I see nothing. Then I see the login screen. The shutdown screen is blank too. What's up with that?

Also, Edgy randomly turns off my computer. After about 10-15 minutes of being on, my computer just turns off. Can't get anything setup either, because a package manager would be installing all the software I need and my computer would just turn off in the middle of it. I turn it back on, and it's like I haven't even done anything.

I didn't expect Edgy to be as stable as Dapper (which is the long term support version), but its just unusable. Aside from the few problems I described, I didn't find anything wrong with Edgy, but these few problems make Edgy 100% crap.

So is it just me, or what?

If anyone has any suggestions why my system is so messed up here's what i'm running: Emachines T1742 tower PC, 1.7 GHz Intel Celeron, 640 MB RAM, 48 MB shared video RAM, 40 GB HD, Dual boot windows XP home. Pretty old and crappy computer, but didn't bother Dapper at all.

---

### Post by Sethro on 2006-10-28
Its just you , mine is great

---

### Post by aysiu on 2006-10-28
Mine is also great.

---

### Post by ~LoKe on 2006-10-28
Mine has been perfect, even during the Knot testing.

---

### Post by moeFinley on 2006-10-28
Overheating? :-k

---

### Post by ejket on 2006-10-28
Mine is also great.  Edgy has even lured me away from debian etch, and I'm an old debian user.

---

### Post by DaveBorealis on 2006-10-28
> **qkmbr22 said:**
> After about 10-15 minutes of being on, my computer just turns off.

Edgy seems to have problems with certain hardware, and it might be part of your problem, but the fact that your computer powers down on its own could be a symptom of major hardware failure unrelated to the OS.

Have you tried looking in '/var/logs'?  Try dmesg, messages, and syslog for clues as to what's going on with the shutdown.

Best regards,
Dave

---

### Post by kerry_s on 2006-10-28
I think the installer is a little buggy, you can use the alternate cd and do a server install than grab the desktop(ubuntu-desktop,kubuntu-desktop,xubutu-desktop) or you can go custom. I haven't had problems with the server install.

---

### Post by d3v1ant_0n3 on 2006-10-28
Mine's been wonderful. Why are so many people having such problems??

---

### Post by taurus on 2006-10-28
I wiped out my Dapper (after a backup, of course) and installed Edgy using the alternate CD on one of my computers in the office early this afternoon and the thing works great!!!  Managed to download a few things with aptitude and will do some more on Monday when I get back in the office.

---

### Post by ianmacgregor on 2006-10-28
I have noticed, from these forums and #ubuntu on freenode, that if you upgrade via apt-get dis-upgrade then there can be problems. However, I don't do this. I always install from the CD media and my Edgy is working great. The only problem I have seen is that nautilus uses 98% of the CPU when I am working with video files. Otherwise, I like it better than Dapper.

---

### Post by moffa on 2006-10-28
It really sucks for me as well.  I am having problems with Firefox and sound, the generic kernel, gaming is constantly crashing, limewire doesn't work anymore.  Maybe Dapper spoiled me, it was really stable.  I just wish I knew how to troubleshoot so I could fix these things.

---

### Post by autocrosser on 2006-10-28
Yes--The recommended way to update is to use Update Manager--I've heard of problems with apt-get & aptitude--I've been using Edgy from Knot 1 & outside of a few problems I had during the generic kernel changes---It works VERY well for me--

---

### Post by Tux Aubrey on 2006-10-28
Mixed results for me.  Upgrades didn't work at all - either via Update Manager or apt-get.  Three clean installs of RC1 went very well, although the newer, high end machine still has a few problems booting (WiFi and the SATA controller?).  Otherwise, it seems very stable and fast.

---

### Post by handy on 2006-10-28
Great for me except for 1 niggling keyboard problem on 1 machine, that I can live with.

I did a clean install of RC1 on 2 machines, I have separate **/home** partitions on both, & I won't do an online upgrade because I think it is asking for trouble.  With the separate **/home's** it is no  big deal to totally scrap the old Root partition.

From the forums it looks like the biggest problem is wireless.

I like CAT-5 cables! :KS

---

### Post by KStorm on 2006-10-28
Mine has been great since Knot-3.

---

### Post by fragos on 2006-10-28
My upgrade from Dapper to Edgy went very well.  There are always a few nits with any upgrade but I'm glad I upgraded.  Not because Dapper was bad but because Edgy is better.

---

### Post by whiterabbit on 2006-10-28
I haven't had one issue thus far.  Probably the most hassle free distro I've tried in a while.

---

### Post by tortus on 2006-10-28
The ugrade from Dapper to Edgy has quite possibly been the smoothest OS upgrade I've ever done, right up there with upgrading from Panther to Tiger on my Mac.

I'm very new to Ubuntu, and haven't used Linux since about 2000 (back when Mandrake was all the rage) and I'm blown away at how far Linux has come and how intelligent, elegant and robust Ubuntu has been for me thus far. I'm finding myself using my Laptop with Ubuntu on it much more than my Mac with OS X on it; and man, I never thought that would happen.

---

### Post by picpak on 2006-10-28
Is it just me, or does every new release have a thread about it being the "worst release ever"?

Edgy has actually been very good for me. It's probably my favourite Ubuntu release since Hoary.

If you're having this many problems, simply backup your data and go back to Dapper. No one's forcing you to use Edgy.

---

### Post by hotani on 2006-10-28
I don't know about the worst release, since all I have to compare it to is Dapper which went pretty smooth on most machines. Also, when installing Dapper it was clean - now I'm experiencing what it is like to go the upgrade route. 

There have been a lot of problems in Edgy by comparison. I experienced the dead azureus bug, the "can't boot with new kernel" bug (by far the most severe), the x11-font issue botched the whole upgrade on one machine leaving it without a window manager -- although that was in the beta days so I can't really complain -- last but not least, I was bitten by the "wifi card no longer sees any networks" problem; basically it worked in dapper now it is dead in edgy.

So yes, it has been problematic. Maybe that is because I have 3 machines I keep running with the latest and greatest so I get to see more bugs than most, but I do think part of it is that Edgy is a rough-around-the-edges release.

One more thing... When a thread like this pops up, invariably someone (or more) will jump in with "works fine for me. Stop whining" or some such garbage. Please explain to me how this helps? Yes, we get it - not everyone has problems. Unfortunately, some of us do and that is why we post in the support forums for help, or maybe just to see if anyone else is experiencing the problem. Sometimes this is a great benefit, even though it may be laced with some frustration - I think we have all been there.

---

### Post by denzilla on 2006-10-28
I wiped/re-installed Edgy after it went final and I could almost swear my system was faster with the patched up RC installation. I also experienced the 100% cpu bug that forced me to restart. Tried Kubuntu and I ran into a KDE problem right away: Went to storage media to view drives, HDD was nowhere to be found, floppy/cdroms were folders that did absolutely nothing when I clicked on them other than  open up to an empty window with no drive activity. I want to like KDE but everytime I try it, its nothing but trouble. Edgy is a good release, but it got shafted because it only had 4 months dev time because Dapper was delayed.

---

### Post by PixelCloud on 2006-10-28
try going back to windows

i've had enough of command line fun for now :P

---

### Post by jamieplucinski on 2006-10-28
Mine works great, although the new boot-screen is horrible, all you see if a bounding progress bar, no startup messages as in the old screen so you can't find out where the heck the boot-up is freezing... aside from that, yayness :)

---

### Post by pay on 2006-10-28
Edgy was horrible on my machine. I couldn't use the liveCD so I tried the alternate kubuntu cd. After I installed it, it didnt load at all. It just stayed at the bootscreen. I tried upgrading to edgy from dapper but the exact same thing happened. I'm pretty sure that the problem is xorg7.1 not playing nice with my ati card. With gentoo I get this but its easy to fix. All I have to do is install the properitery drivers "emerge ati-drivers" but with edgy I can't get an terminal to download the drivers from the repository.

---

### Post by autocrosser on 2006-10-28
To make it "better"--edit your /boot/grub/menu.lst--on the kernel line you use, remove the "quiet" from quiet splash & you get a text box below the progress bar:-D



> **jamieplucinski said:**
> Mine works great, although the new boot-screen is horrible, all you see if a bounding progress bar, no startup messages as in the old screen so you can't find out where the heck the boot-up is freezing... aside from that, yayness :)

---

### Post by Aerandir on 2006-10-28
Edgy has been the best release so far IMO.  Upstart really seems to speed up the boot process.

---

### Post by handy on 2006-10-28
There are bad reports floating around the internet about how much trouble Edgy is, & how it has set back this most popular Linux distro'.

These reports are based on the numbers of problems we are seeing on these forums.

What the caster's of negativity on Edgy fail to consider, is that these forums are for support!!!

It is not the place where the thousands of satisfied user's of Edgy come to congratulate the dev's for doing such an amazing job, let alone such a job in such a short time!

So this kind of thread does at least give a chance for some positive feedback on a forum that exists to basically help people with problems.

---

### Post by SigmaX on 2006-10-28
I only had [one]("http://ubuntuforums.org/showthread.php?p=1680713#post1680713") issue with upgrading via apt-get... except on both my systems I had to run "apt-get -f dist-upgrade" repeatedly before all the packages were completed.  Besides that, I don't see the bootscreen -- but I suppose that's not important.

Just out of curiosity, does the Egdy installer disk have a text-mode option?  The Dapper livecd never worked for me, in any of the dozen or so PC's I tried it in.  "Normal" users (i.e. newbies) shouldn't have to download the "server" version, either -- they get confused.  For dapper I always used the Breezy disk and upgraded.

SigmaX

---

### Post by autocrosser on 2006-10-29
You are so very correct!!The Devs have done a super job in 4 months--And as Mark had said at the start of Edgy--"Edgy strikes out in new directions"

And I would expect some rough edges--a new start-up scheme (Upstart)--poised to have Eyecandy to blow other OS's off the map (Beryl/Compiz) & lots of new bits under the skin--no wonder it's a bit of trouble for some--My ride to here was a bit rough, but I'm very happy with my desktop & as soon as the Fawn is ready to run--I'll be there to help polish 'm (eyecandy cometh!!!)

> **handy said:**
> There are bad reports floating around the internet about how much trouble Edgy is, & how it has set back this most popular Linux distro'.

These reports are based on the numbers of problems we are seeing on these forums.

What the caster's of negativity on Edgy fail to consider, is that these forums are for support!!!

It is not the place where the thousands of satisfied user's of Edgy come to congratulate the dev's for doing such an amazing job, let alone such a job in such a short time!

So this kind of thread does at least give a chance for some positive feedback on a forum that exists to basically help people with problems.

---

### Post by fragos on 2006-10-29
> **hotani said:**
> I don't know about the worst release, since all I have to compare it to is Dapper which went pretty smooth on most machines. Also, when installing Dapper it was clean - now I'm experiencing what it is like to go the upgrade route. 

There have been a lot of problems in Edgy by comparison. I experienced the dead azureus bug, the "can't boot with new kernel" bug (by far the most severe), the x11-font issue botched the whole upgrade on one machine leaving it without a window manager -- although that was in the beta days so I can't really complain -- last but not least, I was bitten by the "wifi card no longer sees any networks" problem; basically it worked in dapper now it is dead in edgy.

So yes, it has been problematic. Maybe that is because I have 3 machines I keep running with the latest and greatest so I get to see more bugs than most, but I do think part of it is that Edgy is a rough-around-the-edges release.

One more thing... When a thread like this pops up, invariably someone (or more) will jump in with "works fine for me. Stop whining" or some such garbage. Please explain to me how this helps? Yes, we get it - not everyone has problems. Unfortunately, some of us do and that is why we post in the support forums for help, or maybe just to see if anyone else is experiencing the problem. Sometimes this is a great benefit, even though it may be laced with some frustration - I think we have all been there.

It's very helpful to know that a problem isn't universal.  I have no objective data for this case but believe that my success with Ubuntu upgrade relates to my religiously first going to Synaptic for anything I want to add to my system.  That's not to say I'm not willing to go elsewhere when I must.  Take the same application and install from tarball, deb package, Ubuntu package or an rpm converted with alien.  I dare say even if all four methods work as used, there are probably differences.  Differences create permutations and unpredictability.

---

### Post by qkmbr22 on 2006-10-29
I'm sorry to have upset those who worship Edgy and have no problems with it, but I was just wondering if I was the only one having these problems. I guess a lot of people actually do have problems, although, apparently nobody is having the same issues as me. I like some things in Edgy a lot more than Dapper (like Gnome 2.16, new Add/Remove software interface, new repository setup, etc), but as much as I like these new features, the fact that I can't use my computer for more than 15 minutes at a time (before it shuts down) does not make me want to use Edgy very much. So I'll go back to Dapper for now. Maybe they'll come out with some fixes for Edgy later, we'll see.

---

### Post by Krash1201 on 2006-10-29
both of the laptops i am currently useing run ati video cards.  i went the upgrade route since i didn't want to have to reinstall and mess up my dual boot setup with windows, ubuntu and my storage partition.  anyway, ht eupgrade was no problem.  the problem was after the reboot, at which point x crashed, the error message indicating that no screens could be found.  After some kicking around, reinstalling xserver-xorg, reconfiguring xorg, i get the same error.

Most of the problems i am finding are with the ati drivers, anyone else notice this being the case?

---

### Post by chickengirl on 2006-10-29
> **qkmbr22 said:**
> Also, Edgy randomly turns off my computer. After about 10-15 minutes of being on, my computer just turns off. Can't get anything setup either, because a package manager would be installing all the software I need and my computer would just turn off in the middle of it. I turn it back on, and it's like I haven't even done anything.

I didn't expect Edgy to be as stable as Dapper (which is the long term support version), but its just unusable. Aside from the few problems I described, I didn't find anything wrong with Edgy, but these few problems make Edgy 100% crap.

So is it just me, or what?

If anyone has any suggestions why my system is so messed up here's what i'm running: Emachines T1742 tower PC, 1.7 GHz Intel Celeron, 640 MB RAM, 48 MB shared video RAM, 40 GB HD, Dual boot windows XP home. Pretty old and crappy computer, but didn't bother Dapper at all.

Once upon a time on my old emachine (specs very similar to yours), I started having problems with the OS seemingly randomly not being able to access the hard drive, accompanied by several dramatic crashes that scared the bejesus out of me (my stuff wasn't backed up!!!).

Turns out the heatsink had fallen off of my motherboard.

Maybe something similar could have happened to you?

---

### Post by Uncle Spellbinder on 2006-10-29
> **Sethro said:**
> Its just you , mine is great

Couldn't have said it better myself. :D

---

### Post by _simon_ on 2006-10-29
2 machines here are also running just fine. We did fresh installs about a month before the release.

---

### Post by Foucault on 2006-10-29
I've upgraded to Edgy too. The update via the update manager was not very smooth and it stopped right before the "Cleaning Up" stage. For some reason the TeX and LaTeX packages are totally screwed up and this drove the update manager crazy. In fact the **latex-ucs-package** seems to undergo some weird dependency issue. Fortunately, update manager installed all the other packages so not a really big problem (but **still** a problem).

Upstart seems a nice addition to the distro, however I don't think this was a necessary update (yet). Boot times are a bit better but I still think the upgrade from long-tested initd to Upstart should have waited for Feisty.

I'll have to agree that Dapper was by far the best release. I've upgraded from Breezy by just editing the sources.list file and everything was flawless.

---

### Post by Craigus on 2006-10-29
My desktop upgrade from Dapper was pretty much unusable due to multiple stability problems.

Did a fresh Edgy install, and it was OK - no stability issues and very fast boot and shutdown. I liked it.

My problem was that despite trying all of the listed tweaks, I couldn't get OpenGL working on my Geforce 440. I couldn't live with that, so I've ended up going to Mepis 6.0, which I've been meaning to try for a while, and it's excellent.

I'll leave Dapper on the laptops, because they work fine. I won't be upgrading them to Edgy.

---

### Post by tubunu on 2006-10-29
All I can say, Edgy is great. It even recognised my prehistoric printer, which I had problems installing under Dapper. 
No issues, everything runs smoothly. :D

---

### Post by Choad on 2006-10-29
> **Sethro said:**
> Its just you , mine is great
yep, i would go so far as to say best release ever! (altho lots of people have problems upgrading, not me!)

---

### Post by Dinerty on 2006-10-29
Personally think it is the best OS for several reasons:

-System a lot more responsive on Synaptic Package Manager
-gnome 2.16 functionality greater increases a more overall responsive system
-boots quicker
-More up to date applications
-Faster shutting down

These are just my personal perceptions of the OS.

If you are having trouble regarding your system automatically shutting down this could be due to hardware problems e.g. overheating?

Was your system shutting down automatically under Dapper?

Edit: Have not read all pages so if this has been ansked sorry

---

### Post by yalding on 2006-10-29
> **Krash1201 said:**
> both of the laptops i am currently useing run ati video cards.  i went the upgrade route since i didn't want to have to reinstall and mess up my dual boot setup with windows, ubuntu and my storage partition.  anyway, ht eupgrade was no problem.  the problem was after the reboot, at which point x crashed, the error message indicating that no screens could be found.  After some kicking around, reinstalling xserver-xorg, reconfiguring xorg, i get the same error.

Most of the problems i am finding are with the ati drivers, anyone else notice this being the case?
Yes. I just did a fresh Dapper install in my "main work" machine after my ati x300 card get messed up with edgy.

I wont even think of upgrading for the next 6 month. Give me a break. For god sake, please do not release "official" stuffs that break my system.

---

### Post by jamieplucinski on 2006-10-29
Thanks :)

---

### Post by dr_d on 2006-10-30
edgy rox for me...

but clearly is *is* having quite a few problems judging by how flooded these forums are... it's insane.

---

### Post by reyfer on 2006-10-30
Just finished upgrading 10 machines using the apt-get upgrade route, and all of them are working great, no problems so far ( the last one has been running for about three hours, the first one which is mine has been running nonstop since the 26th)

---

### Post by cptnapalm on 2006-10-30
As Dapper was labeled long term service, I wonder if Canonical was expecting that the majority of users would continue using it rather than move on to Edgy.  Initially, I was not going to do the upgrade as Dapper was running just fine.  Curiosity, though, got the better of me.

I did have problems with the upgrade.

I was using Courier for mail stuff and while it was installing, I was informed that they could not do a straight forward upgrade, as there was a lot which changed in the packaging.  That was a serious headache only solvable by manually deleting every reference to Courier from the text listing of installed packages, then reinstalling things.

The other problem I had was X.  X has been a cause of difficulties for a very long time.  This one was not so bad, as it just needed something at the bottom to turn off Composite.  As I use the fglrx drivers for my ATI chip, X's composite as of right now, does not work.

I also had to do rather more manual upgrading than I was expecting, though now that I think of it, this sort of thing has happened before and it is perhaps just a limitation of apt.

The usplash graphics, I discovered rather by accident, are a separate package now and was not installed by default.

Aside from the courier issue which took a few hours to deal with, the other irritations were more of the "you're still not done?" variety rather than having to deal with real breakage.

Having gotten everything done, though, Edgy is very, very nice.  They were not kidding when they said that Upstart would decrease boot time.  There are new versions of vim and LyX amongst other things.

Unless I am mistaken, it does use more RAM, but that's not a problem for me as I'm still nowhere near maxing out my laptop's gigabyte of RAM.

I do think that there are legitimate criticisms to be made as far as the upgrading process goes.  Those packages and sets of packages which were not able to go through a straight forward upgrade path, should have had work around packages to uninstall (but leaving behind the configuration files) the current packages then download and install the new ones; I am pretty certain that my courier problem would have been non-existent had that occurred.  The need for a Composite section in xorg.conf must have been apparent, but one was not included in mine, at least.  The usplash graphics problem should not have been a problem; a transitional package should have been able to take care of that.

Was it worth the hassles?  Yes.  Edgy is running much more smoothly than Dapper on my laptop.  Should there have been fewer hassles?  Yes.

Moral of the story: If you want super stable, go with the version labeled long term service.  If you want newest, latest and are prepared to deal with the possibility of headaches to get there, go with the one called Edgy.

---

### Post by deanjm1963 on 2006-10-30
I'm in two minds about edgy. 

First mind, having used dapper, and configured it, customized it, tweaked it, preened it, and made it great, I thought I'd do a fresh install of Edgy and follow my "tried and tested recipe" of installing apps/tweaks etc. First problem, installing nvidia-glx, if you don't install "kernel-generic... etc" beforehand synaptic automatically installs all the restricted drivers etc for linux-386... considering that "kernel-generic...." is installed by default on most systems... hmmm and what a pain that was to fix... simple solution, quick re-install. Using the alternate-cd, fstab settings produces 2 floppy drives ... on some system, not all, but easy fixed by editing the fstab file in /etc/.. metacity themes not showing up properly... again easy fixed by installing gtk2-engine-pixbuf... why isn't this installed as a default? Icons... I like to use nuoveXT for both gnome and kde... copied them to the appropriate folder... still half of my icons are generic ubuntu... back to eye-sore orange for a change. The rest of the install/tweaks etc., worked a treat. I think edgy is great. Not so great if you've heavily customized your dapper install, but no doubt there are work-arounds in the pipeline. 

Second mind... if you're a first time linux or ubuntu user and don't need to install your own icons/themes/etc and settle for the defaults, you can't go past giving edgy a try.

I'm back to dapper... and everything is as it should be, stable, responsive and highly customizable. Edgy shouldn't have been called 6.10, from all the versions of Ubuntu I've used and tried since day one, edgy seems to be the "non-color-specific-sheep of the family". It looks like Ubuntu, sort of behaves like Ubuntu, but it's a new member to the family. Earlier releases were a breeze to update/install, albeit some things were different in configuration, application, and usage for each upgrade, but it wasn't a headache.

In my OWN personal opinion (so please no flames, etc.) I think edgy could have done with a month or two more testing. It's nice having the latest and greatest, but give me an earlier version that works a dream everytime.

---

### Post by flapane on 2006-10-30
mine is not  very fresh, I installed over 1year ago hoary, but EVERY system update went well, even edgy

---

### Post by dada1958 on 2006-10-30
I installed Edgy from the RC alternate CD. Major issue here that my Ricoh Caplio RX isn't recignized. I'm going to try an install from the final release CD one of these days because I do like Gnome 2.16.

---

### Post by tenn on 2006-10-30
Mine is perfect it just gets better.

---

### Post by MattJ100 on 2006-10-30
> **autocrosser said:**
> To make it "better"--edit your /boot/grub/menu.lst--on the kernel line you use, remove the "quiet" from quiet splash & you get a text box below the progress bar:-D

Wow, thanks! Just what I wanted :)

---

### Post by Kateikyoushi on 2006-10-30
> **qkmbr22 said:**
> Also, Edgy randomly turns off my computer. After about 10-15 minutes of being on, my computer just turns off. Can't get anything setup either, because a package manager would be installing all the software I need and my computer would just turn off in the middle of it. I turn it back on, and it's like I haven't even done anything.

```
kateikyoushi@X505:~$ uptime
 20:25:57 up 9 days, 12:28,  3 users,  load average: 0.16, 0.27, 0.43
```

I guess it is not that bad for me...

---

### Post by onegear on 2006-10-30
i had issues, as well, during the upgrade from 6.06.1 but i'm not ready to blast the ubuntu project for it.  the upgrade didn't work so i simply downloaded the iso and did a fresh install.  i always backup all my important data before attempting any upgrade so all worked out well.

once 6.10 was installed and i finished some simple configurations, my laptop and desktop are running great.  very, very fast.

---

### Post by Russty of Oz on 2006-10-30
Just thought I would add my bit.  

My Edgy is FANTASTIC!:cool: 

I have been using Edgy for a couple of months as I was having lots of trouble with Dapper, but Edgy has been reasonably trouble free.  I have not had to reinstall once!  After several installs of Dapper.  

For me, this is THE BEST release so far.  (I began with Breezy)

SO, I'M HAPPY :D

---

### Post by ricanelite on 2006-10-30
Well, As for me it has been a full 2 weeks since I started using Ubuntu Linux, Which I have to say I have enjoyed, But getting through the Edgy install I had some problems with I'm assuming the connection speed to download the files to get the upgrade. Which took me all day long and I mean from 6:00am EST to about 4:00am the next day. Which I was patience enough to hold on and not discourage with it. So far I got to say the major improvement I see with my machine is that the fonts are nice. So much more readable then when I had Dapper installed. That is just me. Also as for the boot screen it is kind of weird that I don't see it which I have been so use to seeing from Windows, MAC OS X, and now not seeing it. Well also can it be that I'm running Ubuntu Linux Edgy on a PPC machine?

Well so far so good. If I run into any problems. I will be sure to post them here on the forums. 

Last thing is Java installed on Edgy, or there is still no java and flash going on.

---

### Post by doobit on 2006-10-30
I did a clean install with the alternate CD on my root partition, and left /home intact. It went well and is working fine. However, I think Dapper was just fine on this old machine. There was no reason for me to upgrade except for curiosity and the fact that I could.

I tried an apt-get dist-upgrade the first time and it failed.

---

### Post by Shay Stephens on 2006-10-30
I had problems upgrading.  Once I did a clean install, things have been great.  I won't go back to dapper, edgy is way too nice and fast and is now more stable than dapper or even my windows xp partition is.  

I thought I needed a new motherboard board because both windowsxp and dapper and breezy would crash after 20 minutes from the first cold boot.  But not edgy.  My system now feels stable for the first time.  I am amazed.

---

### Post by sorin7486 on 2006-10-30
I find it better then dapper was in the first few weeks .... and considering that dapper was supposed to be the stable one that's a huge thing :D

---

### Post by Kateikyoushi on 2006-10-30
Not mentioning how delayed dapper was.

---

### Post by Webziz on 2006-10-30
I think edgy pretty much sucks. Amarok won't work, nautilus peaks cpu usage to  ~100% (I was wondering why my fans make such a noise), movie players don't work and I haven't noticed any positive improvements, that affect my comp using in any way.

---

### Post by meyrd on 2006-10-30
I think you need to realize Edgy is very good software and you may just be having dificulties based on your hardware and configuration of the OS with that hardware. If you take the time to read the forums and try to fix the issues you've run up against you will find Ubuntu to be one of the best distro's.
I just started my linux learning process and I find it takes a bit more patience than other $$$ software. Hang in there and give more details on what exactly is wrong and what type of hardware you have  and you will get helpful advice from the ones who come before us.

Just my input,

---

### Post by steve.horsley on 2006-10-30
> [QUOTE]To make it "better"--edit your /boot/grub/menu.lst--on the kernel line you use, remove the "quiet" from quiet splash & you get a text box below the progress barWow, thanks! Just what I wanted :)[/QUOTE]

Personally, I like to remove the "splash" as well as the "quiet", and get a "normal" boot screen.

---

### Post by autocrosser on 2006-10-30
That's what is nice about Linux--"have it your way!"

---

### Post by kent41 on 2006-10-30
I am very new to linux so I see it different than seasoned linux users.
But I had Breezy 5.10 running good from my perspective and when I downloaded Edgy and burned a .ISO copy and then installed Edgy on a clean hard drive I had high expectations and at first I was impressed with Edgy.
I like the spell checker, boot up speed, shutdown speed, Internet speed seemed faster, and Fire fox 2.0. Just disappears, However my Canon LiDE 60 scanner worked out of the box.
Then I started adding applications and everything fell apart. Things that used to work were now broken or would not install correctly. Remember I had a clean install.
Ethereal was replaced with something else. the FAX pgm had problems. the DISK option to check disk drives was missing and on and on and on.
Many are having problem with the battery monitors.
Open Office has problems now with the fonts all are the same except for a couple. When you change the fonts nothing happens.

---

### Post by kent41 on 2006-10-30
and to add more


I have problems with spanning tree packets on Edgy which in all honesty should have nothing to do with an operating system. This is scary.

Spanning tree packets are used to control switches and bridges multiple paths on a network system. Absolutely nothing to do with OS. So you tell me what future Edgy has. Maybe update will solve the problems.
 
If you only want to surf the internet and little else Edgy will work great.

If you don't believe me just take a look at the Forms.

I have remove my Edgy Disk on my laptop and inserted the Breezy 5.10 disk and all is well for me. I am so glad I did not try to upgrade my Breezy 5.10 to Edgy or I would have a lot different words about Edgy.

___________________________________________________________________
Toshiba Satellite laptop M35X S-111 1.5g  500mb  Dlink DWL G630

---

### Post by vayde on 2006-10-30
I just re-brained my computer 3 times this weekend.

First I upgraded from Dapper to Edgy.  Used apt-get, which I realize isn't the best way.  It didn't fly.  No X, fair enough, I had compiled the ati drivers manually, didn't expect that to work.  Took a while to get them going again.  Machine lagged up constantly, froze occasionally, and Nautilus went zombie and took up 98% of the cpu every time I closed a window.

Upgrades don't always go smooth, so I reinstalled from scratch.  Same problems.  Cpu fans are alway on full blast, screensavers lock up the box, nautilus crashes.  Occasionally it would just lock up completely requiring poweroff/pull battery to fix.

I went back to Dapper, which works flawlessly on my system.  I didn't think my machine was that out of date or strange: Inspiron 9300 2G cpu 1G ram ATI X300 video.

I wonder if edgy just got rushed after dapper's delay?  Oh well.  I'm glad to hear that there are people who are having a good time with it, just not me.

---

### Post by lucia_engel on 2006-10-30
> **steve.horsley said:**
> Personally, I like to remove the "splash" as well as the "quiet", and get a "normal" boot screen.

Me too.

Ever since Breezy my laptop have had trouble booting with quiet and splash so I've always used the 'normal' boot screen and don't have those bootup problem people describes. I used an alternate disc last time to go to dapper because the upgrade killed alot of my apps. This time I just upgraded when RC1 came around. Only Azureus has problem but that's not a big deal. I loved that the repo has alot of up to date softwares so I don't have to download them outside, which to me means a cleaner system.

---

### Post by podunk on 2006-10-30
To the person who started the thread - the autoshut down thing sounds very much like a hot CPU (which others have mentioned). What may be happening is that the new release uses more CPU cycles to keep the fancy desktop up. This results in more heat - heat that you wouldn't have on the Dapper version.

If I were having this problem I'd open up my case and make sure the fan was running OK, that the heat sink and exhaust fans weren't clogged by dust and dirt, stuff like that.

---

### Post by Najand on 2006-10-30
In my case, only the ibook one failed... And it was not because of Ubuntu, but because of yaboot and Macintosh's stupid monopoly policy they have. It is just working great now.

---

### Post by jrjazzman on 2006-10-30
There seem to be a lot of problems reports with upgrades to Edgy.  So I'm pretty discouraged about upgrading.  I'd like to, but I use my computer for work and can't really afford to be down for a significant period of time.  Does anyone know of any remotely accurate statistics on the probability of an upgrade failing?

---

### Post by vixenk on 2006-10-31
At least you got Edgy installed is all I can say. There is a bug with the live cd that I'm one of those unlucky enough to experience. The cause is unknown as of yet. Anyone that gets a black box when loading the Edgy live cd should definitely report it here with their machine specs:
[https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)

---

### Post by Tempurite on 2006-10-31
Yep... the worst.

---

### Post by fragos on 2006-10-31
I can only speak to my personal experience which was good.  I upgraded with the preferred method which was also the simplest and most direct.  I've noticed that many people who had problems used apt.  I backed up my /home directory just in case there was a problem.  In my case I placed it in a spare partition.  Then I followed these instructions.

Upgrading using Update Manager

If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):

gksu "update-manager -c -d" 

The "-d" switch instructs Update Manager to consider pre-release versions, including this Beta release. Without this switch, only official, final releases will be considered. The "-c" switch tells it to look for upgrades at all. By default the 6.06 LTS release will not offer that automatically because of its long support cycle and high stability.

If you have a working network connection, it should then inform you about a new release and offer to upgrade your system.

---

### Post by cotcot on 2006-10-31
From my experience Edgy is a clear improvement. The upgrade from Dapper was spotless. 
Maybe check the alternate install CD

---

### Post by quinnman on 2006-10-31
I am extremely satisfied with edgy. Upgrade from dapper went flawlessly and the only problem i am encountering is missing usplash while booting, but it is just a minor annoyance.

---

### Post by Bentov on 2006-10-31
I guess I've just been really lucky.  This is my first ubuntu install, and I even have an ati card; with no install problems at all.  The only issues I've ran into are a problem with the invest panel applet(it doesn't do anything expcet install, can't remove or use it) and one time my mouse wouldn't stop scrolling on it's own.  Things have come a long way since RH 4.1 which was the last time I tried to run linux.

Bentov

---

### Post by todds on 2006-10-31
Hello i belive edgy is a lot quicker and faster than dapper,it has seen some improvement in the wireless configurations,but still has a long way to go,i was using pclinuxos before which uses kde and my old machine here got really bogged down but using gnome it is really flying,iam very happy and look forward to feisty dawn.....

regards

todds

---

### Post by pillypoon on 2006-10-31
My install has also been one of the best to date.  So quick and simple.  I love my edgy  :p .

---

### Post by bsussman on 2006-10-31
> **ianmacgregor said:**
> I have noticed, from these forums and #ubuntu on freenode, that if you upgrade via apt-get dis-upgrade then there can be problems...

it's **dist-upgrade **and although I do not usually do it, I did this time and have no ubuntu problems to report.

As soon as I make sure that FF1.5 works ok on it, 6.10 becomes my desktop.  It already runs my wife's desktop and my laptop.

---

### Post by Osamabingandhi on 2006-10-31
I got my edgy to run perfectly, with some minor problems not connected to edgy but my own hardware. One thing that could be edgy or not is that i can't get 1366x768 resolution on my Lcd-TV any way i try. Have nvidiaglx and all works good with my desktop monitor but can't get the right resolution on my TV...Could be a problem with linux-nvidia driver and my geforce 3. It works under windows. I am about to get a new computer so i will let this problem slide.

---

### Post by _lynX on 2006-10-31
> **hotani said:**
> One more thing... When a thread like this pops up, invariably someone (or more) will jump in with "works fine for me. Stop whining" or some such garbage. Please explain to me how this helps? Yes, we get it - not everyone has problems. Unfortunately, some of us do and that is why we post in the support forums for help, or maybe just to see if anyone else is experiencing the problem. Sometimes this is a great benefit, even though it may be laced with some frustration - I think we have all been there.

If you make a help thread, you will get some help. If you make a thread entitled, "Is it just me, or is Edgy the worst Ubuntu release ever?", people are going to reply to let you know that it's not.

@topic: I first tried upgrading Ubuntu using the upgrade-manager and things worked fine, but I just felt like I wasn't seeing the updates promised by Edgy. The new splash wasn't there on bootup/down, and some of the packages just weren't installing (Firefox 2.0), so I decided to go ahead with a clean install. 

Things are *perfect* now, and I'm enjoying Edgy more than I've enjoyed any other Ubuntu release.

---

### Post by pillypoon on 2006-10-31
@_lynX.   I could not have replied better myself.!

---

### Post by jdunn on 2006-10-31
Mine has been great.  However, I didn't upgrade from my Dapper install.  I started with a fresh Edgy install.

I'm using Kubuntu Edgy and I only have a few issues:

1)  Kcontrol does not set the "OffTime" properly for DPMS (monitor power saving).  It seems to default to 5 Hours after reboot.
2)  There is an issue with libxine 1.1.2 that causes A/V to be out-of-sync when playing DVDs.  I personally notice this problem when playing DVDs on the Kaffeine player.
3)  I didn't like the new purple color scheme at first but I've gotten used to it.

---

### Post by kvonb on 2006-10-31
Tried it today with a fresh install.

I was very happy with it until I found out that my ATI 9200 won't work with it.

Well it will work, and I did get 3d working, but the only ATI driver that will work with Edgy is the 8.28.x version which crashes Google Earth, Open Office, and who knows what else, (maybe it's just my machine, but I doubt it).

This is NOT the fault of Edgy, just that my card is no longer supported by ATI.

As soon as I can afford an Nvidia card I will load Edgy again.

---

### Post by ZBREAKER on 2006-10-31
Fresh install.....wiped Dapper after hearing of various heartaches for some with upgrading. It's been smooth sailing indeed with Edgy so far!

---

### Post by brownknight on 2006-10-31
:) couldnt be happier with my shiny new installation of edgy. in dapper my wifi will not connect for the first 5-10 minutes after starting ubuntu so i have to sit and wait but edgy just fires up the connection at start-up.

---

### Post by Tobster on 2006-10-31
Mine been wonderful too, love it :)

The only problems I'm having is that I'm still kind of new to Linux so it more user instability rather then the OS[-(

---

### Post by tubunu on 2006-10-31
I've done a fresh install of Edgy and everything seemed to work great. Faster boot time (even on my prehistoric PC), power management: shut down monitor worked also (I couldn't get it to shut down in Dapper). 

On the other hand though, I've just run into a problem of screen resolution which got changed after I hibernated a few times without shutting down completely. I cannot change the resolution in GUI and at the moment I'm running on live Edgy as I'm typing this. I guess I either have to reconfigure Xorg (which I have NO IDEA how as I'm not that geeky) or do another fresh install of Edgy and abstain from hibernating? 
Mmmm... that's my Edgy story. ;)

---

### Post by steve.horsley on 2006-10-31
> **kent41 said:**
> and to add more


I have problems with spanning tree packets on Edgy which in all honesty should have nothing to do with an operating system. This is scary.

Spanning tree packets are used to control switches and bridges multiple paths on a network system. Absolutely nothing to do with OS. So you tell me what future Edgy has. Maybe update will solve the problems.
 

First - I presume that the replacement for Ethereal you are complaining about is Wireshark. If you check their web site, you will find the name changed about 6 months ago after the maintainer moved to a new employer and the old employer retained the (registered) Ethereal trademark. So Ethereal is no longer updated, and Wireshark is the new fork. You can't blame Ubuntu for this.

Second - I am dying to know what problems you are having with spanning tree packets. Unless you are bridging with Linux (unlikely, but possible if you use OpenVPN or similar), they should be completely ignored.

---

### Post by stamy on 2006-10-31
Edgy is working very very well for me.
I have installed it on four computers without any problem. Wifi with wpa and TV tuner are working fine.

With automatix i can watch videos, java, flash all is working fine.

The only negative point is related to the new kernel 2.6.17-10 because allow-hotplug option is no more working in /etc/network/interfaces :( but the startup is so quick that does no matter :)

Since Edgy i have no more Windows installed at all, at least :)

---

### Post by therunnyman on 2006-10-31
It's so frustrating to have a new iteration fail you - as Dapper did for me - mainly because you fall behind on the forums.  My thing, up until Edgy, was that I couldn't offer a whit of help to anyone because I was still running Breezy.  It's a kind of excommunication, too, in that nobody can deal with you very well anymore, try as they might.

There's a little more to a botched upgrade than simply machine malfunction; it does, strange as it sounds, affect people personally.  So, ergo and therefore, I sympathize with the original poster.  I know that frustration, and I'm fairly certain anybody who moved to Ubuntu from Windows only to have something major break can relate, right?

runny

---

### Post by jordilin on 2006-10-31
> **qkmbr22 said:**
> Well let me start by saying that the upgrade from 6.06 completely failed, even though my 6.06 installation was fairly fresh and almost completely unmodified from the original install. It screwed up that installation, so i decided to just burn a copy of Edgy to a CD and install a clean copy.

Edgy doesn't display any boot up screen at all. I turn on my computer and for about a minute I see nothing. Then I see the login screen. The shutdown screen is blank too. What's up with that?

Also, Edgy randomly turns off my computer. After about 10-15 minutes of being on, my computer just turns off. Can't get anything setup either, because a package manager would be installing all the software I need and my computer would just turn off in the middle of it. I turn it back on, and it's like I haven't even done anything.

I didn't expect Edgy to be as stable as Dapper (which is the long term support version), but its just unusable. Aside from the few problems I described, I didn't find anything wrong with Edgy, but these few problems make Edgy 100% crap.

So is it just me, or what?

If anyone has any suggestions why my system is so messed up here's what i'm running: Emachines T1742 tower PC, 1.7 GHz Intel Celeron, 640 MB RAM, 48 MB shared video RAM, 40 GB HD, Dual boot windows XP home. Pretty old and crappy computer, but didn't bother Dapper at all.

You must have a severe hardware issue. I would take a look at system logs. Linux is not perfect, but Edgy in my opinion is the best Ubuntu release ever.

---

### Post by Turin Turambar on 2006-10-31
I have troubles with Edgy as well.

When I installed Edgy and restarted the PC, the grub couldn't boot the Ubuntu system at all!! The reason was wrong root address and wrong HDA. Now, I don't even want to think what could've been if I didn't have prior linux knowledge!

WHY did grub wrote in menu.lst HDA1 instead of HDA3 and Root hd0,0 instead of hd0,2 is beyond me! Can someone explain?

I also tried to install Thunderbird from the Ubuntu DVD. Installation went well.... 'till I wanted to open the Apps menu. The system then collapsed.

Oh yeah, I cannot compile my Lucent ALK8 modem drivers. Something doesn't work, so I don't have internet access in Edgy. :(

Soo...... for me, yes, this definitely is the worse Ubuntu I tried.


No, I don't have any hardware troubles! I've been using Ubuntu since Hoary... my system is working just fine and everything is set accordingly.

---

### Post by Bigbluecat on 2006-10-31
In your menu.lst you need to set groot to you root parition and kopt to the correct drive.

I hit this problem with a previous kernel upgrade.

Correct those two items and you should be good to go for the future.

---

### Post by johnny9794 on 2006-10-31
I am new to linux, and ubuntu dapper drake 6.06.1 is my first linux operating system, I seen that edgy came out so i gave it a shot,  everything worked good up to the part of installing the nvidia driver "when i have a nvidia fx5500 TD256 installed on my pc" and when i "sudo nvidia-glx-config enable" in terminal and rebooted, it could not load up x-server and had a bunch of weird text letters bordering the error with a "ok" to press and i pressed ok then it could not load up the desktop at all. In the error it said that i had a generic graphics driver "did not know nvidia was generic pfft" :S:S. so i tried installing edgy a few more times and all the same "x-server could not be loaded" so i am back to 6.06.1 :) with a working nvidia driver. and ohh they do not have Disks app "good app to have" in edgy wth...

---

### Post by neo_reloaded on 2006-10-31
I think edgy is great

2 problems so far
 - WiFi network connection disconnects and reconnects every time a network request is sent out
 - 100% CPU usage by nautilus

These two are some severe problems. But this is the price you got to pay for staying on the bleeding edge and I hope an upgrade is coming out soon.

---

### Post by Krash1201 on 2006-11-01
i was having a bit of a video problem with x crashing, but sudo apt-get install xserver-xorg-video-ati and a sudo dpkg-reconfigure xserver-xorg fixed the problem after a reboot.  Worked great with my fire gl t2 ati graphics card.  Haven't figured out the same problem with the savage graphics in my older laptop.  Using edgy is great so far, though there are little problems here and there, like network manager doesn't see ath0, or the standard network manager that ships with gnome will no longer detect all available wifi networks, and my shortcut keys don't work in firefox.  Other than that, it looks great and is a little quicker overall.  I am pleased and impressed even with the minor hiccups here and there.

---

### Post by MattJ100 on 2006-11-01
Ah well. It's the same as when Dapper was released. People have problems and say Dapper is the worst release ever. People who don't, love it.

People switching from Windows who have problems say Linux is the worst thing ever. People who don't have problems love it.
These people always seem to turn a blind eye to the endless number of WIndows forums that exist, and how installing Windows from CD is not a particularly nice or easy experience.

My experience of Edgy is that, as was known from the beginning, it is packed full of the latest, greatest technology that hasn't been tested. FF2.0 and Gaim 2 are in (neary barely out of) beta!

In short, I recommend Dapper to anyone trying a first install. It is Dapper I am installing on friend's and familiy's PCs, unless they have hardware problems. So, ok, if you had a bad experience with Dapper, it's probably worth the upgrade (clean install, not dist-upgrade).

---

### Post by CheeseEatingBulldog on 2006-11-01
The upgraqde to edgy killed my machine as well, X broke, usplash broke, nvidia drivers broke, beryl/xgl broke and the new firefox is crap (long load times and sometimes just...vanishes). 

That said, I figured out the usplash problem, you need to define the resolution in the usplash config, then reconfigure your boot 'img' to apply the setting to the boot (shutting down it did see without reconfigure). And after about 2 hours of messing about I got the nvidia drivers to work again and with it beryl/xgl (although that seems a lot less stable under edgy than dapper). I am considering downgrading to Firefox 1.5 as 2.0 really is a heap of bloatware, runs really sluggishly...but apart from that...which to be honest I think was quite fun (fixing stuff), but I can understand that others might not think so. :)

It seems to ok now...on to Feisty Fawn!

---

### Post by Epperly on 2006-11-02
It must be just me, too.

---

### Post by hizaguchi on 2006-11-05
I've gone back to Dapper.  It sucks, because Dapper is noticably slower and sleep doesn't work on my laptop, but it is completely worth it for the stability and the fact that everything important actually works.  I'll try to upgrade again in when Feisty releases.  Worst case though I've got 3 years of Dapper desktop security updates.  Surely in the next 3 years there'll be another solid release, right?

---

### Post by Epperly on 2006-11-05
Dapper is actually 20 seconds faster than Edgy on my PC, weird maybe? Idk.
I just got it working on my laptop, too and yeah... sleep doesn't really work =(

---

### Post by Turin Turambar on 2006-11-05
I have to say that I fixed all issues I had with Edgy (basically, grub & modem drivers). Now runs perfectly and is fantastic!
I'm very impressed though!

---

### Post by sloggerkhan on 2006-11-05
Well, I must say that I don't think Edgy offers too many significant improvements on Dapper, though it can cause a lot of pain.

First of all, the live CD for Edgy is an utter disaster. I can barely manage to use it. Safe mode doesn't work on it, and none of the normal boot modifiers let me even get to a console. Fortunately I figured out a workaround to that which works for my computer (abnormal boot modifier let me get to a console.) But many people can't find any way at all for the live CD to work.

As for the automatic upgrade process over the internet (using "correct" method), the first time I did it, I thought it went pretty well, but turns out I couldn't get access to the consoles (tty1-6), they showed up as gibberish. Still, didn't bother me too much. Went ahead and installed beryl. After about 3 days with beryl I had a hard crash. Guess that's what I get for using beryl... Oh well. 

Anyhow, at that point I didn't know how to get the edgy install disk to work, so I had to reinstall dapper. Which I did. I put off upgrading to edgy, but finally gave in. So this time, it errors in the middle of auto-upgrade. I have to go to command line, use package tools to get it working. A bunch of crossover dependency problems showed up, and I had to remove about half the system so edgy could finish installing without problems. At the end of the day, I have edgy installed. Then I discover that beagle seems to be causing a memory leak. (It would shoot from 12 megs of RAM to taking up all ram and swap in about 1 minute. Then computer would die.) So I have to turn off Beagle. (That's actually my theory on what could be causing your comp to shut down every 15 minutes... monitor your process for memory/cpu use) And whatever problem prevented me from getting to the console screens is still there.

So at the end of the day, my favorite things about edgy are related to the evolution upgrade (spellcheck integration is MUCH better) and firefox 2 (spellcheck, again.), both of which I could have probably gotten working on dapper, which boots at about the same speed, is more stable, and uses fewer system resources.(My processor has a lot more spikes under edgy, and it uses more RAM.

Oh, and flash and java plugins for firefox, which were EASY to get working under dapper I can't seem to get working in edgy. No idea why. It's supposed to be easier, there are add/remove packages for them. But they don't seem to work. Errr. I know I have mplayer plugin working because apple.com/trailers work.

But adobe's sites for testing flash and java both fail, yet the plugins are in the correct directory... I have tried installing them multiple times, multiple methods, linking a bunch of directories, etc. To no avail.

So overall, I really liked edgy for the the 3 days I had xgl/beryl working, but otherwise it's been rather a disaster. I mean I could have an dapper install up and running in like 1/4 the time it's taken me to have edgy not working.

---

### Post by bobpur on 2006-11-05
I got Edgy on my "old Compaq" and it run great from the gitgo. I updated the repositories installed Automatix and Beryl and am loving life. 
Two of my other computers, however, were not so happy. One is quite happy on Dapper and the other went to experiment with dualbooting WinXP and Mepis.
I expected as much from a "new" release and was not surprised at two machines that experienced problems. I'm more shocked that one did not have problems.

---

### Post by graigsmith on 2006-11-05
most of the annoying bugs from dapper are gone.  like totem not being able to scroll thru videos. i love edgy for this.

and also, edgy has better things like the new gaim. which i love.

But, then there are also problems, like nautilus crashing. which has only happened once. but havent seen it since.  And the firefox fonts. which is almost too much to bear. it's a silly little annoyance that *should* be fixed.  it seems every version of ubuntu ships with silly annoyance bugs like this, and i wish there was a bit more testing or something so that bugs like this don't make it to the final release.  either that, or they should fix annoyance bugs after it gets released.

---

### Post by Najand on 2006-11-06
Well, I  don't know until when this conversation is going to continue. Actually what is obvious is that, there are not a lot of changes to dapper just some kernel upgrade, adding some few new packages, etc. If your system is slow, reconfiguration can make it faster. Just don't make the whole story too big. The Nautilus crashing is because of gnome... Gnome is now trying to change many essential stuffs for better effitiently and faster behaviour, these days and that makes unstability. Actually many of them are  to be removed for the next gnome edition. If you find bugs, please don't hesitate to send it to Gnome's bugzilla. Actually some of the bugs are freedesktop's bugs too. Well, I can remember old days, we had kernel crash every 30 minutes. So let us be patient and remove the bugs, one by one. I hope your problems can be removed soon.

---

### Post by ner0tic on 2006-11-06
> **Sethro said:**
> Its just you , mine is great.

---

### Post by ronmarley1 on 2006-11-06
Sorry to the folks having issues, but Edgy has been great for me.  Dapper was great also, but I just could not resist the urge to install Edgy.  I did not try an upgrade, I did a fresh install.  The only problem I ran into was during install and reformatting my old boot partition.  The trick (mentioned on the Edgy page) was to delete the partition and then recreate it using gparted.  Install went quick, and has been running fine for six days.  Also, getting Beryl to work on Dapper was a chore.  On Edgy, it was a simple copy/paste from the Beryl wiki, and 5 minutes later I had all the AIGLX eye candy.  Good luck to the folks that are having a hard time.
I have an IBM ThinkPad R51 with Intel 855 graphics card (32 Mb RAM), 512 RAM, CD-RW, Intel integrated 2200 wireless and integrated NIC.  All work with Edgy.

---

### Post by turbojugend_gr on 2006-11-06
Another VERY happy user here, I just love xorg7. Oh btw my issues only had to do with updates, ehy on earth they are messing 'em up recently (i mean the last 2-3 months)? Anyway I hope there won't be anymore...

---

### Post by Grog140 on 2006-11-06
I had to put a backup of dapper I had back on my computer. I just couldn't stand Edgy one minute longer.

I loved certain features and would love to use it but I just need to draw a line somewhere.

The bootup was slick and fast except my computer kept freezing. Not a hard lock but the system monitor would stop ticking and I couldn't interact with anything except the windows on screen. Sometimes it would hard lock though.

That is the main reason I switched back, other than that its fine its just the I would rather a slightly longer boot sequence that I only have to see once every two weeks than a damn fine and fas one that I need to see upwards of once a day.

I don't agree that it is worthless, its just completely undtable on my machine or something.

---

### Post by therunnyman on 2006-11-06
Edgy properly enumerates drives, Dapper does not.  You can make a proper RAID with Edgy; with Dapper, you cannot.  If your system consists of more than two disks, Edgy can deal with it; Dapper cannot.  Edgy recognizes optical disks; it's hit or miss with Dapper.

What confuses me is that Dapper is valorized as this particularly special iteration because it's "stable".  "Stable" is great, sure, but what good is stability if it's stagnant?  It's like being married to a corporate slave with a regular cost-of-living salary increase: an ostensible movement forward, but, in reality, no movement at all.

Dapper sucks, and I'll probably hear from the mods for saying so now (just as I did when it came out).  Edgy made hardware recognition and enumeration robust, no dingling around as Dapper did.

Now what I'm curious to see is the amount of disenchanted Edgy users who get it from the mods for light gripes, like the ones in this thread.  I got it for a heavy gripe - and a significant one - in one thread.  Mods, I love you, but let's see the PMs and anger hit the anti-Edgy users.

runny

---

### Post by johnny9794 on 2006-11-06
Ok I made a post in this forum " #95 post [http://ubuntuforums.org/showpost.php?p=1695441&postcount=95](http://ubuntuforums.org/showpost.php?p=1695441&postcount=95) " and well i decided to go and try edgy one more time and well everything works great now with the regular nvidia driver and the nvidia beta driver. "Dunno if ubuntu had update fixs or w/e for the nvidia driver" I have not run into any problems yet for the reason why i went to edgy is to have beryl which is a badas* program "I Love It" :) and for edgy, its going good so far.

---

### Post by Atomic Dog on 2006-11-07
> **Najand said:**
> Well, I  don't know until when this conversation is going to continue. Actually what is obvious is that, there are not a lot of changes to dapper just some kernel upgrade, adding some few new packages, etc. If your system is slow, reconfiguration can make it faster. Just don't make the whole story too big. The Nautilus crashing is because of gnome... Gnome is now trying to change many essential stuffs for better effitiently and faster behaviour, these days and that makes unstability. Actually many of them are  to be removed for the next gnome edition. If you find bugs, please don't hesitate to send it to Gnome's bugzilla. Actually some of the bugs are freedesktop's bugs too. Well, I can remember old days, we had kernel crash every 30 minutes. So let us be patient and remove the bugs, one by one. I hope your problems can be removed soon.

Yup yup yup.  Report bugs, determine if the issues are bad enough to switch back to 6.06 or work on the fixes that have already come out.  In my case, with a number of Ubuntu machines to tend at work and home, I have decided to wait a while before upgrading.  I don't have time at work to deal with bugs right now -even the spectre of possible ones.  It will cut into my PR, coffee and chat time with the employees/managers (to put a nice face on the hated IT dept) :D  

ps.  95% of employees like Ubuntu better than OSx.  I retired two nice iMac's because nobody wanted to use them :o  That's a hell of a compliment.

---

### Post by drewtown on 2006-11-07
I did a clean install of edgy and I'm pretty new to linux and it has gone exceptionally well, except getting beryl to work but that is its own beast.

---

### Post by sktfeelsdapper on 2006-11-07
Well, I've had alot of problems with Ubuntu that are my own doing, but my update to Edgy wasn't all that bad.

for starters it is recommended at least from what I saw you do "gksu update-manager -c" to upgrade, because even though it's printed here in the forums changing your sources or dist-upgrade might not work as well.

My problem (I reinstalled dapper cause I'd screwed up a dual boot) with installing/Edgy was how long it took to install. I think I clocked in under 3 hours, and I know my computer can't be THAT slow.

Also with about 7 minutes (7 very long minutes) left the update-manager disappeared although everything else was still in tact. With my sources and everything else now being Edgy-fied I just dist-upgraded and everything worked and it installed the rest.

The only problem other then that, was xmms was really buggy and kept shutting down, as well as xchat-gnome. Also I made the mistake of not having a swap partition and my computer ran really slow, which I thought was Edgy but really my stupidity. 

I actually was really scared to upgrade to Edgy because I have ati hardware and I heard that they weren't having that great of time with Edgy. Also the livecd of Edgy I burnt never made it past the bouncing progress bar screen (which I conclude is the fact that I think I burnt it too fast.)

But yah, Edgy worked great. I think for now I'm going to stick to Dapper until I plan out my next move.

---

### Post by johnny9794 on 2006-11-07
> **drewtown said:**
> I did a clean install of edgy and I'm pretty new to linux and it has gone exceptionally well, except getting beryl to work but that is its own beast.

If you are on a nvidia card 
[http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers)

if not then search
[http://forum.beryl-project.org/forum-5-howto](http://forum.beryl-project.org/forum-5-howto)

---

### Post by Athanasius on 2006-11-07
After fixing some resolution problems it is working allright for me  but I can't get crossover office to recognize windows disks.. other than that everything seems ok.

---

### Post by drewtown on 2006-11-07
> **johnny9794 said:**
> If you are on a nvidia card 
[http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers)

if not then search
[http://forum.beryl-project.org/forum-5-howto](http://forum.beryl-project.org/forum-5-howto)

Thanks a lot for the link I haven't seen that one I'll have to give it a try :)

---

### Post by heathenx on 2006-11-07
i had the same problem as you as far as the usplash disappearing on boot up. but i only had this problem on my old armada laptop. the other 5 computers that i installed edgy on worked just fine. i read somewhere that if you re-install the usplash it will work normally again.

as far as your computer shutting down, try adding acpi=off to your /boot/grub/menu.lst.

example:

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro acpi=off quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

---

### Post by CCBalla10 on 2006-11-28
[COLOR="Red"]I wasn't sure if i wanted to upgrade to Edgy because I had heard horror stories about it.  I decided to try it on my HP dv1000 and it works great!  After I installed it I had 13 updates to apply, so I figured they had fixed most of the unstableness of Edgy.  So I couldn't be happier.  Edgy is for me! :D[/COLOR]

---

