---
title: "Having problems adding PPA's; system can't seem to find them..."
date: 2015-04-05
forum: General Help
---

### Post by Mike_Walsh on 2015-04-05
Evening, everybody.

I've decided to change my main system from Ubuntu to Xubuntu. I've recently upgraded my CPU from a single-core Athlon 64 to a dual-core X2, and thought by changing to the lighter Xubuntu (which I really like, having experimented with it in the past), that it should help to speed things up even more.

Current system specs; Athlon 64 X2 3800+ dual-core CPU @2 GHz
                               3 GB RAM
                               WD 160 GB 'Caviar' Black
                               ATI Radeon Xpress 200 integrated graphics chip

I was right; it HAS speeded things up nicely, and the system is much more responsive now. The installation's gone really well; totally straight-forward & fuss-free, as you would expect.

I'm having a couple of problems, however. I want to install the current version of pSensor; 1.02 (psensor-unstable). Sounds dodgy, but I've been using it for nearly a year now, and it is in fact very stable; gives no problems at all. This version lets you put your readings into the taskbar, unlike the older version in the repos, which only shows you a graph. It means adding a PPA; I've always been able to add this quite easily by following the very clear instructions from here:-

[http://www.webupd8.org/2014/06/psensor-updated-with-option-to-display.html](http://www.webupd8.org/2014/06/psensor-updated-with-option-to-display.html)

Now, however, no matter how many times I enter the PPA info, it keeps telling me that the PPA can't be located, and to 'check my spelling', and also to make sure I've got the format correct...

I'm also attempting to install the beta version (1.7) of Wine, in order to use a small graphics app called PhotoScape, which I haven't been able to find an equivalent for in Linux.....not without installing half-a-dozen others to obtain the same degree of functionality. It runs perfectly in Wine; has the coveted 'Platinum' rating...and in fact it was I who submitted the review on the newest version of this app to the WineHQ database:-

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=31074](https://appdb.winehq.org/objectManager.php?sClass=version&iId=31074)

As you can see from the other reviewer, it doesn't run as well under the version of Wine in the repos. I normally install Wine, following the instructions from here:-

[https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu)

...but, once again, the PPA refuses to show up in the Software & Updates 'sources' window. I've installed most of the 'buntus several times during the latter half of last year, and have got into a steady routine with my installs. I can't help feeling I've forgotten to do something, somewhere along the line.....does anybody have any ideas what it could be? I re-installed using my old Xubuntu 'Trusty' LTS disk from last year...I'm not one of these who wants the 'latest & greatest' every 6 months...stability is far more important to me; the update, to bring it up to 14.04.2 spec took about 70 MB; but over the course of the last year, Ubuntu must have had several GBs of updates, to reach the same point. I'm wondering if some critical library or something has got missed out in the process...

Or has the format for adding PPAs in the terminal changed in the last few months.....from the usual 'sudo add-apt-repository, etc...'?

Any suggestions will, as usual, be much appreciated.


Regards,

Mike. :)

---

### Post by mc4man on 2015-04-05
>  I want to install the current version of pSensor; 1.02 (psensor-unstable). Sounds dodgy, but I've been using it for nearly a year now, and it is in fact very stable; gives no problems at all. This version lets you put your readings into the taskbar, unlike the older version in the repos, which only shows you a graph. It means adding a PPA; I've always been able to add this quite easily by following the very clear instructions from here:-

[http://www.webupd8.org/2014/06/psens...o-display.html](http://www.webupd8.org/2014/06/psens...o-display.html)

Now, however, no matter how many times I enter the PPA info, it keeps telling me that the PPA can't be located, and to 'check my spelling', and also to make sure I've got the format correct...
So this does not offer to add the ppa?
```
sudo add-apt-repository ppa:jfi/psensor-unstable
```

---

### Post by Mike_Walsh on 2015-04-05
Hallo, mc4man.

It doesn't appear as though it wants to any longer. When I attempt to add it (in the terminal, as usual), this is what I get:-

```
paul@mic-w:~$ sudo add-apt-repository ppa:jfi/psensor-unstable
[sudo] password for paul: 
Cannot add PPA: 'ppa:jfi/psensor-unstable'.
Please check that the PPA name or format is correct.
paul@mic-w:~$ 
```

I HAVE checked it.....repeatedly. Unless I'm suddenly going word-blind, I don't see what else I CAN check..! And the format looks absolutely spot-on to me. When I try adding the ubuntu-wine PPA, I get the same:-

```
paul@mic-w:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for paul: 
Cannot add PPA: 'ppa:ubuntu-wine/ppa'.
Please check that the PPA name or format is correct.
paul@mic-w:~$ 
```

And that IS correct! See for yourself:-

[https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu)

I've never come across this problem before, personally.....although I do recall, at times, having come across other people on the forums who appear to have had something going on along the same lines. Can't track any down at the moment, however.

What do you think? Any ideas? I'm still leaning toward the theory that some critical piece of system data is missing...but it says it's 'up-to-date'...(!)


Regards,

Mike. :confused:

---

### Post by sandyd on 2015-04-05
Possibly: [http://www.webupd8.org/2014/03/fix-cannot-add-ppa-please-check-that.html](http://www.webupd8.org/2014/03/fix-cannot-add-ppa-please-check-that.html)

I've encountered a few other causes including a bad dns resolver and ipv6.

---

### Post by Mike_Walsh on 2015-04-05
sandyd, you're a blooming marvel! That link appears to have fixed it.

I don't understand HOW, since it clearly stated that nothing was added, and nothing was removed.....but here's your proof that it's done SOMETHING:-

```
paul@mic-w:~$ sudo apt-get install psensor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  psensor-common
The following NEW packages will be installed
  psensor psensor-common
0 to upgrade, 2 to newly install, 0 to remove and 10 not to upgrade.
Need to get 118 kB of archives.
After this operation, 876 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu/ trusty/main psensor-common all 1.1.2-1ppatrusty1 [53.1 kB]
Get:2 http://ppa.launchpad.net/jfi/psensor-unstable/ubuntu/ trusty/main psensor amd64 1.1.2-1ppatrusty1 [64.5 kB]
Fetched 118 kB in 0s (535 kB/s)
Selecting previously unselected package psensor-common.
(Reading database ... 182252 files and directories currently installed.)
Preparing to unpack .../psensor-common_1.1.2-1ppatrusty1_all.deb ...
Unpacking psensor-common (1.1.2-1ppatrusty1) ...
Selecting previously unselected package psensor.
Preparing to unpack .../psensor_1.1.2-1ppatrusty1_amd64.deb ...
Unpacking psensor (1.1.2-1ppatrusty1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 added doc-base file...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up psensor-common (1.1.2-1ppatrusty1) ...
Setting up psensor (1.1.2-1ppatrusty1) ...
paul@mic-w:~$ 
```

So; something in the ca-certificates list must have downloaded slightly out-of-whack, when I installed this morning. I'm presuming it's simply replaced the list, as is. But it's done the trick...

They say the 'proof of the pudding is in the eating', don't they...

[ATTACH=CONFIG]261113[/ATTACH]

That's VERY much appreciated. Thank you! I'll mark this as 'solved'; I only wish a lot of the other problems that crop up on the Forums were as easy to fix...


Regards,

Mike. :D

---

