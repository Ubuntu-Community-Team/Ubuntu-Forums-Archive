---
title: "Win4Lin 2.0 is out w/ kqemu support"
date: 2005-09-03
forum: General Help
---

### Post by twowheeler on 2005-09-03
I bought win4lin a couple of years ago (under a different distro), and used it for windows progs I couldn't live without and couldn't run under wine.  It was fast and reliable.  There were of course several problems with it.  One was having to patch the kernel.  Another was lack of support for win2K and up.  The third one was that it insists on installing the CD image in one place, then a full image copy in each users home directory, eating up enormous amounts of disk space.  They released win4lin pro recently with win2k support, but by all accounts it was as slow as molasses in Anchorage.

This week they released an upgrade to win4lin pro 2.0.  It has kqemu module support, the same as the qemu package.  It does not require a kernel patch and is reportedly much faster.  There is a $89US price tag but there is a 2-week free evaluation period.  So I downloaded it and tried it out.

I just wanted to start a thread here on experiences with this product.  I will post mine for at least the next 13 days.   :smile: 

Day 1:

The installer can be downloaded as a .deb, so I grab that.  They warn you that mouse synchronization during installation is weird, and it is.  The mouse jumps around if you move it so the easiest thing is to just use the keyboard.  The install of Win 2k Pro takes the better part of an hour on my comp.  Otherwise it is uneventful and finishes well.  The network is set up correctly for IE access to the outside world.  The best part is that they put an icon on the desktop which opens up my home directory so I have access to my files.  It is still slower than native windows but not too bad.

Next I try to use windows update to get the security fixes etc.  You _don't_ want to do this.  Waited a long time for SP3 to install, then found that it refuses to restart.  Something about a bad .dll file.  I wipe the winpro directory and start over.   :-x 

Eventually I am back with a functional win4lin desktop, and go to bed.

Day 3:

I begin to install stuff.  Some things work well, while others do not.  I notice that sound works, but is a little scratchy.  Not bad.  Also it boots into an administrator account that has no password.  Not great for security, but it is easily remedied.

I try to install a kids game, Kid Pix 3.  It runs to the end, but then dies with "Severe:  Can't create shortcuts".

Some of the docs at the win4lin site are .pdf files, so I install Adobe Reader.  Annoying, because AR has become 16MB of bloatware.  Then the installer bombs with this:

```
This version of Windows 2000 is not supported.  
You should upgrade to Service Pack 2 and run setup again.  
Setup will now terminate.
```
 ](*,) 

My experience with SP3 was not good so I decide to read the docs for advice.  So I grab a copy of Multivalent from sourceforge, a java pdf reader.  And of course a java executable from Sun.  Eventually I can read the docs. Of course, I could do this from my linux desktop, but this is part of the test.  

The release notes are essential reading.  They explain exactly how to install service packs in windows without pain.  They recommend downloading the SP2 network install and running it offline, so I do that.  Note to self: read the docs before you complain.

I install my ancient copy of MS Office 97.  It runs ok but coughs up many errors like:
```
Setup could not create the folder "\\HOST\Documents and Settings\Administrator\Templates\EXCEL8.XLS".
```
However it reports a successful install and it works.

More software: 
Quicktime and iTunes -- perfect.
H&R Block TaxCut -- perfect.
Broderbund Print Master -- perfect.

So the main trouble now is that some installers can't create shortcuts and folders, while others can.  I have no idea why.
 
Still, not a bad run.  Will try again later.

---

### Post by twowheeler on 2005-09-05
Day 4:

Ok, now I am annoyed.  Lots of things will crash win4lin.  For example I decided to try the adobe reader again after the SP2 update.  It installed just fine.  However whenever I try to run it, the program crashes.  I mean, the win4lin window just disappears without an error message.  Bang, I am back to gnome.

Same with quicktime.  Now, I did not expect much from any media program due to speed, but it just crashes the whole thing.  

With all of these crashes, of course, windows insists on running scandisk on restart.  

On the up side, the printer installed and works without a hitch.  Just follow the directions in the release notes.

---

### Post by twowheeler on 2005-09-10
Day 9:

Sorry, been busy.  Spent some time with win4lin today however, and am getting used to its quirks.  I have been using iTunes, and snagged an album.  It works well, and the play back quality is decent.  It will not burn a CD however.  I will have to learn about libfaad2.   :smile: 

I don't have any crashing anymore, and I am thinking that it was just a problem with adoe reader 6.0.  After I upgraded to AR 7.0, the problem went away.

All of the basic non-media programs work very well, and print without a problem.  So the lesson seems to be, don't buy win4lin for any media-type programs.  Also the docs warn that directx games don't work.  I don't care about that, although I have tried a few kids games I had sitting around.  Some work and some don't, and it seems the only approach is to try them and see.

So, I guess win4linpro has a niche, although it will not do enough for some people.  If you need non-media windows functionality that can't be had in wine, then this is a good product.  Some media programs do work (iTunes) but not others, and it is hard to predict which is which.  You can easily get to your linux personal files, and use a printer.  The "windows"-window is easier to use than in previous versions, because you don't have to press "Ctrl-Alt" to un-grab the mouse.  For my purposes, which is mostly to run a tax program, it works well.

---

