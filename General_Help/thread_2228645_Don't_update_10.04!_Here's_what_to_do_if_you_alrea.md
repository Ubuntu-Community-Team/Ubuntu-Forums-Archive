---
title: "Don't update 10.04! Here's what to do if you already did."
date: 2014-06-08
forum: General Help
---

### Post by Randy M on 2014-06-08
The latest updates to 10.04 cause problems with online activities. Thunderbird, Firefox, and Opera are all affected. There are probably more. You have two options at this point. First, you can upgrade to 12.04. That should be an option in update manager. Or, you can roll back the update and continue with the previous version. Both have a couple of drawbacks. Upgrading to 12.04 (or higher) may slow down older hardware. It did in my case. Remaining with the previous version will prevent any future updates.
 
If you wish to roll back to the point prior to the latest updates, install Grub Customizer and move the previous version to the top of the list. The first version listed (you'll want the one that lists 60 as the first one) is the one that boots automatically. You can find more on Grub Customizer here [http://launchpad.net/~danielrichter2007/+archive/grub-customizer](http://launchpad.net/~danielrichter2007/+archive/grub-customizer)

Other posts on this subject can be found here.
[http://ubuntuforums.org/showthread.php?t=2228304](http://ubuntuforums.org/showthread.php?t=2228304)
[http://ubuntuforums.org/showthread.php?t=2228459](http://ubuntuforums.org/showthread.php?t=2228459)
[http://ubuntuforums.org/showthread.php?t=2228265](http://ubuntuforums.org/showthread.php?t=2228265)

---

### Post by monkeybrain20122 on 2014-06-08
It is very bad advice to not to update 10.04. It is unsupported (therefore security risk) and all the software is very outdated.  It is a vastly suboptimal computing experience comparing to what is available now.

On the other hand don't go the route of "upgrade", always back up your data and do a fresh install of a supported version of *buntu, it is a lot faster and a lot less problematic.

---

### Post by mörgæs on 2014-06-08
Threads mentioned in original post have been merged.

Besides, +1 to what Monkeybrain writes.

---

### Post by Randy M on 2014-06-08
I understand that the unsupported version may have some security risk, but users are picky. Not all users are power users ready to dive in to command line processing and learning the latest and greatest system. Many users treat computers like a toaster. They want toast, not new ways to make toast. One of the users that I helped with this problem is 60, a cancer survivor, and has several other health problems. He doesn't like change. He just wants to read his mail, check on his kids and grandkids on facebook, and do a couple of other things online. Installing a new version, updating the GUI, and making the changes necessary to keep going are beyond him. I converted him to Ubuntu years ago to prevent some of the malware issues he was facing with Windows. There have been a lot of comments saying that users should upgrade, but none explaining why an update was released that would shut a system down without warning. Some have said it was because 10.04 server edition is still valid. Was a simple check to see what was installed too much to ask? Can Ubuntu not tell what it's about to over-write? I've only been a software developer for 30 years (application, not OS), but it appears to me that some kind of check should be possible. In any case, the systems I help with (friends and family) are up and running again. I hope yours fare as well in the future.

---

### Post by Bucky Ball on 2014-06-08
Without security updates for over a year your friend could end up with a lot more problems than you currently envisage. No security updates = security vulnerability. That 10.04 LTS machine shouldn't even be online.

Why not Xubuntu 12.04 LTS or 12.04 LTS with Gnome? I have no idea why you think upgrading to a newer version means you need to become some sort of terminal/coding guru. Did you need to do that to install 10.04 in the first place?

Good luck with it all. The only updates you will be getting are for things like Firefox, Opera and Thunderbird so your questions really are about that. Newer versions of these will probably not work with 10.04 so you may have no choice but to upgrade eventually ...

---

### Post by grahammechanical on 2014-06-09
Ubuntu 10.04 was an LTS release and it most certainly possible to upgrade from one LTS to the next. It is indeed an option in Update manager and has been there since 12.04 LTS was released. But we cannot get from 10.04 LTS to 14.04 LTS without going first to 12.04 LTS.

There is a big code difference between 10.04 and 12.04. To start with the Gnome developers stopped working on Gnome 2 and its Gnome 2 panel user interface and switched to Gnome 3 and its Gnome 3 shell. Ubuntu now uses Gnome 3 but with the Unity user interface that was developed by Ubuntu developers.

In many ways there is also a big code difference between 12.)4 and 14.04. Life moves on.

An OS does not slow down older hardware. It will push older hardware harder and it may prove to be that the hardware cannot cope with the demands of the newer OS. This is especially true of the graphic adapter. This is a fact of computing life.

Many of us recommend a fresh install rather than an upgrade. I have Ubuntu on hardware that is more than 5 years old and I am happy but I recognise that Xubuntu and Lubuntu can be better choices for certain hardware.

---

### Post by pretty_whistle on 2014-06-09
I migrated from Windows in 2011 to Ubuntu.  I've upgraded every time an upgrade has been available and I haven't noticed anything bad happening nor have I had to learn things all over again.  So I don't understand what you mean either.

---

### Post by Niets on 2014-06-09
> **Bucky Ball said:**
> Without security updates for over a year your friend could end up with a lot more problems than you currently envisage. No security updates = security vulnerability. That 10.04 LTS machine shouldn't even be online.

Why not Xubuntu 12.04 LTS or 12.04 LTS with Gnome? I have no idea why you think upgrading to a newer version means you need to become some sort of terminal/coding guru. Did you need to do that to install 10.04 in the first place?

Good luck with it all. The only updates you will be getting are for things like Firefox, Opera and Thunderbird so your questions really are about that. Newer versions of these will probably not work with 10.04 so you may have no choice but to upgrade eventually ...

Actually, 10.04 continues to update nicely.  The Linux kernel updated this week and the lib modules continue to receive regular updates also.  Not sure why all the naysayers.  I'm sure there are some items from 10.04 not being updated but it's not like updates are not happening.  I'm can understand those that like to do a fresh install on a new Ubuntu version, but I can only think the depth of the installation must be pretty shallow.  I can't see reinstalling all the VPN, FTP, Wine, Virtualbox, email (5 accounts), etc. settings for each new install.  Not to mention the dozens of applications and tweaks involved with a heavily used system.  I also don't see new versions of Ubuntu offering me anything that superior to what I am running now in 10.04 although I am partial to Gnome 2 and Compiz.  I do run each new release on a test machine as well as other distros.

That said, the newest updates received yesterday on 10.04 shut down my keyboard and mouse clicks.  (Mouse pointer moves but no clicks registering from the buttons.)  Anyone car to speculate on why and how to fix?  Been doing allot of forum searching this morning and can't find anything definitive.

---

### Post by Bucky Ball on 2014-06-09
Did you install the server version? That is supported for five years, until 2015. Sure sounds like it if you're getting kernel updates ... :-k

---

### Post by pretty_whistle on 2014-06-09
> **Niets said:**
> Actually, 10.04 continues to update nicely.  The Linux kernel updated this week and the lib modules continue to receive regular updates also.  Not sure why all the naysayers.  I'm sure there are some items from 10.04 not being updated but it's not like updates are not happening.  I'm can understand those that like to do a fresh install on a new Ubuntu version, but I can only think the depth of the installation must be pretty shallow.  I can't see reinstalling all the VPN, FTP, Wine, Virtualbox, email (5 accounts), etc. settings for each new install.  Not to mention the dozens of applications and tweaks involved with a heavily used system.  I also don't see new versions of Ubuntu offering me anything that superior to what I am running now in 10.04 although I am partial to Gnome 2 and Compiz.  I do run each new release on a test machine as well as other distros.

That said, the newest updates received yesterday on 10.04 shut down my keyboard and mouse clicks.  (Mouse pointer moves but no clicks registering from the buttons.)  Anyone car to speculate on why and how to fix?  Been doing allot of forum searching this morning and can't find anything definitive.
You got the updates ok but now you have a messed up mouse and keyboard.  I'm sure someone will say it happened because you need to upgrade.

I dont know why someone would do a fresh install unless they're forced into it because, as you said, they have reinstall everything and that's a lot of trouble.  Personally I've always just upgraded and never fresh installed.  It's too much trouble.

---

### Post by Randy M on 2014-06-09
> **Niets said:**
> That said, the newest updates received yesterday on 10.04 shut down my keyboard and mouse clicks.  (Mouse pointer moves but no clicks registering from the buttons.)  Anyone car to speculate on why and how to fix?  Been doing allot of forum searching this morning and can't find anything definitive.

Hold down the left shift key when you boot and see if the Grub menu is displayed. You can then pick the previous version and go back a step. It's not a real fix, but considering the responses I've been getting, a fix isn't going to happen.

---

### Post by monkeybrain20122 on 2014-06-09
> **Niets said:**
> Actually, 10.04 continues to update nicely.  The Linux kernel updated this week and the lib modules continue to receive regular updates also.  Not sure why all the naysayers.  I'm sure there are some items from 10.04 not being updated but it's not like updates are not happening.  I'm can understand those that like to do a fresh install on a new Ubuntu version, but I can only think the depth of the installation must be pretty shallow.  I can't see reinstalling all the VPN, FTP, Wine, Virtualbox, email (5 accounts), etc. settings for each new install.  Not to mention the dozens of applications and tweaks involved with a heavily used system.  I also don't see new versions of Ubuntu offering me anything that superior to what I am running now in 10.04 although I am partial to Gnome 2 and Compiz.  I do run each new release on a test machine as well as other distros.
.

The more heavily tweak your system is, the more likely that 'upgrade' will break and the more important that you do a clean install. And the longer you put it off, the harder migration will be, and the longer you use an unsupported OS, the more problems will emerge.

Don't expect people to help you trouble shoot an OS which has been long dead (the Desktop Edition for 10.4 is dead for more than a year, those updates are meant for server)

---

### Post by Niets on 2014-06-09
> **Bucky Ball said:**
> Did you install the server version? That is supported for five years, until 2015. Sure sounds like it if you're getting kernel updates ... :-k

Nope.  No server version (good thought).  Maybe someone else with 10.04 will chime in with what they are seeing.

But, no keyboard and mouse remain the issue.

---

### Post by Randy M on 2014-06-09
> **Bucky Ball said:**
> Did you install the server version? That is supported for five years, until 2015. Sure sounds like it if you're getting kernel updates ... :-k

No, I've never installed the server version. It also seems unlikely that all of the people reporting problems installed the server version. Kernel updates were provided to an unsupported desktop version. The most likely explanation is that the developers released kernel updates for the server version and didn't bother to check to see if they were about to be improperly applied to desktop installations. A simple case of "Ready, Fire, Aim."

---

### Post by Niets on 2014-06-09
> **monkeybrain20122 said:**
> 
Don't expect people to help you trouble shoot an OS which has been long dead (the Desktop Edition for 10.4 is dead for more than a year, those updates are meant for server)

I'm not actually expecting help (thought there might be a quick fix I overlooked) but thought I would mention while correcting miss-information being spread about 10.04 not updating.

---

### Post by bapoumba on 2014-06-09
> **Randy M said:**
> No, I've never installed the server version. It also seems unlikely that all of the people reporting problems installed the server version. Kernel updates were provided to an unsupported desktop version. The most likely explanation is that the developers released kernel updates for the server version and didn't bother to check to see if they were about to be improperly applied to desktop installations. A simple case of "Ready, Fire, Aim."
It is not a matter of checking or caring or not. The desktop version has gone unsupported for a year. In an ideal world, no one should be using it any longer and everyone should have upgraded already to a supported desktop release.

Now if things are broken on the server edition, that is worth a bug report (I have not read all the threads over so that may have already been done).

---

### Post by monkeybrain20122 on 2014-06-09
> **Niets said:**
> I'm not actually expecting help (thought there might be a quick fix I overlooked) but thought I would mention while correcting miss-information being spread about 10.04 not updating.

There is no misinformation. It is not updating except for packages common to the server edition. It is beyond all reasonableness to go through such great length and troubles to stay in the past and rationalize it just to avoid learning a few new tricks and maybe an afternoon of setting up a new system. :)

---

### Post by Niets on 2014-06-09
> **monkeybrain20122 said:**
> There is no misinformation. It is not updating except for packages common to the server edition. It is beyond all reasonableness to go through such great length and troubles to stay in the past and rationalize it just to avoid learning a few new tricks and maybe an afternoon of setting up a new system. :)

Apologies.  I stand corrected.  I was trying to make the point that those of us that do not need the latest and greatest and are still running 10.04 are seeing a substantial amount of updates coming through for not only applications but core Linux components including the kernel and many of the libs.  Those not running 10.04 have assumed that there are no updates at all and that would be incorrect.

As I stated, I run all the new releases on a separate machine.  Personally I haven't found any compelling reason to upgrade other than the lack of Conical support.

---

### Post by Randy M on 2014-06-09
> **monkeybrain20122 said:**
> It is beyond all reasonableness to go through such great length and troubles to stay in the past and rationalize it just to avoid learning a few new tricks:)

Perhaps a better explanation from a simple users perspective is in order. Go rearrange your wife's kitchen cabinets. Tell her the new way is better and she has to get used to it. Let me know how that works out for you.[IMG]http://ubuntuforums.org/images/icons/icon10.png[/IMG]

---

### Post by deadflowr on 2014-06-09
It isn't just updating server packages, but core packages, like the kernel.
The problem lies in it is no longer dealing with supporting the desktop packages.
So no testing the new core packages against the desktop packages, since they no longer need to be tested together.
So the breakages of late should come as no surprise at all.
Anyway, that's how I see the cookie as crumbling...

---

### Post by bapoumba on 2014-06-09
Please keep the thread on tracks, thanks (not talking to you deadflowr).
.

---

### Post by Niets on 2014-06-11
> **Randy M said:**
> Hold down the left shift key when you boot and see if the Grub menu is displayed. You can then pick the previous version and go back a step. It's not a real fix, but considering the responses I've been getting, a fix isn't going to happen.

I hope this isn't diverging too far from the original topic but wanted to add a conclusion for the knowledge base-

Although holding the shift key did not work as the keyboard was ineffective by that time (thank you for the idea), it got me to thinking that the boot file could be altered to stop on the grub screen.  Booting from CD and editing the line "set timeout=10" to "set timeout=-1" in grub.cfg did the trick and let me roll the kernel back from 2.6.32-61 to 2.6.32-60 and everything is fine.  No one should be really be editing grub.cfg directly, but when you don't have a keyboard working to run "update-grub" there is not much else I could do.  I'm still deciding how to make this change permanent so I don't have to stop on the grub screen every time or the updates for 2.6.32-61 are corrected to not interfere with USB operations.  (Mouse and keyboard weren't the only problem.  Anything connected via USB suffered on this update.) Yes, long term is to get current on my version, but at least now I can get into my 10.04 to retrieve all the settings for VPN, RDP, FTP, mail, etc.

And there have been quite a few issues with this last kernel update -
[http://ubuntuforums.org/showthread.php?t=2228206](http://ubuntuforums.org/showthread.php?t=2228206)

---

### Post by Bucky Ball on 2014-06-11
You should edit this file:

```
sudo nano /etc/default/grub
```

You can change timeouts there, then:

```
sudo update-grub
```

That will write the changes to .cfg. Done. ;)

---

### Post by Niets on 2014-06-12
> **Bucky Ball said:**
> You should edit this file:

```
sudo nano /etc/default/grub
```

You can change timeouts there, then:

```
sudo update-grub
```

That will write the changes to .cfg. Done. ;)

Agreed, but the problem is no working keyboard and mouse which makes the update difficult.  /etc/default/grub can be edited after booting another distro from CD but running "update-grub"will not have the desired effect as it is trying to update grub from the live CD OS.  Maybe there is something that I missed to force the grub update to the install on the hard drive, but all I could think of was to edit  grub.cfg directly.  I would be interested to know if there is another option I missed.  I then purged the 2.6.32-61 kernel and updated grub.

---

### Post by bapoumba on 2014-06-12
Update : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1327300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1327300)
Looks like if you enable the -proposed repositories ([https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)) and upgrade the kernel to 2.6.32-62.125 it fixes the issues. See here for ex : [http://ubuntuforums.org/showthread.php?t=2229309](http://ubuntuforums.org/showthread.php?t=2229309)

From the bug report : 
> This bug is awaiting verification that the kernel in -proposed solves the problem. Please test the kernel and update this bug with the results. If the problem is solved, change the tag 'verification-needed-lucid' to 'verification-done-lucid'.

If verification is not done by 5 working days from today, this fix will be dropped from the source code, and this bug will be closed.
So you have 5 days from today to confirm in the bug report that is fixes the issue for the fixed kernel to go to the main repos, otherwise the fix will be dropped.

Please keep in mind it would be better to move to a suported desktop release.

---

