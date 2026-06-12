---
title: "Is your OpenOffice crashing? Look here!"
date: 2007-10-20
forum: General Help
---

### Post by kolinab on 2007-10-20
Hi,

My OpenOffice.org v. 2.3 was crashing (usually when opening dialog boxes) on a clean install of Gutsy. I did some searching and discovered that my problem was somehow related to the package Openoffice.org-gtk. Uninstalling this package has solved the problem for me. However, OpenOffice no longer obeys the gtk theme specified elsewhere.  

I'm just trying to sew a few of these threads together so we can help some folks out. I've listed some of the related threads and bug reports below.

OpenOffice.org Crash in Gutsy 7.10 related threads:

[http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088) (this thread)
[http://ubuntuforums.org/showthread.php?t=450008](http://ubuntuforums.org/showthread.php?t=450008)
[http://ubuntuforums.org/showthread.php?t=582152](http://ubuntuforums.org/showthread.php?t=582152)
[http://ubuntuforums.org/showthread.php?t=583813](http://ubuntuforums.org/showthread.php?t=583813)
[http://ubuntuforums.org/showthread.php?t=563781](http://ubuntuforums.org/showthread.php?t=563781) in closed Gutsy Forum

Related(?) Bug Reports:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) This looks to be the primary report. Others listed are likely duplicates.
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/141049](https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/141049)

Good luck!

Kolin

---

### Post by grantk86 on 2007-10-20
You should not have to uninstall one Gutsy core package in order to get another to work properly.
I've had Gutsy on my laptop for a few weeks now, and it is obvious that this release has been rushed and pushed out as final without being fully tested.  While there are some nice new features, they seem to come at the price of old features no longer functioning properly.  I've had to tell my fiance and my sister not to install the update from Feisty, as something will most likely cease to work in the process, and I cannot be there to fix it for them.
This release is showing a lot of similarities to all of the problems plaguing Vista, and if Ubuntu doesn't get things together fast, they're going to be losing a lot potential Windows switchers that were waiting for Gutsy to be released to try out Linux.

---

### Post by kolinab on 2007-10-20
> **grantk86 said:**
> You should not have to uninstall one Gutsy core package in order to get another to work properly.

No, you shouldn't. 

But did removing the Openoffice.org-gtk package work for you? And what gtk theme are you using?

If we can figure out what works and what doesn't, hopefully we can determine exactly what the problems are and keep things improving.

K

---

### Post by grantk86 on 2007-10-20
No, I have not uninstalled the openoffice.org-gtk package, as my OO stopped crashing after the ubuntu5 package release on October 16-ish.
The main problem that I am currently having with OpenOffice is that the Select Data Range buttons in the Chart Wizard (Calc) do not work at all.  They used to make the entire program crash, but since the last update, they just simply don't work.  When clicked on, things look promising, but when I try to select a range of cells, I just get a system beep and have to return to the main Chart Wizard form.  I currently have to manually type in the sheet/cell references for all of my data series in order to produce a chart.  This is a giant inconvenience, especially since everything in OpenOffice 2.3 had worked perfectly when I had it installed on Feisty.
I also did a clean install of Gutsy, just to make sure that no previous installations of unsupported software messed anything up during the upgrade.
And I'm using the default Human theme.

---

### Post by kolinab on 2007-10-20
Strange. The Select Data Range Buttons work for me. 

I wonder what would happen if you uninstalled the OOo-gtk package. That's the only really significant thing I have changed from the default installation of OpenOffice.

[EDIT]

I have tried to reproduce your problem with the oo.o-gtk package installed, but my OO crashes before I can get to the chart dialog.

---

### Post by grantk86 on 2007-10-20
> **kolinab said:**
> Strange. The Select Data Range Buttons work for me. 

I wonder what would happen if you uninstalled the OOo-gtk package. That's the only really significant thing I have changed from the default installation of OpenOffice.

Uninstalled package, Chart Wizard still not working, and Calc crashed on me.  I'm just going to try reinstalling openoffice again... for the third time.

---

### Post by kolinab on 2007-10-20
I was looking around Launchpad and found your bug report. There's certainly a few crash bug reports there that could be related.

Have you tried runninc calc from the terminal to see if you get any errors or other feedback?

---

### Post by FuturePilot on 2007-10-20
This seems to be directly related to the GTK theme you are using at that time. Try to reproduce it with the Human Theme. Nothing is reproducible. 
But I was able to reproduce it using the Crux theme and pressing F11 in OO

---

### Post by grantk86 on 2007-10-20
I just did a full re-download and re-install of OOo 2.3, and I'm still having the same problem with the Chart Wizard.  The program does not crash when I try to select a data range, it just won't let me select anything and sounds the system beep each time that I click outside of the small Select Data Range window.  If anyone knows how I can get a system log of what the program's error is at this point, please let me know.

---

### Post by grantk86 on 2007-10-20
Running OOo Calc from terminal does not fix the problem either (and no errors produced).  And as stated earlier, I AM using the default Human theme.

---

### Post by kolinab on 2007-10-20
I've added a couple more bug reports to my original post. 

Now I'm looking through forums over at openoffice.org

The prevailing opinion over there so far seems to be suggesting that people install the official version of OpenOffice, not the packaged Ubuntu version. I honestly have no idea what the pros and cons of this are.

[http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

### Post by grantk86 on 2007-10-20
Con (in my experience anyways) is that it will screw up future distribution upgrades unless it is uninstalled, and the Ubuntu version is reinstalled before upgrading.

---

### Post by kolinab on 2007-10-20
> **grantk86 said:**
> Con (in my experience anyways) is that it will screw up future distribution upgrades unless it is uninstalled, and the Ubuntu version is reinstalled before upgrading.

Yeah, that's what that link I just read kind of suggests. Honestly, I do not feel like going through that hassle, just to have OO work with my gtk theme. I guess I'll leave mine be for now. Especially since I haven't gotten any *real* work done tonight yet anyway! :)

---

### Post by kolinab on 2007-10-21
> **grantk86 said:**
>  If anyone knows how I can get a system log of what the program's error is at this point, please let me know.

I have not played with any of these tools . . . 

[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

### Post by grantk86 on 2007-10-21
Thanks for all of your help with this!

---

### Post by grantk86 on 2007-10-21
I just tried installing the Official version of OOo 2.3 from their website, and I still get the same problem.  Must be something screwed up elsewhere on my system.  I don't feel like messing around with this anymore.

---

### Post by kolinab on 2007-10-21
I know how you feel. Hopefully these threads will attract some attention - I'm sure in the coming days and weeks more folks will encounter these problems and a solution will arrive . . . 

Cheers, K.

---

### Post by zhangsong023 on 2007-10-21
I have the same problem in function wizard with the default Human theme.
I pressed the select cell range button and selected some cells, but when I pressed that button again or pressed return key, the whole program crashed.

---

### Post by FredB on 2007-10-21
Sorry to bother you, but : not a crash with my Gutsy cleanly install since beta time...

And I'm running AMD64 version. Maybe it is the answer ?!

---

### Post by kurbey on 2007-10-21
The problems  disappeared after uninstalling the gtk and gnome packages of OpenOffice. It's only a workaround for the time being, at least I don't have to use Office at work then.

---

### Post by texadactyl on 2007-10-21
Two easy solutions that work (one or the other):

1. Stay on Gnome but uninstall openoffice-gtk (Gnome binding for ooo).
2. Switch to KDE.

Also works but time-consuming and risky if you do not back up your data first: Fall-back to 7.0.4.

When the openoffice-gtk package is fixed, then you can go back to the way openoffice was intended with Gnome look and feel.

-Richard

---

### Post by FuturePilot on 2007-10-21
I think this is the bug report that is most relevant to the issue. All of the others are not related or are duplicates of this one.
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526")

---

### Post by RFScheer on 2007-10-21
I was having the same problems, as well as unreadable font, after clean install of Gutsy.  Well, it wasn't exactly a clean install.  I preserved my former /home/"user" partition to save all my former settings, directories, etc.  The font problem was solved by selecting Bitstream Vera Sans from the System>Preferences>Appearance menu.  I had been trying out OpenSymbol.  The menu crashing problem was solved by switching from Pharago theme to Human.

Obviously I don't like fooling around with this level of tweaking just to get something working that worked great under Feisty, but I hope it helps.

- Robert

---

### Post by KStorm on 2007-10-21
No crashes here, but the Oo.o interface font rendering doesn't jibe with the rest of the system fonts.

---

### Post by rgsproductions on 2007-10-22
I don't know if this helps anyone, but I reinstalled the gtk package and tried the different themes and controls.  I was able to crash the  OO database and presentation on crux and clearlooks, but all open office programs ran under human and glossy.  The above was with compiz on and off.  Compiz did not seem to matter.

Don't know if this matters, I am running a Nvidia gforce 4 mx420 card.  Since it seems that the issue might be in the themes  and or graphics?

Just throwing my $.02 in.:confused:

---

### Post by GatorV on 2007-10-22
Was crashing very badly but after removing the gtk package it works again (althought it looks Excel-like :lolflag:) but It works without problems, lets hope a fixed version of those packages can be made. :)

---

### Post by Down8ve on 2007-10-22
> **GatorV said:**
> Was crashing very badly but after removing the gtk package it works again (althought it looks Excel-like :lolflag:) but It works without problems, lets hope a fixed version of those packages can be made. :)

Ditto here.  I filed a bug (#131526) along with others.  Wonder how many folks lost patience with it and moved on.

I followed the advice of one soul over on the bug report: am now using Abiword instead.  Hopefully I can churn out papers that don't need advaced features until the GTK fix is in (it really is hard on the eys with the default OO theme).

---

### Post by Rotarychainsaw on 2007-10-23
Just checking in to say I'm having this problem as well. Getting rid of the GTK and gnome packages made it work, but it looks like crap and I'm having some other problems as well. Maybe a reboot will help.

---

### Post by andymushu on 2007-10-23
Whenever I try to print in writer openoffice crashes. This was reconciled by switching to the human theme. I was using the linsta3 theme with neu icon set, in case anyone wanted to know.

---

### Post by aphelionos on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi.

I am experiencing the same issue as the rest of you here. Open office has been crashing on start... doenst even open, as long as i have the -gtk and -gnome package installed. I'm luckily experienced enoug to be able to troubleshoot my problem, but it really should be fixed for others that aren't. This thread helped me solve my problem, by switching away from my custom theme to human theme. But its only temporary, cause even if the human theme is nice, some of the charm of ubuntu is the ful customability. Anyway, I'll post my terminal output when OO crashed, hoping it can help someone looking in to the issue.

cyrano@bergerac:~$ openoffice -writer
X-Error: BadDrawable (invalid Pixmap or Window parameter)
        Major opcode: 53 (X_CreatePixmap)
        Resource ID:  0x4e0024a
        Serial No:    2365 (2365)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging

** (process:8705): WARNING **: Unknown error forking main binary / abnormal early exit ...

---

### Post by iamthemicrowave on 2007-10-23
I removed openoffice.org-gtk and openoffice.org-gnome and it stopped crashing for me.

---

### Post by eyemeansit on 2007-10-24
Uninstalling everything "openoffice.org" related, then reinstalling without openoffice.org-gtk or openoffice.org-gnome seems to have done the trick for me. (So far...!)

Thanks! I needed that.

---

### Post by beow on 2007-10-24
I removed openoffice.org-gtk, which automatically removed openoffice.org-gnome and ubuntu-desktop. Now it works stable, albeit it looks ugly... :neutral:

---

### Post by kolinab on 2007-10-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Just a note to those following this. Apparently a fix for the gtk related crash has been released into OO.org. There is work being done to somehow propagate (??!) the fix to the Ubuntu packages. I have absolutely no understanding of how any of this works behind the scenes or what is really going on, but if you want to follow along with the process you can read the launchpad page relating to this bug. I might be kind of learning how this process works, but I'm pretty sure there's a computer somewhere quietly churning away on fixing this right now.

Cheers,

K

---

### Post by i8bugs on 2007-10-26
OK this is incredible.  I did a complete uninstall and reinstall.  Clicking the Icon gives me no response...nothing.  I did this three times.  I am not using an old icon..I watch them disappear and reappear in the new install.  NOTHING.  Not even a splash screen...not even a change in mouse cursor.  OOffice is dead on my Computer using 7.10.  
bugs

---

### Post by nanayaw on 2007-10-27
OO was crashing when I issued a print command - using synaptic to unistall openoffice-gnome and openoffice-gtk worked fine to resolve this problem

---

### Post by Orgin on 2007-10-29
I had the same problem as described in this thread with crashing openoffice on the three machines I've installed 7.10 (x386) on. I've removed the openoffice-gtk and openoffice-gnome packages to get it working again.

---

### Post by atatistcheff on 2007-10-29
I'm in the process of reinstalling Writer after trying all the gnome-gtk and other uninstall tricks listed here.  My Openoffice installation continues to be completely unstable.  My symptoms are the application  hanging, usually when there's another dialog in front.  This has happened 100% of the time when I try to use the help system and 50% of the time when I try to use the "Find" dialog.  I'm just in the process of completely removing and reinstalling OpenOffice - just writer this time to see if that works...

Well, no luck here.  Just tried opening Help and it's locked up again.  Removing gnome-gtk actually made it worse because before it would detect that the program hung and provide the "force quit" dialog.  Now I have to go and kill the processes manually.  I'm using Dapper too so it's not like I'm trying to be bleeding edge.

I'm going to have to break down and edit the doc in Windoze...

---

### Post by Crafty Kisses on 2007-10-29
> **kolinab said:**
> Hi,

My OpenOffice.org v. 2.3 was crashing (usually when opening dialog boxes) on a clean install of Gutsy. I did some searching and discovered that my problem was somehow related to the package Openoffice.org-gtk. Uninstalling this package has solved the problem for me. However, OpenOffice no longer obeys the gtk theme specified elsewhere.  

I'm just trying to sew a few of these threads together so we can help some folks out. I've listed some of the related threads and bug reports below.

OpenOffice.org Crash in Gutsy 7.10 related threads:

[http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088) (this thread)
[http://ubuntuforums.org/showthread.php?t=450008](http://ubuntuforums.org/showthread.php?t=450008)
[http://ubuntuforums.org/showthread.php?t=582152](http://ubuntuforums.org/showthread.php?t=582152)
[http://ubuntuforums.org/showthread.php?t=583813](http://ubuntuforums.org/showthread.php?t=583813)
[http://ubuntuforums.org/showthread.php?t=563781](http://ubuntuforums.org/showthread.php?t=563781) in closed Gutsy Forum

Related(?) Bug Reports:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) This looks to be the primary report. Others listed are likely duplicates.
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/155154](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/155154)
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/141049](https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/141049)

Good luck!

Kolin
Haven't had that many issues.

---

### Post by KingNothing13 on 2007-10-30
I was running it on two different computers,  one a 64-bit desktop, and the other a 32-bit laptop.  While running the Crux theme on both, OO would crash when trying to do a Data->Sort from the menu, before the Sort window came up.

Switched both machines over to the Human theme, and both work fine now.

---

### Post by Michael Longval on 2007-10-31
> **rgsproductions said:**
> I don't know if this helps anyone, but I reinstalled the gtk package and tried the different themes and controls.  I was able to crash the  OO database and presentation on crux and clearlooks, but all open office programs ran under human and glossy.  The above was with compiz on and off.  Compiz did not seem to matter.

Don't know if this matters, I am running a Nvidia gforce 4 mx420 card.  Since it seems that the issue might be in the themes  and or graphics?

Just throwing my $.02 in.:confused:

This also (so far) works for me.  I'm running 7.10 with Compiz on a T41 ati radeon 9000.  Was crashing really badly with the Crux theme.

---

### Post by shane2peru on 2007-10-31
This problem is still not solved!  I have three machines running Ubuntu 7.10 and one of them switched to the Crux theme and had problems with OOO crashing.  So would this be an OOO problem, or a Crux and Clearlooks theme problem?  Either way, this is not a good thing, and certainly needs fixed.  Everything is running up to date.  No Fixes as of yet.

Shane

---

### Post by FuturePilot on 2007-10-31
> **shane2peru said:**
> This problem is still not solved!  I have three machines running Ubuntu 7.10 and one of them switched to the Crux theme and had problems with OOO crashing.  So would this be an OOO problem, or a Crux and Clearlooks theme problem?  Either way, this is not a good thing, and certainly needs fixed.  Everything is running up to date.  No Fixes as of yet.

Shane

They're still working on it
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526")
It's an OO problem. It was actually a problem with the upstream OO. Sun has fixed it in 2.3.1 and the Ubuntu devs are trying to apply the patch for the Ubuntu version 2.3. Hopefully it will be fixed very soon

---

### Post by shane2peru on 2007-10-31
> **FuturePilot said:**
> They're still working on it
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526")
It's an OO problem. It was actually a problem with the upstream OO. Sun has fixed it in 2.3.1 and the Ubuntu devs are trying to apply the patch for the Ubuntu version 2.3. Hopefully it will be fixed very soon

ahhh, good.  I read in this thread that it had been fixed, or thought I did.  Glad to hear it is still being worked on.  Thanks.

Shane

---

### Post by tanmays on 2007-11-01
I have changed the GTK theme to Human and everything seems to work perfect. The problem arises when i change the GTK theme something other than Human.

Hope this problem will be fixed soon.

---

### Post by perixx on 2007-11-01
Hmm... 

there have been so many issues with bad Ubuntu-OO packages reported in the OO forums - and most of them (including mine) could be solved by completely removing OO and installing the original OpenOffice .deb-package! 

I must admint that I use Feisty, though. But still might be worth a try...


I completely removed the old OO version with Synaptic, closed it again and then:

1) downloaded the localized archive, linked on suggested site
[http://download.openoffice.org/index.html](http://download.openoffice.org/index.html)

2) used Xarchive to unpack it to the new directory /home/USER/tmp

3) opened a Terminal in that directory and typed
sudo dpkg -i *.deb

Done.


perixx

---

### Post by grantk86 on 2007-11-02
No, installing the official OpenOffice package from their website does not fix the problems.  That is why this is so frustrating, because the program worked perfectly in Feisty, but somehow the Ubuntu version in Gutsy got broken.

---

### Post by Depressed Man on 2007-11-02
In one of my beta tests of Gutsy it kept crashing my system. Now it works perfectly (same laptop, just reinstalled the OS completly).

---

### Post by jhenager on 2007-11-03
It would crash and make me do a Force Quit if I tried to print or insert a picture. I uninstalled from Synaptic and used Add/Remove to re-install it.
Worked great.
I do think there are a few issues with this new release, but there is no such thing as a painless hardware or software upgrade, IMHO.

---

### Post by bg1256 on 2007-11-03
It seems to me that I have at least a usable Open Office for now.  I've not tested it rigorously, but it seems I at least have my word processor back.

I removed:

openoffice.org-gtk


And it seems to be working okay now.

Thanks for the useful thread.

---

### Post by Mike'sHardLinux on 2007-11-03
> **bg1256 said:**
> It seems to me that I have at least a usable Open Office for now.  I've not tested it rigorously, but it seems I at least have my word processor back.

I removed:

openoffice.org-gtk


And it seems to be working okay now.

Thanks for the useful thread.

Wow! I just removed that package, and not only is OOo stable, but it is much faster now!!!

---

### Post by FuturePilot on 2007-11-03
> **grantk86 said:**
> No, installing the official OpenOffice package from their website does not fix the problems.  That is why this is so frustrating, because the program worked perfectly in Feisty, but somehow the Ubuntu version in Gutsy got broken.

Yes. Installing the official OO will not fix it. This is a problem with the upstream OO, not just Ubuntu.

---

### Post by bluehue on 2007-11-03
Fixed it by reverting back to the default "Human" theme whenever I use OO.

---

### Post by Sepp1 on 2007-11-05
This has been said before, but switching back to "human" also solved my problems. 

Why does that make me sound like a werewolf? 

it crashed when tried to open the "paragraph tab", when i used "Crux" - rather anoying

---

### Post by stchman on 2007-11-05
I have a script to uninstall OO in Ubuntu and install OO 2.3 from OO's website.

[http://www.stchman.com/tools/openoffice/OO_2_3_install.sh](http://www.stchman.com/tools/openoffice/OO_2_3_install.sh)

My script install the Sun Java 5 stuff, so go into the script and comment out the line that installs Java and run the script.

Here is my page of other tools and such
[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

---

### Post by pssturges on 2007-11-05
> **Mike'sHardLinux said:**
> Wow! I just removed that package, and not only is OOo stable, but it is much faster now!!!

Same here.:) I will try re-installing when some fixes come through.

Phil

---

### Post by shane2peru on 2007-11-05
> **stchman said:**
> I have a script to uninstall OO in Ubuntu and install OO 2.3 from OO's website.

[http://www.stchman.com/tools/openoffice/OO_2_3_install.sh](http://www.stchman.com/tools/openoffice/OO_2_3_install.sh)

My script install the Sun Java 5 stuff, so go into the script and comment out the line that installs Java and run the script.

Here is my page of other tools and such
[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Nice web page with some very nicely written scripts!!!  Thanks!  I love the comments through them as it makes it easy to understand what is taking place where!

Shane

---

### Post by lod_john_marbury on 2007-11-06
> **kolinab said:**
> ... my problem was somehow related to the package Openoffice.org-gtk. Uninstalling this package has solved the problem for me...


It was just the opposite for me. OO crashed when I opened a .odt with forms, so I tried to uninstall openoffice,org-gtk *but* it was not installed!. Just for fun, I've installed it and, guess what? It works. Impressive :) 

BTW, my theme is "Glossy" and I'm using Ubuntu Studio 7.10 x86_64

---

### Post by skyjacker on 2007-11-06
I used OO since it was first relaesed. (in MS.) Since the new version came out, Some of my important file became "read only", and I cannot modify them. Dumped OO for now am am usimg koffice package. No problems with this so far.:)

---

### Post by hollowhead on 2007-11-06
Yep my version 2.3 gutsy install crashes in the chart wizard, I was hoping this would be solved by downloading the official oo version.  Not using human theme.

---

### Post by Hairy_Palms on 2007-11-07
even forcing openoffice them doesnt work,oo-gtk doesnt crash when i use clearlooks as my desktop theme, but does when i use my own theme and force oo to use clearlooks
it still crashes when i run it as
GTK2_RC_FILES=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc oowriter

---

### Post by vio-tfsi on 2007-11-08
> **grantk86 said:**
> No, I have not uninstalled the openoffice.org-gtk package, as my OO stopped crashing after the ubuntu5 package release on October 16-ish.
The main problem that I am currently having with OpenOffice is that the Select Data Range buttons in the Chart Wizard (Calc) do not work at all.  They used to make the entire program crash, but since the last update, they just simply don't work.  When clicked on, things look promising, but when I try to select a range of cells, I just get a system beep and have to return to the main Chart Wizard form.  I currently have to manually type in the sheet/cell references for all of my data series in order to produce a chart.  This is a giant inconvenience, especially since everything in OpenOffice 2.3 had worked perfectly when I had it installed on Feisty.
I also did a clean install of Gutsy, just to make sure that no previous installations of unsupported software messed anything up during the upgrade.
And I'm using the default Human theme.

I had the same exact problem. I just set the Visual Effects from "extra" to "none" and ... problem solved... Try it if you still have the problem :)

---

### Post by carlosjuero on 2007-11-08
I was having issues opening a CSV file with OO today, kept locking and having to be forced to shut down - uninstalling openoffice.org-gtk fixed that problem. It seems the entire problem is with the GNOME integration :/

Edit: Thanks to those who figured this workaround, I was about to give up on opening that file :)

---

### Post by Michal_D on 2007-11-08
> **vio-tfsi said:**
> I had the same exact problem. I just set the Visual Effects from "extra" to "none" and ... problem solved... Try it if you still have the problem :)

I too have the exact same problem, and yes, switching the Visual Effects to None does work. [Running plain 7.10 install, human theme, the only graphical gizmos are from the 'Advanced Desktop Effects Settings', which was preinstalled - I did not meddle with any compiz fusions, emeralds etc myself]

There are two buts though:

1. The 'None' setting is the only one that makes the problem disappear - the three that remain - Normal, Extra & Custom all have the problem.

2. I installed 7.10 only a week ago, it's my first encounter with Linux, and I just love the degree of customization it allows [although being a newbie I don't think I've seen 10% of it yet] and I plainly don't like the idea of resigning from desktop cube, ring switcher and all that nice stuff...

So I have a question to more advanced users - as I don't like complaining, I'd like to do something to help solving the problem. What should I do? Is there a way I can get a problem report of somesort to send it to someone [developers]? Is it even worth bothering?

---

### Post by grantk86 on 2007-11-08
> **vio-tfsi said:**
> I had the same exact problem. I just set the Visual Effects from "extra" to "none" and ... problem solved... Try it if you still have the problem :)

Thanks, this seems to fix the problem, albeit raising another one in that I can't have any visual effects to run this properly.

---

### Post by morticiaskeeper on 2007-11-08
I've only just returned to some presentation work that I started in XP, but need to get finished for the weekend, and now the problems start.

OO loaded the file, played the presentation, but as soon as I tried to change the view, or edit a slide, it crashed, offering to recover the file on the next startup.

Sent the file to a mate who tried it on OO on both XP and redhat, modified the file, and sent it back. It still wouldn't run.  

I re-installed the whole OO suite, then it wouldn't even load a file, just going through a doom loop of recovering the file, crashing, recovering the file etc...etc...

Loaded the file in OO on XP (sorry) and everything worked ok, although the music disapeared, but that MAY not be linked.   Saved the file, exported to powerpoint as well, then rebooted to Ubuntu.

The same problems appeared again, until, after reading this thread, I switched from the Crux theme to Clearlooks, then everything ran fine, except the music.  Switched back to Crux, it crashed again. Switched to Human, works again!!!

***EDIT***

Just started using it, every time I attempt to save or export the file, it crashes, offering me a recovery.  The recovered file includes all changes made.  Turned off all visual effects, but it made no difference.   Copied the file from the ftp server I was using to an internal hard disk, now everything works fine, including saving files.


At least I can get the job done without resorting to XP!.

Gutsy & Compiz Fusion installed.

---

### Post by kolinab on 2007-11-08
> **Michal_D said:**
> 

[snip]

So I have a question to more advanced users - as I don't like complaining, I'd like to do something to help solving the problem. What should I do? Is there a way I can get a problem report of somesort to send it to someone [developers]? Is it even worth bothering?

The answer is basically that the developers know about it already. You can go to the launchpad page for this bug, (launchpad is the system through which bugs are reported on, nailed down, and hopefully fixed) where you can read about the solutions being enacted . . . It takes a while for the bug fixes to get integrated. Look here for more:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526)

---

### Post by Michal_D on 2007-11-08
> **kolinab said:**
> The answer is basically that the developers know about it already. [snip]
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526)
I'm actually wondering if we're talking about the same bug here.
I had the exactly same problem as grantk86, and as you might remember, uninstalling the OOo-gtk package [which the tread you linked to seems to be about, if I get it correctly] did not help with his problem.

---

### Post by kolinab on 2007-11-08
> **Michal_D said:**
> I'm actually wondering if we're talking about the same bug here.
I had the exactly same problem as grantk86, and as you might remember, uninstalling the OOo-gtk package [which the tread you linked to seems to be about, if I get it correctly] did not help with his problem.

Oh I see, sorry again. Yeah, if your crashing is fixed by turning visual effects off then it certainly sounds like it could be a different bug. Likely even. Have you tried searching around launchpad (or here) for visual effects related/affected OO crashes? I'll bet you'll find you're not alone.

Cheers,

K

---

### Post by NeverM$4Me on 2007-11-09
My OO 2.3 crashed on Gutsy whenever trying to open any .ppt files then change its mode to "Normal" from the tabs with a customized theme and i was able to fixed that by switching back to the default Human theme.:confused:

---

### Post by bg1256 on 2007-11-10
A few pages back, I posted that removing the gtk pacakge cured my open office.

I've now discovered that is only partially true.

I have a working Writer, but the spreadsheet is missing window borders. It opens as a maximized window, and I can close it with alt+F4, but nothing beyond that.

---

### Post by gotee12 on 2007-11-10
My OO.o install was broke (only Writer worked properly), but I fixed it by installing the openoffice-gtk package. I don't know why the gtk package wasn't installed on my machine, it seems to normally be installed. Anyway, I'm using Compiz and Emerald theme manager. And just to take it a step further, I'm using the 51077-VistaBlack theme found on compiz-themes.org that uses the Oxygen frame engine. Good luck to everyone that's still experiencing problems.

---

### Post by crossz on 2007-11-19
it's some issue about the theme. When I use MILK theme (downloaded from art.gnome.org), only writer works, When changed to some theme else, no problem.

---

### Post by Pathfinder_ on 2007-11-19
I'm using azur gtk theme and OOo writer and it crashes every time I try to format the page or  paragraph. OOo impress doesn't even start. anybody know how long it will be until it's fixed?

---

### Post by DemonStar55 on 2007-11-20
OO.o crashes when I try to open it with no errors

I do get "WARNING **: Unknown error forking main binary / abnormal early exit ..." some times, but not a lot

I was getting that before then I purged-removed it and reinstalled and now just no work

---

### Post by steve_k on 2007-11-21
My OpenOffice was freezing on a regular basis, especially when I tried changing the options section. By simply changing my desktop theme from Crux to Glider seems to have solved the problem (at least I hope it has).:)

---

### Post by defaultlogin on 2007-11-21
Hi,

I suddenly started having problems with Oo, at first with Impress, that basically just didn't work anymore after just a few weeks. For no apparent reason I was unable to open presentations anymore. Also, Writer seemes sluggish too.

Found this article that solved my problem - now Oo is way faster than anything else, just as it should :)

[http://www.howforge.com/optimizing-openoffice-org-for-speed](http://www.howforge.com/optimizing-openoffice-org-for-speed)

Made a huge difference!



/defaultlogin

---

### Post by mmichalowicz on 2007-11-22
Same problem. 
Solution for me was:
apt-get remove openoffice.org-gnome openoffice.org-gtk. 
And then reinstall : 
apt-get install openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-dtd-officedocument1.0 openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-l10n-pl openoffice.org-math openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-human openoffice.org-thesaurus-en-us openoffice.org-thesaurus-pl openoffice.org-writer

Hope it will help :)

---

### Post by jkzubu on 2007-11-22
Any progress on solving this problem?  Clean install Gutsy + updates.  AMD64 version.  Open Office still crashing - apparently caused by Genome Themes.

Anyway after further research, I reset my theme to the basic Human theme and I was unable to replicate the Open Office Crashes.  The 'crashing' theme that I was using was a modified version of the base Human; where all I did was change the color options. I did not add any other themes - just made changes to the existing Human theme.  After I reverted back to the original Human theme, Open Office seemed to work fine - so far.  Also, I did not add, change or remove any packages or dependencies.

The way that Open office reacts with the themes issue appears to be persistent and should be fixed. Obviously, users should be able to use a theme of their choice in any of the base packages.  For the time being, I will resort to switching themes (back to Human) while using Open Office.  FYI - I am not using Compiz, Beryl, GL Desktop or any other modified desktop theme.  Just the base stuff.  Any permanent fix recommendations are welcome.

---

### Post by zba78 on 2007-11-23
Strange as it may seem I've found a solution that worked for me. Like most of you I have to remove openoffice.org-gtk & openoffice.org-gnome. But I did ```
sudo apt-get install openoffice.org-kde
```I've found that as long as I disable desktop effects OOo works perfectly fine for me. With desktop effects on only writer & calc worked correctly

---

### Post by rfurman24 on 2007-11-23
I found this in the bug report. It works for me. I finally have oo working with the gtk package and custom theme.

Hello,

i have got problems with open office too. Perhaps this solution can help:
open the gtkrc file of your theme and disable the following lines
    GtkOptionMenu::indicator_size = {...}
    GtkOptionMenu::indicator_spacing = {...}
Reset yout theme and launch openoffice again.

---

### Post by ipetter on 2007-11-24
Above solution worked for me too :) Finally I can get some work done i Ooo

---

### Post by frodon on 2007-11-24
This workaround works for me too, hope this doesn't have drawbacks (maybe someone can bring some insight on this).

Thanks for sharing your fix :)

---

### Post by rune0077 on 2007-11-24
OpenOffice.org has a stable and functioning Linux version for download. So, one could just uninstall the Ubuntu-version and install the "official" OpenOffice suite instead (which is bound to be better anyway, but of course won't support your GTK theme).

---

### Post by zba78 on 2007-11-24
That solution works for me too (using openoffice.org-gnome). Thanks for that

---

### Post by rfurman24 on 2007-11-24
I wanted it to blend in with my desktop. I had tried uninstalling the ubuntu version and installing the OO version. I even tried the nightly build from OO. Nothing worked with my themes until I saw the fix above in the bug report. So far I see no repercusions from using this fix.

---

### Post by sabre2th on 2007-11-25
I just managed to fix my problem without sacrificing functionality or doing any editing of files.  I had been experiencing all manner of crashes involving the customize window, saving, printing, etc...

All I did to fix it was completely remove everything OpenOffice related in Synaptic.  I then installed just Word Processor and Spreadsheet using Add/Remove Programs.  (I essentially just removed openoffice.org-gtk and -gnome, but doing it this way fixed a number of other issues for me.)

My theme is a combination of Crux controls and Glider borders.  I do have Compiz installed and running.  This was a Feisty box, upgraded when Gutsy came out.

---

### Post by Shne on 2007-11-25
My father had this problem on his laptop. Any new windows in OpenOffice Writer and the drawing function would make it crash.
We fixed it simply by switching from Crux Controls to Clearlooks Controls in Appeareances.

---

### Post by nikoah on 2007-11-25
Thanks, removing that worked for me. 

Nikoah

---

### Post by nikoah on 2007-11-25
Learned something I should have known already.  I read all the way down, and changed from Crux to the Clear appearance, and that too worked, so I added the package back onto my computer.
Nikoah

---

### Post by jen1963 on 2007-11-26
Had the same OOo crash problem and uninstalling the openoffice-gtk did indeed fix it.
As much as I love Ubuntu I'm concerned that quality is slipping in favor of release dates. This bug should have never made it past beta testing...

---

### Post by frodon on 2007-11-26
This is an openoffice bug not an ubuntu bug and if you use the ubuntu human theme there's no problem.
So this may affect you only if you tweak your theme settings, default settings are safe.

---

### Post by rfurman24 on 2007-11-26
I do agree that Gutsy was not as ready as Feisty however this concern is not an Ubuntu issue. As stated above this is an OO issue and although it is irritating that out of the box it will not work with some themes it really was not intended to do so. If you want to use your theme try the editing the theme as stated above.

---

### Post by -grubby on 2007-11-26
I guess I'm not the norm...but OpenOffice.Org almost never crashes

---

### Post by byte69 on 2007-11-26
I was using the CRUX theme and it crashed on all OpenOffice programs except writer.   I just switched back to the human default theme as someone else noted and it all works again.   So its seems to be related to themes and OpenOffice.

---

### Post by bg1256 on 2007-11-26
Hello everyone,

For the record, I've gotten Open Office to work using several variants of the Human theme, found out gnome-look.org.

My current theme is Human Olive, and everything seems to be working fine. So, if you want some variety other than the default human, you might try those out.

Good luck!

---

### Post by rfurman24 on 2007-11-26
Did no one see this. I keep seeing people complaining still about themes not working. Just try this.
> **rfurman24 said:**
> I found this in the bug report. It works for me. I finally have oo working with the gtk package and custom theme.

Hello,

i have got problems with open office too. Perhaps this solution can help:
open the gtkrc file of your theme and disable the following lines
    GtkOptionMenu::indicator_size = {...}
    GtkOptionMenu::indicator_spacing = {...}
Reset yout theme and launch openoffice again.

---

### Post by moxer on 2007-11-28
My OpenOffice crashes whenever i try to use the MINVERSE function in Spreadsheet.

It opens the function dialog, but as i fill in the arrays it just blocks and crashes.


I've tried changing my theme as well as removing the gtk/gnome packages and it didn't solve my problem.

Using the same OO version in windows does not have the same problem. I'm being forced to use windows if i want to work :(

---

### Post by skrribble on 2007-11-28
>  Originally Posted by rfurman24  View Post
I found this in the bug report. It works for me. I finally have oo working with the gtk package and custom theme.

Hello,

i have got problems with open office too. Perhaps this solution can help:
open the gtkrc file of your theme and disable the following lines
GtkOptionMenu::indicator_size = {...}
GtkOptionMenu::indicator_spacing = {...}
Reset yout theme and launch openoffice again.

wow.... thank you so much for this.... I havent tried this out extensively, but at first glance, all of the things that crashed OO.o before seem to work fine...

---

### Post by rfurman24 on 2007-11-28
You are welcome. I did not find the fix. Just found the post with the fix.

---

### Post by grantk86 on 2007-11-28
> **rfurman24 said:**
> Did no one see this. I keep seeing people complaining still about themes not working. Just try this.

This still does not solve the problem.  I am using the Human theme, Compiz turned off, and OpenOffice still crashes frequently on me.  Those two lines to comment out in the gtkrc file do not even exist for the Human theme.

---

### Post by rfurman24 on 2007-11-28
Ya. That fix is only for those having issues with OO-gtk and custom themes.

---

### Post by rare HERO on 2007-12-01
i changed my theme to "human"...

[B]system -> preferences -> appearance 

selected "human" them.
[/B]
works now.  wow.

i also uninstalled / reinstalled openoffice - word processor.

---

### Post by sanford55 on 2007-12-01
Hi everyone.  My open office writer crashed every time I tried to print, or even to look at the printer options while in writer -- I originally thought it was a printer problem but someone mentioned in response to my question that if I had changed my ubantu theme, I might try shifting back to the "human" theme.  I guess that is the default theme.  I did it and open office writer started printing.  I have not tried other programs in open office.  Thanks for all the help on this and other things.  Sanford

---

### Post by rfurman24 on 2007-12-01
> **sanford55 said:**
> Hi everyone.  My open office writer crashed every time I tried to print, or even to look at the printer options while in writer -- I originally thought it was a printer problem but someone mentioned in response to my question that if I had changed my ubantu theme, I might try shifting back to the "human" theme.  I guess that is the default theme.  I did it and open office writer started printing.  I have not tried other programs in open office.  Thanks for all the help on this and other things.  Sanford

If you want your themes to work all you have to due is edit the theme as stated elsewhere in this thread.

---

### Post by NIT006.5 on 2007-12-04
> **FuturePilot said:**
> This seems to be directly related to the GTK theme you are using at that time. Try to reproduce it with the Human Theme. Nothing is reproducible. 
But I was able to reproduce it using the Crux theme and pressing F11 in OO

Same applied here. It seems to be running fine with any other theme.... only crashes using Crux.

---

### Post by FuturePilot on 2007-12-04
Updates are available to fix this. :guitar:

---

### Post by kolinab on 2007-12-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **FuturePilot said:**
> Updates are available to fix this. :guitar:

Indeed, it seems this popular thread can now die a natural death. . . 

I reinstalled openoffice.org-gtk, did updates, ran OO and everything seems as normal. But I have been running OO without openoffice.org-gtk for so long now . . . I was entirely happy with the way it ran before and honestly can't even tell a difference now. huh

Cheers to those who squashed the bug!

K

---

### Post by kolinab on 2007-12-04
I just removed openoffice.org-gtk again to see the difference. I must say I prefer the look when OO doesn't stick to the GTK theme!

On left - OO with openoffice.org-gtk installed
on right - OO without openoffice.org-gtk

---

### Post by Nexusx6 on 2007-12-10
Hi all,

I too had OO crashing that was caused by custom gtk themes. A look at the bug report states that the problem will be fixed in 2.3.1

Well, 2.3.1 came out last week (I think) and I can't seem to update OO. I uninstalled the version that comes packages with Ubuntu and installed the stand alone version. I followed instructions to a T but I can't get synaptic to update to the new version. It looks like I have to uninstall OO completely and re-install 2.3.1 :(

Is there anyway around this? Should I just stick to the Ubuntu packaged one instead?

---

### Post by rfurman24 on 2007-12-10
> **Nexusx6 said:**
> Hi all,

I too had OO crashing that was caused by custom gtk themes. A look at the bug report states that the problem will be fixed in 2.3.1

Well, 2.3.1 came out last week (I think) and I can't seem to update OO. I uninstalled the version that comes packages with Ubuntu and installed the stand alone version. I followed instructions to a T but I can't get synaptic to update to the new version. It looks like I have to uninstall OO completely and re-install 2.3.1 :(

Is there anyway around this? Should I just stick to the Ubuntu packaged one instead?

The easiest way to fix the concern is to edit your gtk themes as states in this thread. It does not require to reinstall OO.

---

### Post by Tedel on 2007-12-10
Hope I can fix my crashes with these advices. Two additional questions, please.

1. How can I add extra dictionaries to OO? I used to do that manually under Windows, but I don't have the same access under Ubuntu.

2. What if I want to download and install OO 2.3.1 OFFLINE? Should I download it from OO.org or from packages.ubuntu.com?

---

### Post by Jiawen on 2007-12-16
Here are my problems:[LIST]
[*]I use Xfce. Removing openoffice.org-gtk doesn't help anything; OOo still crashes. I think I also got the aforementioned "no sidebars" problem when I tried this.
[*]I tried the repository listed on the Launchpad site (after tearing my hair out trying to figure out how to use it), then couldn't actually update OOo from it. It only listed a few "updates" to some packages that have nothing to do with OOo, and the update manager declares the site to be UNAUTHOURiZED.
[*]I'd really not have to use a third-party repository, if possible.
[*]I'd really like to be able to use themes of my choice, come to think of it! I strongly dislike the default Human theme.
[/LIST]

---

### Post by Jiawen on 2007-12-23
There are supposedly bugfixed versions in the proposed repository, but I see no way to enable or install them. Has anyone successfully dealt with this bug? If so, *please* describe how to do so. 

Thanks.

---

### Post by Trinità on 2008-01-03
In my fresh installation (but regolar updated) openoffice crash when saving the document. In .odt format and specially in .xml format .
But the theme is the original human and i also try with compiz enabled and disabled.

Any suggestion?

---

### Post by ppm on 2008-01-05
> **Jiawen said:**
> Here are my problems:[LIST]
[*]I use Xfce. Removing openoffice.org-gtk doesn't help anything; OOo still crashes. I think I also got the aforementioned "no sidebars" problem when I tried this.
[*]I tried the repository listed on the Launchpad site (after tearing my hair out trying to figure out how to use it), then couldn't actually update OOo from it. It only listed a few "updates" to some packages that have nothing to do with OOo, and the update manager declares the site to be UNAUTHOURiZED.
[*]I'd really not have to use a third-party repository, if possible.
[*]I'd really like to be able to use themes of my choice, come to think of it! I strongly dislike the default Human theme.
[/LIST]

Also in my case removing openoffice.org-gtk **did not help**. I ended up reinstalling the all openoffice packages, but still any OO application did not start. Based serious googling I tried to switch from fglrx display driver to ati driver and **that did work**.:)

Switching to ?Vidia card as soon as possible... :mad:

---

### Post by stuart.crouch on 2008-01-19
This is how I fixed my crashes. Maybe unique to me, maybe not.  It was the same symptons though...

[http://ubuntuforums.org/showthread.php?p=4166241](http://ubuntuforums.org/showthread.php?p=4166241)

---

### Post by Michl on 2008-02-05
I just did a fresh install of Gutsy and open office worked.  Then I did the updates available
and open office crashes right at the start and then keeps asking me to recover
documents.  No matter what I say, yes or no, it keeps asking to recover documents.


P.S.
Tried reinstalling ubuntu5 version instead of 5.3, and that didn't help anymore.  So
the solution was to upgrade to Heron and leave all my other computers running nice
stable Feisty.

---

### Post by Michl on 2008-02-05
> **FuturePilot said:**
> Updates are available to fix this. :guitar:

Nope, updates just done right now cause openoffice crashes.

---

### Post by Jiawen on 2008-05-08
I just opened OO for the first time in a month or so and got another CPU spike that meant I had to re-boot. I wish someone would fix this problem. :(

---

