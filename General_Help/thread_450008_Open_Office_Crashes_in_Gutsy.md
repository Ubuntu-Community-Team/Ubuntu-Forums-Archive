---
title: "Open Office Crashes in Gutsy"
date: 2007-05-20
forum: General Help
---

### Post by gjtoth on 2007-05-20
Open Office components crash when I attempt to enter any data.  After about 3-4 keystrokes... crash.  I've been able to duplicate this on two systems, one with AMD 3200+ and the other with Pentium 4.  Both machines run 1 gig of RAM.  Both systems were upgraded from clean installs of Feisty.

Anyone else get this?

---

### Post by ronacc on 2007-05-20
spellcheck has been crashing OO and FF disable it and see if the problem goes away , there  are several posts on this.

---

### Post by gjtoth on 2007-05-20
> **ronacc said:**
> spellcheck has been crashing OO and FF disable it and see if the problem goes away , there  are several posts on this.

Thanks for the info.  I did a search, as I always do, and didn't come up with anything pertaining to OO crashing in Gutsy.  

That did the trick.

---

### Post by ronacc on 2007-05-20
yeah most of the posts are about firefox and only mention OO in passing.

---

### Post by ButteBlues on 2007-05-20
Firefox was updated a long while back to fix that... on the other hand, OO still waits to be rebuilt against current hunspell packages. :(

---

### Post by AlexenderReez on 2007-05-21
i'm using feisty libhunspell so a while.....it doesn't give any problem.....

---

### Post by Icarosaurus on 2007-05-28
yes.. OO crashes due to spell checker...
Any way to solve the problem and continue using spell checker?
Or we have just to wait for the OO rebuilding?

---

### Post by lunamystry on 2007-08-10
Uhm my open office does not open for some reason. I just installed gusty gibbon two days back and I did a apt-get dist upgrade today but open office still does not work. I shows the splash (and now its a new splash) then nothing. All the open office things. 

What do I do?

---

### Post by AlexenderReez on 2007-08-10
> **lunamystry said:**
> Uhm my open office does not open for some reason. I just installed gusty gibbon two days back and I did a apt-get dist upgrade today but open office still does not work. I shows the splash (and now its a new splash) then nothing. All the open office things. 

What do I do?

hm...latest update snapshot oo 2.3 should fixed it:)

---

### Post by jbaloul on 2007-08-15
nope, its still broke even on 2.3

```

jacob@jbdual:~ :) $ dpkg -l |grep -i "openoffice"
ii  openoffice.org                             2.3.0~src680m224-1ubuntu2               OpenOffice.org Office suite
ii  openoffice.org-base                        2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite - database
ii  openoffice.org-calc                        2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite - spreadsheet
ii  openoffice.org-common                      2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite architecture ind
ii  openoffice.org-core                        2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite architecture dep

```

JB

---

### Post by paulle on 2007-08-15
> **lunamystry said:**
> Uhm my open office does not open for some reason. I just installed gusty gibbon two days back and I did a apt-get dist upgrade today but open office still does not work. I shows the splash (and now its a new splash) then nothing. All the open office things. 

What do I do?

The same thing happens too me till now.

---

### Post by AlexenderReez on 2007-08-15
> **jbaloul said:**
> nope, its still broke even on 2.3

```

jacob@jbdual:~ :) $ dpkg -l |grep -i "openoffice"
ii  openoffice.org                             2.3.0~src680m224-1ubuntu2               OpenOffice.org Office suite
ii  openoffice.org-base                        2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite - database
ii  openoffice.org-calc                        2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite - spreadsheet
ii  openoffice.org-common                      2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite architecture ind
ii  openoffice.org-core                        2.3.0~src680m224-1ubuntu2               OpenOffice.org office suite architecture dep

```

JB

i can use all 0o application except 0o presentation.....i don't know why...it seems broken...

---

### Post by Anagonda on 2007-08-15
Yeah, my open office is down too. Tried to calc,write etc and all hangs on "loading screen". It freezes my other cpu to 100% untill I kill openoffice.

I tried to run open office calc and write from terminal, or this is the normal way I do, but here is the result:

```
anagonda@anagonda:~$ oowriter 

(process:7451): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.13.7/gobject/gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7451): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:7451): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

```

---

### Post by Anagonda on 2007-08-15
Okay, I tried with my laptop. It has been installed with clean feisty and after first login dist-upgraded to gutsy, that was before first tribe. Two days ago was done dist-upgrade. Open office calc opens slowly but fine! Now I did dist-upgrade(about 10 minutes ago) and it still opens.

So there must be something that old systems doesn't have. My home pc is running old setup, has been the same install for over 3 years of ubuntu. Just dist-upgrades and alot "alphas,flight,tribes etc".

Ok, did dist-upgrade for my home pc. Still the same error, but my other cpu doesn't freeze to 100%. So it's a bit better...

---

### Post by flowbot on 2007-08-17
> **Anagonda said:**
> Yeah, my open office is down too. Tried to calc,write etc and all hangs on "loading screen". It freezes my other cpu to 100% untill I kill openoffice.

I tried to run open office calc and write from terminal, or this is the normal way I do, but here is the result:

```
anagonda@anagonda:~$ oowriter 

(process:7451): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.13.7/gobject/gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7451): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:7451): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

```

I get the same thing on Gutsy Xubuntu ... haven't been able to open a single document with openoffice yet.

---

### Post by AlexenderReez on 2007-08-17
just finish upgrade ..it is seems everything working back in my system:)

---

### Post by jbaloul on 2007-08-17
i did an upgrade and still no luck...i had to take "drastic" measures to get mine working again as i need my openoffice for day to day....so for  those interested in hacking a bit to make it work here is what i did....please use it only as a refference and make sure you know what your doing on your system....

I downloaded the latest dev snapshot from openoffice.org:
[http://openoffice.bouncer.osuosl.org/?product=OOo-Dev&os=linuxinteldeb&lang=en-US&version=OOG680_m1](http://openoffice.bouncer.osuosl.org/?product=OOo-Dev&os=linuxinteldeb&lang=en-US&version=OOG680_m1)
```

OOo-Dev_OOG680_m1_LinuxIntel_install_en-US_deb.tar.gz

```

then composed the list of packages i wanted to remove from the ubuntu auto install
```

dpkg -l |grep -i openoffice | cut -f 3 -d ' ' | tr -s '\n' ' '

```

then used that list to apt remove my stuff...
```

sudo apt-get remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-debian-files openoffice.org-draw openoffice.org-filter-binfilter openoffice.org-filter-mobiledev openoffice.org-help-en-us openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-us openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-human openoffice.org-style-industrial openoffice.org-thesaurus-en-us openoffice.org-writer openoffice.org2 openoffice.org2-base openoffice.org2-calc openoffice.org2-common openoffice.org2-core openoffice.org2-draw openoffice.org2-evolution openoffice.org2-gnome openoffice.org2-impress openoffice.org2-java-common openoffice.org2-kde openoffice.org2-l10n-en-gb openoffice.org2-l10n-en-us openoffice.org2-math openoffice.org2-writer

```

then finally went into the dir containign the debs extracted from the file i downloaded earlier and installed like this:
```

sudo dpkg -i ooo-dev-base_2.3.0-1_i386.deb ooo-dev-calc_2.3.0-1_i386.deb ooo-dev-core01_2.3.0-1_i386.deb ooo-dev-core02_2.3.0-1_i386.deb ooo-dev-core03_2.3.0-1_i386.deb ooo-dev-core03u_2.3.0-1_i386.deb ooo-dev-core04_2.3.0-1_i386.deb ooo-dev-core04u_2.3.0-1_i386.deb ooo-dev-core05_2.3.0-1_i386.deb ooo-dev-core05u_2.3.0-1_i386.deb ooo-dev-core06_2.3.0-1_i386.deb ooo-dev-core07_2.3.0-1_i386.deb ooo-dev-core08_2.3.0-1_i386.deb ooo-dev-core09_2.3.0-1_i386.deb ooo-dev-core10_2.3.0-1_i386.deb ooo-dev-draw_2.3.0-1_i386.deb ooo-dev-emailmerge_2.3.0-1_i386.deb ooo-dev-gnome-integration_2.3.0-1_i386.deb ooo-dev-graphicfilter_2.3.0-1_i386.deb ooo-dev-headless_2.3.0-1_i386.deb ooo-dev-impress_2.3.0-1_i386.deb ooo-dev-javafilter_2.3.0-1_i386.deb ooo-dev-kde-integration_2.3.0-1_i386.deb ooo-dev-math_2.3.0-1_i386.deb ooo-dev-onlineupdate_2.3.0-1_i386.deb ooo-dev-pyuno_2.3.0-1_i386.deb ooo-dev-testtool_2.3.0-1_i386.deb ooo-dev-writer_2.3.0-1_i386.deb ooo-dev-xsltfilter_2.3.0-1_i386.deb

```

if all is well....it installs in /opt/ooo-dev2.3/

so you can do something like this:
```

export PATH=/opt/ooo-dev2.3/program:$PATH

```
i added it to my .bashrc

then you will be able to run ...
```

sbase
scalc
sdraw
smath
soffice
swriter

```


good luck & enjoy,
JB
[http://howtoforums.net](http://howtoforums.net)

---

### Post by reinderien on 2007-08-17
I have a fully apt-updated Gutsy system, and I still receive the "Glib-CRITICAL" errors and it freezes while loading every time. I'm not willing to download the development files and do the installation myself, as it should be built to work straight from apt, and anything else is just avoiding the problem instead of fixing it.

---

### Post by disturbedite on 2007-08-17
i've had the same problem as reinderien.  the last version was "broken" as well and so is the current version.  (2.3.0~src680m224-1ubuntu2).  this error just to clarify is the one i get:
disturbedite@disturbedite-desktop:~$ ooffice -writer

(process:17941): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.13.7/gobject/gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:17941): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:17941): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

---

### Post by flowbot on 2007-08-17
yeah, fully up-to-date and still no good for me. i've noticed a few errors with glib in other applications, so maybe the problem's with the glib packages ... is there a bug-report on this?

---

### Post by flowbot on 2007-08-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/127944](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/127944) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **flowbot said:**
> yeah, fully up-to-date and still no good for me. i've noticed a few errors with glib in other applications, so maybe the problem's with the glib packages ... is there a bug-report on this?

Ok, it's being tracked in Launchpad ... quick fix (for me, anyway) is to install openoffice.org-gtk.

---

### Post by disturbedite on 2007-08-17
i tried that before and it didn't work.  (i'm on kubuntu, maybe thats why?)

---

### Post by hoodwink on 2007-08-18
I'm just lucky, it seems. I'm using xubuntu-desktop and OO 2.3.0~src680m224-1ubuntu1.

No crashes of any sort (including spellcheck) with Writer or Spreadsheet. No unusual CPU utilization. Didn't see any problems on earlier releases either.

---

### Post by 7/9 on 2007-08-20
Same thing here - using OO 2.3.0-src680m224-1ubuntu2 on Xubuntu Gutsy Gibbon (Tribe 4). 

Solved my GTK crashes by installing openoffice.org-gtk (also 2.3.0-src680m224-1ubuntu2) as mentioned earlier on the board. Should openoffice.org-gtk be added to OO's depends?

---

### Post by aQsu on 2007-08-30
I had similar problem w/ Feisty. Solved it by changing the theme. There was a conflict apparently...

---

### Post by morphet on 2007-09-30
> **aQsu said:**
> I had similar problem w/ Feisty. Solved it by changing the theme. There was a conflict apparently...

Thanks, aQsu! I needed to finish a spreadsheet by tomorrow, and Calc crashed everytime I opened help, cell format, etc... Turns out, the art.gnome.org theme "Alluminum Alloy" was the problem. Changed it and Calc is rock solid.:KS

---

### Post by Borg on 2007-10-04
Open Office is useless now, nothing but crashed and problems. Lets hope a fix comes out soon.

---

### Post by LongTooth on 2007-10-04
Just clicked on 'Updates' notifier. What ever was installed seem to fix the OpenOffice problem because OO doesn't crash any more.

---

### Post by pirxx on 2007-10-04
Houston, we have a problem: OpenOffice 2.3 Write on Gutsy starts once, but after closing it won't start again.

After having started and closed OpenOffice Write, OpenOffice Calc, Impress and Base won't open at all.

Updates applied are all up to the minute of this writing.

---

### Post by Unicast on 2007-10-04
No problems with OpenOffice 2.3 here:

[img]http://img407.imageshack.us/img407/56/screenshothg3.png[/img]

---

### Post by LongTooth on 2007-10-04
Don't know what to say. I've got all those apps open and have no problems. I am able to open OO and close it and reopen it without an crashing.

---

### Post by pirxx on 2007-10-05
A complete re-install of OpenOffice 2.30 brought relief: it seems to be working fine now.

---

### Post by awakatanka on 2007-10-05
> **pirxx said:**
> Houston, we have a problem: OpenOffice 2.3 Write on Gutsy starts once, but after closing it won't start again.

After having started and closed OpenOffice Write, OpenOffice Calc, Impress and Base won't open at all.

Updates applied are all up to the minute of this writing.

Same behaivor over here, if i start it in terminal with sudo it works everytime. From kubuntu kicker menu it start once and never again till i reboot.

dictooo still crashes and only works if i install also openoffice.org (feisty bug with low priorty and still there)

---

### Post by monsieurdozier on 2007-10-12
Open Office seems to be working fine for right now, except when I try to do a manual break in Writer.

I try to insert say a page break and it gives me an unexpected error and crashes.  Using ver 2.3.0.

---

### Post by lnogueir on 2007-10-13
(SOLVED) for me!

I have the same problem! Then I change the theme and like by a miracle, oppenoffice never crashes again!


Try change theme... Like I said it works for me!

---

### Post by Dawnrazor on 2007-10-15
> **lnogueir said:**
> (SOLVED) for me!

I have the same problem! Then I change the theme and like by a miracle, oppenoffice never crashes again!


Try change theme... Like I said it works for me!

Yes it works, but this cannot be the solution for a final in 3 days

---

### Post by rfurman24 on 2007-10-15
My OO will not start consistently unless I remove openoffice-gtk. This is unacceptable. I hope it is fixed soon.

---

### Post by mabovo on 2007-10-15
> **lnogueir said:**
> (SOLVED) for me!

I have the same problem! Then I change the theme and like by a miracle, oppenoffice never crashes again!


Try change theme... Like I said it works for me!

My OO was a mess even after last updates so I follow Dawnrazor tip and reinstalled all OO pack trough synaptic and now it is ok ! Open very fast.
I agree that is not a solution but solved for me.

---

### Post by rfurman24 on 2007-10-15
I have tried to uninstall and reinstall with no luck. I actually just got two updates within the past few hours with no luck.

---

### Post by LenzM on 2007-10-16
I had the same problem and it was fixed by switching to the standard Human theme.

Hope this gets fixed so I don't have to look at orange borders.

---

### Post by dahlheim on 2007-10-16
> **rfurman24 said:**
> I have tried to uninstall and reinstall with no luck. I actually just got two updates within the past few hours with no luck.

what worked for me, twice (meaning on two different systems with "updated" gutsies.  i've been avoiding updates on a couple other machines with more satisfaction, awaiting the official release):

sudo apt-get remove --purge openoffice*
sudo apt-get autoremove
yes | rm -r ~/.openoffice*   (not sure if this step is completely necessary, but i had nothing to save/lose)
sudo apt-get install openoffice.org

hope this helps somebody.

---

### Post by Dark_Stang on 2007-10-16
That fixed the freezing. Except now whenever I run Impress (Presentation as Ubuntu calls it) It automatically goes to full screen and covers up the gnome bars.

---

### Post by dahlheim on 2007-10-16
> **Dark_Stang said:**
> That fixed the freezing. Except now whenever I run Impress (Presentation as Ubuntu calls it) It automatically goes to full screen and covers up the gnome bars.

got me there, i'm actually currently creating a presentation in Impress without any trouble...

---

### Post by Dark_Stang on 2007-10-17
I really hope this is fixed for the release...

Edit: Just tried downloading and installing from OpenOfice.org's website. And it's actually gotten worse. Now it freezes the moment I try to open or save anything.

---

### Post by n00buntu NJ on 2007-10-17
> **dahlheim said:**
> what worked for me, twice (meaning on two different systems with "updated" gutsies.  i've been avoiding updates on a couple other machines with more satisfaction, awaiting the official release):

sudo apt-get remove --purge openoffice*
sudo apt-get autoremove
yes | rm -r ~/.openoffice*   (not sure if this step is completely necessary, but i had nothing to save/lose)
sudo apt-get install openoffice.org

hope this helps somebody.

I was just about to post the very same suggestion.  I just did this on my system, and it did the trick.  In fact, first I tried to:

```
sudo apt-get remove --purge openoffice.org
```

..in hopes that I could remove every thing by removing the meta-package, only the meta-package "openoffice.org" was not installed on my machine (neither was openoffice.org2).  

So I resorted to a:

```
sudo apt-get remove --purge openoffice.org*
```

...followed by: 

```
sudo apt-get install openoffice.org
```
EDIT: I originally posted that I used the package "openoffice.org2", but I just looked and it is only a pointer to the metapackage "openoffice.org" - so you should probably use that instead...

I also wanted the Tango icons for openoffice, so I did a:

```
sudo apt-get install openoffice.org-style-tango
```

Now everything works just fine.

Hope this helps!

---

### Post by Speedoo on 2007-10-17
My Open Office is crashing too.  I can input data, but in the spreadsheet, I need to format cells.  When I right-click a cell, or click on Format, the application freezes.  After the first time, I know to save the unformatted version before trying to format, but at some point (today!) I'm going to need a completed, formatted spreadsheet.  My job involves copying data from a Word schedule into a spreadsheet and emailing it to my employees.  When the spreadsheet freezes, it also freezes the Word doc (in OO word processor.)  I tried unchecking the spell checker, and that froze the application too!
I'm using 2.3 in Gutsy on an AMD64.  Could Compiz Fusion have anything to do with this? (just guessing at this point.)
Thanks for any help,

---

### Post by Speedoo on 2007-10-17
Wow.  Just tried the above code (removing and reinstalling openoffice.)  Now, I've lost my desktop background, and when I open a Word document, I can see the document, but can't edit or even close openoffice.  It's full-screen, and there's no taskbars or anything. I got out of it by rebooting my desktop (CTRL-ALT-Backspace.)  NOW what do I do?
Ubuntu is great...when it works!

---

### Post by rfurman24 on 2007-10-17
> **dahlheim said:**
> what worked for me, twice (meaning on two different systems with "updated" gutsies.  i've been avoiding updates on a couple other machines with more satisfaction, awaiting the official release):

sudo apt-get remove --purge openoffice*
sudo apt-get autoremove
yes | rm -r ~/.openoffice*   (not sure if this step is completely necessary, but i had nothing to save/lose)
sudo apt-get install openoffice.org

hope this helps somebody.


Yes, that works great, BUT it removes OO-GTK which defeats the point. I appreciate the help very much but it is a little ridiculus that this problem exists the day before release.

---

### Post by Speedoo on 2007-10-17
What is oo-gtk?  Found a couple references, but no explanation.  I tried the remove, purge, reinstall.  It turns out Compiz Fusion desktop effects were screwing up my openoffice.  When I disable effects, openoffice runs fine.  But it somehow looks different than it did.  Could this be because of my now missing oo-gtk?
Thanks,

---

### Post by rfurman24 on 2007-10-17
Open Office-GTK. By removing Openoffice.org-Gtk. It disables openoffice's ability to obey gtk themes.

---

### Post by nowshining on 2007-10-17
> **rfurman24 said:**
> Open Office-GTK. By removing Openoffice.org-Gtk. It disables openoffice's ability to obey gtk themes.
edit: thanks furman for that info. :)
openoffice works fine for me at least for now, as I don't use that much however I didn't update last time due to it was not needed on my .x86 machine and only fixed someone on a sparc one. :P oh and I don't want to download newer ones every other day..or so lolz it works fine for me of course and yes I locked the version in synaptic if anyone is wondering.

---

### Post by texadactyl on 2007-10-21
Same with me.  100% CPU or crashing in write, my day-to-day writing production-oriented tool.  Major disappointment and negative surprise!  Fortunately for my family, I have all our stuff rooted at /home in its own HDD partition and I have regularly backed up /home onto a USB portable HDD.

So, I am jettisoning 7.10 in favour of a stable distro/ooo combo, probably Ubuntu 7.04.
I do not need the latest anyways but my non-techie significant other needs to get back to work.

Incidentally, that development patch did work-around on another of my machines.  Thanks.

---

### Post by kolinab on 2007-10-21
See also related threads:

[http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088) 
[http://ubuntuforums.org/showthread.php?t=450008](http://ubuntuforums.org/showthread.php?t=450008) (this thread)
[http://ubuntuforums.org/showthread.php?t=582152](http://ubuntuforums.org/showthread.php?t=582152)
[http://ubuntuforums.org/showthread.php?t=583813](http://ubuntuforums.org/showthread.php?t=583813)
[http://ubuntuforums.org/showthread.php?t=563781](http://ubuntuforums.org/showthread.php?t=563781) in closed Gutsy Forum

---

### Post by PACSFerret on 2007-10-23
> **aQsu said:**
> I had similar problem w/ Feisty. Solved it by changing the theme. There was a conflict apparently...
That works for me.  Writer was crashing but couldn't pin down a pattern - could have been a certain time after opening (a few seconds).  I had a customised theme - changed to a standard and seems to be OK now.:guitar:

---

### Post by eyemeansit on 2007-10-24
Crashes happening for me as well in Gutsy. I have uninstalled OO, reinstalled a couple of times. For me, the crashes happen anytime I try to do anything in the menus... including trying to change the theme! I think I will try to download and install the official version from the Open Office website.

---

### Post by treblesix on 2007-10-24
I had the problems of Office crashing when i selected print.

Removing and re-installing OO has fixed the problem.


sudo apt-get remove --purge openoffice*
sudo apt-get autoremove
sudo apt-get install openoffice.org

---

### Post by eyemeansit on 2007-10-24
Totally removing anything to do with openoffice.org through Synaptic, then reinstalling openoffice.org without openoffice.org-gtk and without openoffice.org-gnome fixed it for me.

---

### Post by craigyjack on 2007-10-25
> **treblesix said:**
> I had the problems of Office crashing when i selected print.

Removing and re-installing OO has fixed the problem.


sudo apt-get remove --purge openoffice*
sudo apt-get autoremove
sudo apt-get install openoffice.org

Thank you! Thank you! Thank you!
I was having the exact same problem, when I would click Print OO would either crash or lock up (and I would have to Force Quit).

My guess is that is had to do with old config files left from OO 2.2 in Feisty (because i dont format my /home partition at gutsy install). That is really not cool though, because I almost freaked because I thought I wasn't going to be able to print my documents.

Thanks,
Craig

ps. special thanks for posting the commands, not just telling what to do. giving the commands just makes it so much easier and clearer. thanks a bunch for that.

---

### Post by kolinab on 2007-10-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Just a note to those following this. Apparently a fix for the gtk related crash has been released into OO.org. There is work being done to somehow propagate (??!) the fix to the Ubuntu packages. I have absolutely no understanding of how any of this works behind the scenes or what is really going on, but if you want to follow along with the process you can read the launchpad page relating to this bug. I might be kind of learning how this process works, but I'm pretty sure there's a computer somewhere quietly churning away on fixing this right now.

Cheers,

K

---

### Post by treblesix on 2007-10-25
> **craigyjack said:**
> Thank you! Thank you! Thank you!
I was having the exact same problem, when I would click Print OO would either crash or lock up (and I would have to Force Quit).

My guess is that is had to do with old config files left from OO 2.2 in Feisty (because i dont format my /home partition at gutsy install). That is really not cool though, because I almost freaked because I thought I wasn't going to be able to print my documents.

Thanks,
Craig

ps. special thanks for posting the commands, not just telling what to do. giving the commands just makes it so much easier and clearer. thanks a bunch for that.

You are very welcome mate. Glad it helped :)

---

### Post by 8f27e956 on 2007-10-26
I too have the freeze; it does so whenever a oo operation would invoke a dialog box or popup menu.  It *is* related to 3d affects being enabled (compiz).

I'm otherwise freeze-free in 2d mode.

Still in search of a legit fix...

/Scott

---

### Post by 8f27e956 on 2007-10-26
> **PACSFerret said:**
> ...I had a customised theme - changed to a standard and seems to be OK nowI read this. I too had custom theme. I just made it "standard" and oo seems fine, though a bit too soon to say "stable" or "all in order."

/Scott

---

### Post by caen1944 on 2007-10-27
I am having a similar problem as someone else reported.

I can launch all the openoffice programs EXCEPT presentation. It just hangs at the splash screen. This is a fresh install of 7.10, not an upgrade.

This is rather annoying, I hope we find the cure.

Good luck

---

### Post by FuturePilot on 2007-10-27
For now you can remove openoffice.org-gtk 
They're working on the issue now
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526")

---

### Post by pelo8280 on 2007-10-28
That's all I needed!

I was using the aeroclone theme, switched it to human, now it works like a charm!

---

### Post by z0mbie on 2007-10-29
Freezes when I open Spreadsheet or Database. Hoping to substitute MS Office. Will try removing openoffice.org-gtk. 

Even though it looks bit ugly, removing **openoffice.org-gtk** worked:

```
sudo apt-get remove openoffice.org-gtk
```

---

### Post by bluehue on 2007-10-29
> **aQsu said:**
> I had similar problem w/ Feisty. Solved it by changing the theme. There was a conflict apparently...
Yes! Thank you! Went back to the default "Human" theme and it works fine now :)

---

### Post by Royce on 2007-10-30
Thanks for the help with OpenOffice 2.3 after the 7.1 update  Was having numerous problems with crashing.  Spell check being the most obvious and repeatable.  Changing the desktop theme back to default Human while not as easy on the eyes solved the problems.  This is the first time for me that Ubuntu update caused any kind of a problem.

---

### Post by pelo8280 on 2007-11-01
You don't have to switch it to human; any of the built-in themes work fine.  And only "Controls" (under advanced) have to be from the built-in theme; you can use icons, etc. from any theme and openoffice will run fine.

---

### Post by kolinab on 2007-11-02
> **pelo8280 said:**
> You don't have to switch it to human; any of the built-in themes work fine.  And only "Controls" (under advanced) have to be from the built-in theme; you can use icons, etc. from any theme and openoffice will run fine.

That has not been my experience. My OO was crashing with Controls set to built in 'Redmond,' Window border set to 'clearlooks,' and icons set to Human (all built in themes). However, I don't doubt that diddling with theme settings further could make the crashing stop without removing oo.org-gtk.

K

---

### Post by gabz8472 on 2007-11-12
> **gjtoth said:**
> Open Office components crash when I attempt to enter any data.  After about 3-4 keystrokes... crash.  I've been able to duplicate this on two systems, one with AMD 3200+ and the other with Pentium 4.  Both machines run 1 gig of RAM.  Both systems were upgraded from clean installs of Feisty.

Anyone else get this?

Have the same problem, although it doesn't happen all the time, this is the first time actually, but after 3 or 4 keystrokes, down it goes. Sometimes I get as far as a single sentence, but before I can save it, its gone.  I don't want to tinker with removing stuff from the system, but can somebody tell us what's going on?

---

### Post by pelo8280 on 2007-11-12
Run this command from the terminal and reply with the output that you get
```
ooffice -writer
```

---

### Post by gabz8472 on 2007-11-12
> **pelo8280 said:**
> Run this command from the terminal and reply with the output that you get
```
ooffice -writer
```

All it did was to open my writer. What was it supposed to do?

---

### Post by FuturePilot on 2007-11-12
> **gabz8472 said:**
> All it did was to open my writer. What was it supposed to do?

Try to reproduce the crash now. When it crashes you'll see a whole bunch of stuff show up in the terminal.

---

### Post by orpat on 2007-11-27
> **aQsu said:**
> I had similar problem w/ Feisty. Solved it by changing the theme. There was a conflict apparently...

I can't believe it was that easy. I was using Crux, switched and now OO is working again.
Thanks.

---

### Post by GPJ on 2007-12-06
Dear All,
In my case (I am using KDE), it seems the problem is with the package openoffice.org-KDE (KDE integration for OO). I don't know why, but installing it separetely from the OO suite after installing all the other packages running Adept Package Manager seems to work.
Regards.

---

### Post by abrazafi on 2007-12-10
Hi All,

I have similar problem, see my thread: OpenOffice 2.3 in kubuntu (general help)
I wanted to install the dictionary (from the wizard) and OO is keep telling me 
the following:

"OpenOffice.org Document Recovery
Due too an unexpected error, OpenOffice.org crashed. All files you
were working on will now be saved ..."

Of course, the dictionary is not installed and keep looping on this 
message.

Thanks for any advice.
Abdon

---

### Post by to young on 2007-12-11
> **pirxx said:**
> Houston, we have a problem: OpenOffice 2.3 Write on Gutsy starts once, but after closing it won't start again.

After having started and closed OpenOffice Write, OpenOffice Calc, Impress and Base won't open at all.

Updates applied are all up to the minute of this writing.

Exact same problem.  I did a fresh Open office install from Synaptic.  It opened the word processor only once and never after that.  Somebody pleas help.

---

### Post by thunder.dude44 on 2007-12-16
I find this completely rediculous. How is it that openoffice.org-gtk can be the only problem? And why is this not fixed by now? Now my OOO looks really lame next to my dark background. ugghh.

---

### Post by pelo8280 on 2007-12-16
I find this pretty lame, too.  The bug is reported as critical: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526)
And also is an unofficial workaround: [http://codeprobe.de/tmp/ooo/](http://codeprobe.de/tmp/ooo/) All the packages here have the bug fixed.  I haven't tried it out yet.

---

