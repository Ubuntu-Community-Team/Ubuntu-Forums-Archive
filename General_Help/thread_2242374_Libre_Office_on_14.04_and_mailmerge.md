---
title: "Libre Office on 14.04 and mailmerge"
date: 2014-09-01
forum: General Help
---

### Post by Richard_York on 2014-09-01
I've just installed 14.04, with a clean reformat, after a year enjoying most aspects of 12.04 - much better than M$ XP - and hoping that the latest Libre Office would again let me use spreadsheets as address sources for mail-merged letters & emails for my work. It used to to this, but recently stopped.

Frustration - still can't register my spreadsheet as an address list. 
L O Help tells me to open File - Wizards - Address Data Sources. In earlier versions,  this used to appear, but now it doesn't, not even greyed out, so no option there.

I note that 14.04 didn't include L O Base in the package, is this the problem?

Please does anyone have a solution? Last time round I think I eventually updated L O straight from their own site, but gather this was probably the cause of some problems I had with it later, so I don't want to introduce stuff which is going to upset things - I don't understand enough to rescue them!

Any help gratefully received, thank you.

I'm using AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2; 2 GiB Memory; 32 bit OS; Gallium 0.4 on NV86 Graphics; 155.3 GB on disk.

---

### Post by amanchesterman on 2014-09-01
I'm not sure that this is much help to you, but on my installation LibreOffice works fine: I can add data sources in the way you describe. I use Xubuntu rather than the Unity desktop, but like you I have the 14.04 version of Linux, and I have LibreOffice 4.3.1.2.

When I installed Xubuntu -- a fresh install -- I installed LibreOffice from the Software Center, but I checked all the options so I do have Base included. That's because I use it, but it might be worth your while to add it in to see if that makes a difference. Also, I added the Libre Office ppa as a software source, so the whole Libre Office suite gets updated regularly.

However you imply that you started having problems even when you had the 12.04 version, and your new installation hasn't corrected them? That makes me wonder if the problem is actually with your Libre Office User Profile. This is a set of files which store your personal settings. If they get corrupted Libre Office doesn't work right! They are in a hidden folder in your Home directory, and depending on how you installed 14.04, those settings may have been preserved and thus carried over to affect your new version. (When you install Ubuntu, there's an option to 'keep existing files and folders' or something like that, and if you select that option you don't get a 'clean' new version.)

If that's the case then you could try resetting your Libre Office Profile. (You'll find instructions online or you can ask for them here.) I have known that to cure persistent malfunctions of Libre Office in a number of cases.

---

### Post by Richard_York on 2014-09-01
Thanks greatly for this encouraging and helpful reply! And I believe it's led to the answer, which is great.

You've also led me to learn a useful lesson! 
I'd looked earlier in the Software  Centre, searching for "Libre Office Base" and got nothing. I read your  message and tried again, typing "Base", which led me to "LibreOffice Base" ... no  space... which I've now installed. I haven't had time to check right  through, but my spreadsheet now offers ""File - Wizards - Address Data  Source" which on a quick check appears to do the right things. So simple - no space!

It was a clean install, completely reformatting the disk, using a USB stick download rather than the upgrade, as I hoped this would kill any resident problems.

The LO version which has arrived with 14.04, installed just last Thursday, is not 4.3.1.2, however, it's 4.2.4.2 Build ID: 420m0(Build:2), which is presumably older than the one you're on - puzzling....

I confess that first I did look at [https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)    which was mostly way over my head, though I did try renaming the "User" folder which was indeed then re-made automatically, though this had no effect. But at least I now know it's there!

So again, many thanks!

---

### Post by amanchesterman on 2014-09-02
I'm glad that things seem to be working now. ;)

I believe it's not uncommon for the versions of software that come from the Software Center to be not entirely up-to-date. After I installed Libre Office from it, I also added the Libre Office PPA to my system, and since then (last April) my Libre Office suite has updated itself three times I think -- so that's the best way to ensure that you have the latest version for your distro.

---

### Post by Richard_York on 2014-09-05
Thanks again, amanchesterman.
***Edited: I first wrote this: [ If you're so minded, please, I'd really appreciate a quick idiot's guide to how I add the Libre Office PPA to my system: I'm still a real out-of-my-depth swimmer when doing things to the system! ]

 ***Edit continues:  Then I did some more research and found
[http://news.softpedia.com/news/How-to-Install-LibreOffice-4-2-on-Ubuntu-12-04-and-Ubuntu-13-10-423091.shtml](http://news.softpedia.com/news/How-to-Install-LibreOffice-4-2-on-Ubuntu-12-04-and-Ubuntu-13-10-423091.shtml)
this link. It does warn that this is only for experienced users, and that it may not be so stable. I'm not good at tweaking systems, as I said, and have been advised that maybe a broken element on Libre Office was part of my problem with LO on Ubuntu 12.04 having problems.
So I'll welcome advice, please.

 Meanwhile, LO is mostly working, and does document merges, which is the main thing I needed. 
At present it's still failing at the last stage of trying to do email mail merge, however, so I need to do something here...

---

