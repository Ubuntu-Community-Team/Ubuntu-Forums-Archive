---
title: "Firefox in Ubuntu 16.04 LTS"
date: 2016-05-05
forum: General Help
---

### Post by Mike_Andrews on 2016-05-05
Firefox is behaving aberrantly in html issues that deal with draw and render; my guess is that the system is infected with a malware, although it's a fresh install from an overwritten Ubuntu 15.10 Wily. 
The media used for the present system (16.04 LTS) was ordered from OS Disk dot com, who seem credible. I didn't download and burn the iso myself.
But the new 16.04 has been very problematic so far and I'm wondering if a complete uninstall of firefox followed by reinstall may solve the draw and render issue and delete whatever bug is causing it?
I did install AdBlocker Ultimate in Firefox, although that shouldn't cause any problems.
To be concise, there's nothing abnormal in the functioning of Firefox as far as accessing websites nor of draw-render are concerned; the issue is only apparent when first loading Firefox from the Unity launcher and clicking on the Bookmarks (or any) option listed in the Browser pane. That's when a long, tell-tale rectangular (digital) bar juts down initially as prelude to the launching of the menu just clicked. It's difficult to describe, but suffice it that this type behavior is extremely reminiscent of old Windows builds that were infected with a Cool Web Search trojan (CWS), which was very common from the late 1990's to about the time when Vista first shipped. 
I recently used Synaptic Package Manager to remove and reinstall Firefox, but as in Macintosh systems that use plists, the new version of Firefox came back again already coded and set up like its predecessor.
. . . It was anything BUT a fresh install.
So -- my need is for a Terminal command that will completely remove firefox from its current active state, that it can be reinstalled fresh. That way it will become evident whether Firefox is the sole source of the problem or if the bug is operating at the system level. 
I tried doing the removal with various methods using Terminal but as I'm fairly new to Linux my knowledge of Terminal is limited. I know only the most basic commands under apt.
Right now it looks as though a bare-metal wipe of the drive may be in the works, which I will accomplish via manual removal of the HD from its laptop home and connecting it via tether to an older, Jobs-era Mac system - then running a secure, 3-pass random overwrite.
Will someone please offer a ray of hope B4 I do?

Thanks

---

### Post by ajgreeny on 2016-05-05
*Thread moved to **General Help**.*  This is not a multimedia software problem.

Try running command ```
mv .mozilla .mozilla-backup
``` in terminal; this will rename your current profile and it is that which contains all the extensions you are using, if any, all your baookmarks and the complete configuration of FF that you are using at the moment.

If you do not sync your bookmarks online, you will find a backup file of your bookmarks in that backup folder.  You can see that folder if it does nor normally show in the file manager by using keys Ctrl+H, to show all hidden folders and files.

Reinstalling firefox seldom solves problems such as this, as a reinstall will still be using the same old profile.

---

### Post by Mike_Andrews on 2016-05-06
. . . Couldn't locate the post in General Help.
I tried what you suggested, ajgreeny; thanks, but NOTHING seems to have happened at all. No change in Firefox' aberrations. No bells, no whistles.
But now, happily, there is more information in re underlying cause of the aberrant behavior in Firefox and T-bird.
Firewall Sundry (a front-end) is the problem, or at least directly related to it. I'm positive.
Initially the gufw was my pick, as it had pretty much become the standard in Ubuntu 14.04 LTS and it worked very well. It was reliable. I always used it because of the pretty little blue-and-white shield.
Kidding.
But in Ubuntu 16.04, gufw doesn't even install, although the package goes through the semantics of installation. 
So, falling back to the next-best, I ran the installer for (brick wall icon) Firewall Sundry. 
The installation hangs but following a system reboot it seems to be installed -- and that's when the problems return. There's no un-installing it. Once you run the package, it's carved in granite, although it has SUPPOSEDLY been removed.
Not according to Firefox, however. Same abnormalities with html over-runs.
I made it a point to confirm, following installation this time. . . that Firefox was acting normally. It was. Then came Firewall Sundry. A bbbig bbbump.
So, unquestionably, this SUNDRY front-end is doing some weird things to the html coding in Firefox and seems to be killing smtp in T-bird.
. . . Because yesterday I sent off an email to myself, consisting of a list of SHA-1 and MD5 hashes for the Ubuntu 16.04 ISO just downloaded, as it would have been a simple matter to run SHA-1 and MD5 verifications of the installer package in a Mac computer B4 reinstalling Ubuntu 16.04 the second time on my System76 laptop. 
The email never arrived. 
There's a copy of it in my Sent Messages folder stored on the Yahoo server; but if it was sent from yesterday's install I've no idea where it went, nor who received it, as it never arrived in my Inbox.
Am now wiping a spare sata  laptop-HD in preparation for the third install of Ubuntu 16.04.
. . . Wish someone from the Dev community would put out a feeler. I might be persuaded to wait and maybe keep things as they are, anticipating a fix.
Short of that the third install is a done deal. I only have four other computers, so this is critical. Not.
But it would make me very happy to learn that, here at the end of Western civilization as we've known it, Linux remains sacrosanct.
I fear that such hopes fall into the pipe dreams category.
And besides, Linus Torvalds pretty much let the cat out of the bag recently when nodding YES but saying no to the question, "is there a backdoor in Linux?" Everyone at the press luncheon laughed, but it was a dead serious issue and they all knew it.
As a completely uninteresting and ordinary person it's hard to conceive of the alphabet-soup-three-letter faction showing interest in me, or that any competent black hat would want to steal my identity. 
So I say. . . if you want to pretend you're me, leave a note with your name and address and I'll send you a bouquet of flowers, a thank-you letter and a sympathy card.
Thanks,  ajgreeny  for your help and I regret posting to the wrong forum.
Peace.

---

### Post by ajgreeny on 2016-05-07
I have never heard of nor come across Firewall Sundry, but I can tell you that to run **gufw** you need to make sure that **python-gobject** is installed as well as **python-gobject-2**.  This will also pull in **python-gi** which provides a missing module otherwise missing in 16.04.

I found this by installing gufw in my VM of 16.04 and trying to start it; nothing happened and no gufw appeared, just an error saying ```
ImportError: No module named gi
```
A quick search found the missing culprit in thread [http://ubuntuforums.org/showthread.php?t=2218506](http://ubuntuforums.org/showthread.php?t=2218506)

If you prefer to use gufw as you used to, that is the way I suggest you go.

There is a launchpad bug lodged already about this which you might like to add your name to.
[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1573567](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1573567)

---

### Post by maglin2 on 2016-05-07
By Firewall Sundry I believe the OP means Firewalld [http://www.firewalld.org/](http://www.firewalld.org/)

It is just called Firewall in Gnome Software Centre, but is tagged Sundry

---

### Post by Mike_Andrews on 2016-05-07
It seems there may be a plethora of bugs in this new 16.04 build, each affecting its predecessor.
Originally trying to launch firewalld (sundry) and finding that this front-end has negative effects on Firefox and T-bird, I removed firewalld, or at least attempted to -- the negative effects yet linger -- and installed gufw. 
Gufw still refuses to load onto Desktop, making it impossible to work with.
Thanks to maglin2 and ajgreeny for their input and I've tried the simple solution, sudo apt-get install python go-object && apt-get install python go-object-2, with the following result:
```
mike@mike-Kudu-Professional:~$ sudo apt-get install python-gobject && sudo apt-get install python-gobject-2
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gobject is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-gobject-2

E: Package 'python-gobject' has no installation candidate
mike@mike-Kudu-Professional:~$ sudo apt-get install python-gobject-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gobject-2 is already the newest version (2.28.6-12ubuntu1).
python-gobject-2 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up amavisd-new (1:2.10.1-2ubuntu1) ...
Creating/updating amavis user account...
Job for amavis.service failed because the control process exited with error code. See "systemctl status amavis.service" and "journalctl -xe" for details.
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: error processing package amavisd-new (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 amavisd-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@mike-Kudu-Professional:~$
``` 
-------------------------------------------------------------
 amavisd-new seems to be the bad penny that keeps turning up.
. . . Have attempted to install, yet get same advisory, i.e., that there is no installation candidate.
It's as if the packages cannot be activated by the system installer, just as would be the result if a user doing a manual installation of a package forgot to first tic the little box under Properties allowing the pkg to run as a program.
I have no idea how to check on this and will await a fix from gufw's daddy.
But here's the latest Terminal output:

```
mike@mike-Kudu-Professional:~$ sudo apt-get install python-gi
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-gi' has no installation candidate
mike@mike-Kudu-Professional:~$ sudo apt-get -f install python-gi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gi is not available, but is referred to by another package. [i.e. amavisd-new] my interpolation
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-gi' has no installation candidate
mike@mike-Kudu-Professional:~$
```

Got it!
Rather convoluted process, involving Synaptic P.M. 
After reloading all packages in Synaptic and running search for python-gobject a second time it came up with multiple items rather than the one that had appeared B4 reloading the package cache. 
So the developers have evidently been very busy these past 24.
amavis.service (related to Clamav) still doesn't work; but after marking for install on additional packages listed in Synaptic, despite errors and a continuing problem with amavis.service & related, gufw now loads and is opening fine.
I'm a happy camper.
Aberrant behavior in Firefox and T-bird may now possibly disappear. 
Hope springs eterne. . . ha!
If not, another SATA drive is ready, although after all these problems with 16.04 LTS I will probably go back to the tried-and-proven 14.04 LTS and wait a bit.
But ajgreeny. . . thanks again, although I tried the fix at the link you offered and it didn't help.
I believe reloading Synaptic cache and installing from there is key, as that brings into play missing pkgs.
. . . Just type python-gobject into a search box in Synaptic and if only one or two lines of entries appear, reload the package cache (top-left).
After Synaptic finishes, install everything related to python-gobject (everything in the list) and if you've been having a problem getting gufw to appear, this should fix it.
Fair winds to all.

---

### Post by ajgreeny on 2016-05-08
Before you install any packages from the repos, whether using synaptic, software-centre or just the command-line you should ALWAYS refresh the repos or you may find many problems.  I nearly always use synaptic, never use the software-centre, and also use terminal with **apt-get install** command, now just **apt -install** in 16.04, I think.

I am glad the gufw package is now working as it should.

Please mark as SOLVED from the Thread Tools menu at the top if this really is solved for you.

---

### Post by Mike_Andrews on 2016-05-08
My thanks again to ajgreeny and maglin2 for their considerations.
M.

---

