---
title: "Determining a package's actual installed size"
date: 2020-09-07
forum: General Help
---

### Post by davepool on 2020-09-07
I'm trying to determine the installed size of a package that insists on not showing up! Specifically, the Canonical product BlueMail.  It's installed and it's running. But none of the methods I've found seem to detect it.

I've read that using Synaptic Package Manager is good for this since it measures more than just the size of various directories...but BlueMail does not show up there (even with a search).

I've tried the "aptitude search" technique via command line....and, because I have a general idea of how big it is, I can tell it's not in the report.

I've tried the "dpkg query" string...same as above: many show up in the report, but not BlueMail.

OTOH, both of the above show libgli-mesa-dri and that one's a mystery.  Both of the above also return a bunch of linux-modules-extra-5.4.0-xx-generic (where xx is a two-digit number).

Any thoughts on how to get the installed size of this puppy?

---

### Post by deadflowr on 2020-09-07
I don't know of any bluemail package for Ubuntu except the snap version.
```
snap info bluemail
```

I also don't think bluemail is a Canonical [s]package[/s] Product.

EDit: I guess they (blix) does have a deb version ,but it's only downloadable from their website.
I don't see anything related in the Ubuntu repositories.

---

### Post by davepool on 2020-09-07
Yeah, all of what you're saying is what I've seen. In one particular installation, I had to use the .deb version (available on their web page) because the distro itself is not snap enabled.  But in the examples I'm referring to, BlueMail is installed in two Ubuntu and one Ubuntu-based distro. So I'm not having trouble *finding* the package for download or with *installing* it. It's there (all 3 examples) and I'm using it. It's in determining the installed size that I'm running into walls.

BTW, at the bottom of the BlueMail download page for the snap version it says:

[COLOR=#111111][FONT=Ubuntu]© 2020 Canonical Ltd.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu and Canonical are registered trademarks of Canonical Ltd.

Now, on reflection, that might very well be a "must have" disclaimer on a page that involves snap in any way.  So, apologies if I took that to mean BlueMail was somehow affiliated.[/FONT][/COLOR]

---

### Post by deadflowr on 2020-09-07
If installed from a deb
then
```
apt show <package-name-here> | grep Installed-Size
```
or
```
apt-cache show <package-name-here> | grep Installed-Size
```

---

### Post by davepool on 2020-09-07
Thank you for that.  And the results are displayed in.....kB?  For BlueMail I've got 224225.

---

### Post by TheFu on 2020-09-07
Simple answers to simple questions often don't turn out to be so simple.

Almost all commands on any Unix system will come with manpages.  These describe the command, options, and how to understand the output from the command. man apt-cache
>        show pkg...
           show performs a function similar to dpkg --print-avail; it
           displays the package records for the named packages.
So, the results are probably bytes, but the packager may be able to override any value they choose.

You can also look in  /var/cache/apt/archives/ for properly installed packages. Looking at firefox ... 
```
$ du -h firefox*
54M     firefox_80.0.1+build1-0ubuntu0.16.04.1_amd64.deb

$ apt-cache show firefox |grep Size
Installed-Size: 218943
Size: 56308150
Installed-Size: 104729
Size: 43192748

$ cd /usr/lib
$ du -sh firefox
214M    firefox

```

Packages are compressed.  Firefox is made up of a number of libraries, configs, scripts and multiple programs, but all from the same package.  When installed using APT (the total package management system [not referring to any specific program]), files get placed in a few different locations, so that /usr/lib/firefox/ directory isn't all there is.  After all, every who runs firefox gets their own settings inside their HOME. That's more storage being used which the users have control over with their individual settings, especially cache size.
The same would apply to email programs.

---

### Post by davepool on 2020-09-07
> **TheFu said:**
> Simple answers to simple questions often don't turn out to be so simple.

When installed using APT (the total package management system [not referring to any specific program]), files get placed in a few different locations, so that /usr/lib/firefox/ directory isn't all there is.  After all, every who runs firefox gets their own settings inside their HOME. That's more storage being used which the users have control over with their individual settings, especially cache size.
The same would apply to email programs.

I think....I _***think***_...that's why the benefit of using Synaptic was touted, because -- if I understood the article correctly -- its Installed column results tally up everything.  Problem is, BlueMail, though installed, wasn't showing up there.

In using your apt-cache command, I received this report for BlueMail:

Installed-Size: 224225 (same as reported above in my message #5)
Size: 57526462

So, which is what? I can certainly believe that BlueMail is 224 meg. No idea, though, what Size is reporting here.

[ADDED LATER] To get right to it, based on all you've said about how scattered the elements of a package can be, how can one compare two installed packages to make a determination of which one is using the most HD or SSD space?

---

### Post by TheFu on 2020-09-07
I've never heard of bluemail.  But I've only been running email servers since around 1995. We've always gone with F/LOSS answers and avoided proprietary code solutions.  I've self-hosted email since about 1998 for home needs.

Ah ... it is a client, but tied to their service?  I've been using some sort of email client from Netscape/Mozilla for decades now, except when outside company mandated MS-Exchange.

bluemail is proprietary. [https://github.com/bluemail](https://github.com/bluemail) and [https://github.com/gabrielxpanda/bluemail/releases](https://github.com/gabrielxpanda/bluemail/releases) 

I'd bet those are bytes (B), not KB and not MB.  Lowercase 'b', means bits most of the time, but for stuff like this, it would be bytes.

If you care that much about the size of a package, you'll likely not be happy with the way Ubuntu does stuff. This OS wastes storage all over the place, usually without asking or providing any real control for the local admin. That's a trade off between having a package manager and not having a package manager.  And since bluemail isn't provided as source, I don't see you repackaging it to make it smaller.  Plus, all Unix-like OSes need 1-2GB of extra space for temporary files or the system may crash.

---

### Post by davepool on 2020-09-07
I care generally only because I never like bloat, on my phone, on my computers, etc. But I care _*specifically*_ in only one instance: Back in January I picked up a used Lenovo ThinkPad 131e for just $40. It had already been converted to Linux (Linux Mint, it probably won't surprise you to know)...and it was only after I got it that I discovered there was also a m-SATA card installed....of a whopping 20gB!  The previous owner had apparently used it for storage.

But I got the idea that maybe this was a way to test out the speed of an SSD against the onboard HD with identical distros (the answer was: not much, really) and after that, I embarked on a search for a distro/DE that could actually fit on that card...and function through updates.  That last point was what killed every Ubuntu flavor I tried (and I tried more than Ubuntu), the last being Ubuntu MATE. I kept getting notifications that the pending update was going to require a gazillion terrabytes of space and I needed to make room for it. 

Ultimately, I landed on Zorin Lite for this particularly cozy installation...and it's working!  But with space being at a premium, I'd like to do what I can with apps to be economical. My usual email client is Geary...and it's pretty lightweight. But with some distros, Geary is really boggy.  So, for performance reasons alone, I decided to try BlueMail. And it's better, for sure (in terms of speed). But I'd sure like to have a handle on how big that thing is before I settle in with it.

---

### Post by TheFu on 2020-09-07
I've had a few chromebooks. They came with 16G SSDs.  I specifically bought models where the SSD could be replaced and did that.  120G and 64G.  With snaps, 16G just isn't enough and Canonical doesn't care about people with limited storage.

If your device has a USB port, you could insert a flash drive into it (ssd or normal flash), format it with f2fs and place your HOME onto it for more storage. 20G should be find for the OS.  Snaps will hate you, but we can avoid most of those still - except 3 that I'm aware which aren't provided in any other way.  Chromium is provided as a snap from the team behind it, but others have re-re-repackage chromium and put up a PPA.  Or just switch to Brave.  Firefox is still in the repos.  The only thing that I really want, without a snap is lxd, but Canonical refuses. The choice is to run a version from 2018 on 16.04 or to use the snap version which has many more capabilities, but baggage of the snap system and having updated forced down my throat without any reasonable method to control those.  Admin tools like LXD shouldn't force updates like a damn web browser, especially when a few of the updates broke working systems.

Can you not replace the mSATA storage?  I put some into my router a few months ago. Went from 8G to 32G (I think).  More router logs!

---

### Post by davepool on 2020-09-07
I might have been less than clear. I'm not stuck with that mSATA card as my only storage. The ThinkPad 131e comes with a 320gB HD so I'm not challenged for space in that regard. In fact, that drive now hosts Kubuntu and Linux Mint installations. And for those, the size of a package doesn't matter to me.

BTW, here's some product copy about that HD installation (because of the education market that the ThinkPad "e" devices were designed to serve): [COLOR=#555555][FONT=Lato]For models with traditional hard drives, an accelerometer detects movement and stops the drive when a fall or similar event is detected. Rubber mounts are used for the hard disk drive (rather than rails) and the HDD connector is not rigidly attached to the board, so the connector absorbs shock and impact and protects against system damage.[/FONT][/COLOR]

I alternate between Brave and Vivaldi. I usually install both. I keep Firefox only because it's usually already there (same as LibreOffice but, in that case, I uninstall that beast). 

I was ready to replace that mSATA card with something larger....until I got down to the task and found that even with a little WD-40 the screws were not budging and I was close to rounding them off or doing other damage.  Because that card is more of a fool-around thing for me and not crucial to running the device, I just decided to forget it.

---

### Post by TheFu on 2020-09-08
> **davepool said:**
>  
I was ready to replace that mSATA card with something larger....until I got down to the task and found that even with a little WD-40 the screws were not budging and I was close to rounding them off or doing other damage.  Because that card is more of a fool-around thing for me and not crucial to running the device, I just decided to forget it.

Thanks for that. Gave me a chuckle this morning.  I've been foiled by a screw this month too!  Sadly, mine was because I'm an idiot and couldn't remove a drive cage. Rather than checking for some other screw that I'd missed - the cage was sliding in any partially out - my brain decided that there was a metal catch somewhere that needed to be depressed to get over some lip/curb on the way out.  Of course, it never worked because there was a screw holding the cage still. Probably spent 2 hrs gently sliding that cage in and out before giving up for the day.  The next day, decided to spin the case around and got a different view; with the screw very clearly seen, this time.
For spinning disks in laptops, I've been lucky and swapped out soon-to-fail disks before they fail.  320G --> 500G --> 750G.  The 750 is a WD-black with 5 yr warranty. Those are tanks compared to Blue desktop models which have always failed within 4-5 yrs in my experience.  I need to check that 750G SMART data. It doesn't run Linux, so that's a bit of a hassle to me. All my other systems are Linux, so SMART reporting is automatic every week.

---

