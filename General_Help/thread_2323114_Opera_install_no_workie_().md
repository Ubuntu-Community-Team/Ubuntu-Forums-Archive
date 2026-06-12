---
title: "Opera install no workie (?)"
date: 2016-05-03
forum: General Help
---

### Post by Ronald_F._Guilmett on 2016-05-03
I downloaded the file opera-stable_36.0.2130.65_amd64.deb to my freshly installed Ubuntu 16.04 system and then double clicked on it, which brough up the Ubuntu software installer.  I then clicked on the **Install** button, and the install process seems to start, but then it just dies after a few seconds and opera does not in fact get installed.

What am I doing wrong?  (This process seemed to work A-OK for the several other software packages I've already installed.)

Am I the only person this has happened to?

Is there something special that needs to be diddled in order to install opera from the .deb file?

---

### Post by SuperFreak on 2016-05-03
try installing it with gdebi

---

### Post by mc4man on 2016-05-03
This is/was a [bug in  gnome & ubuntu-software]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573408") that has been fixed, the fix is in -proposed & should be available as a normal update in the very near future.
for info's sake apt (not apt-get) now handles dependencies so from a terminal this would work - 
sudo apt install /path/to/whatever.deb

---

### Post by kc1di on 2016-05-03
It installs fine on mate with gdebi
if you like opera you may also want to try vivaldi web browser web page [here ]("https://vivaldi.com/?lang=en_US"):

---

### Post by howefield on 2016-05-03
Try..

```
sudo apt install path/to/opera/debpackage
```

eg, if it is downloaded to your ~/Downloads folder..

```
sudo apt install ~/Downloads/opera-stable_36.0.2130.65_amd64.deb
```

---

### Post by Ronald_F._Guilmett on 2016-05-03
Thanks everybody.  After seeing the first response, I went ahead and installed gdebi and then used that to install the opera .deb file.  That seems to have worked rather better, *however...*

Invoking opera from an xterm window (command line) opera comes up with ***no ***main menu (i.e. the big O button normally in the upper left).  This is basically kinda ridiculous, cuz you almost can't do anything useful with Opera without that button.

I resarched this a little and found that this apparently has something to do with Unity hiding the button, *however *if one invokes Opera with the --show-opera-menu command line option, then you do get the "start menu" button in the upper left, where it should be. (There didn't seem to be any other way to get this.  It's not something that can just be diddled, apparently, in settings.)

Of course, I'm sure that there are a zillion dedicated people working on Ubuntu who are just standing around with their hands in their pockets, waiting for something to do (just kidding), so perhaps one of those folks will fix this small bit of goofiness.

**_Unrelated Strangeness:_**  While trying to find a solution for the above, I ran **Firefox** also, and used that for some judicious googling around.  As I was looking at one particular page, in Firefox (sorry, I didn't save the URL) when all of a sudden, after that specific pages had been up for several seconds, the particular tab that I was looking at, in Firefox, went all dark grey on me... you know... kinda like the whole page was some greayed-out/unavailable menu item.  The page was still visible, but it was underneath a semi-translucent dark grey overlay covering the whole page.  At first I thought that perhaps Firefox was trying to tell me my Internet connection had just gone down or something, so I tried some pings from within xterm, and no, there was no connectivity problem.

So anyway, has anybody else ever seen this kind of behavior in Firefox?  It sorta seemed to me like as if that one specific tab had caused some sort of quasi-crash in Firefox or something.  I tried to close just that one tab, and Firefox exited.  This is pretty much the strangest thing I've ever seen a web browser do, and I've been on the net for about 20+ years.

---

### Post by SuperFreak on 2016-05-03
Could it be you have activated Web Developer under Tools by mistake

---

### Post by Ronald_F._Guilmett on 2016-05-03
> **SuperFreak said:**
> Could it be you have activated Web Developer under Tools by mistake

You talkin' about Firefox now, or Opera?

Well, anyway, the answer is the same in both cases.  Nope, I didn't activate anything unusual in either case.

---

### Post by SuperFreak on 2016-05-03
> **Ronald_F._Guilmett said:**
> You talkin' about Firefox now, or Opera?

Well, anyway, the answer is the same in both cases.  Nope, I didn't activate anything unusual in either case.

I was referring to Firefox. I find Web Developer which is preinstalled is activated inadvertently on my PC quite often and it grays out the whole web page. For example copy and paste using the mouse can sometimes activate it

---

### Post by mc4man on 2016-05-03
> **Ronald_F._Guilmett said:**
> 

Invoking opera from an xterm window (command line) opera comes up with ***no ***main menu (i.e. the big O button normally in the upper left).  This is basically kinda ridiculous, cuz you almost can't do anything useful with Opera without that button.

I resarched this a little and found that this apparently has something to do with Unity hiding the button, 
In an ubuntu session the so-called opera menu is in the global menus. If you don't want them there & rather in the opera window (opera menu) then edit opera.desktop.

---

### Post by leilton on 2016-07-06
I know, must be one of those Windows cross overs, but no, have been away for some while, and this new 16.04 is really throwing me.   for the life of me cannt get opera to open.
Have downloaded to downloads,double clicked and get , no file name-for-app results to show, then tried solutions offered by Howefield,and got Unable to locate package path/to/opera &Unsupported file /home/tony/Downloads/opera-stable_36.0.2130.65_amd64.deb given on commandline .   At my age,grey cells not what they should be,but any help, in basic english would be appreciated.

[FONT=Verdana]
[/FONT]

---

### Post by X-RED_Tech on 2016-07-06
Are you trying to install a 64-bit deb in a 32-bit system? That would explain the "unsupported file"...
Anyway you should fully update your system so you have the bug preventing third party software to be installed by the new default software manager corrected. And/or you can install GDebi as suggested above and open the deb with it (Right click, Open with...). It will tell if there's something wrong with the deb you're trying to install, if it has unsolvable dependencies or wrong architecture. If it doesn't complain - "all dependencies satisfied" - go ahead and click install.

---

