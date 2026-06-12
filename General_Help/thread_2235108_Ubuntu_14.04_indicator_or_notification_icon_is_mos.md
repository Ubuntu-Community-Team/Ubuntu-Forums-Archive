---
title: "Ubuntu 14.04 indicator? or notification? icon is mostly offscreen and unclickable."
date: 2014-07-18
forum: General Help
---

### Post by landstander on 2014-07-18
**_Preamble:_**
I've searched the threads and the bug reports but couldn't find anything related to this issue.

**_Relevant system specs:_**
OS: Ubuntu 14.04
Desktop: Gnome3
Video Card: NVIDIA GeForce 8800 GT
Video Card Driver: nvidia-331-updates, version: 331.38-0ubuntu7
...yes I know this is an ancient card, planing on upgrading soon.

**_Description of problem:_**
On the desktop there is an icon in the lower right hand corner of the screen which in Ubuntu 12.04 LTS Gnome3 desktop, is where minimized programs and notifications of system issues, media notifications (USB auto-mounted or removeable, etc.) would appear. After upgrading from 12.04 LTS to 14.04 LTS, this icon indicator notification thing is now mostly offscreen and there doesn't seem to be a way to get it to show up. The main problem with this is that programs that are minimized to this area will forever be running in the background with no way to access them again without attempting to relaunch the programs which of course is only possible if you know or remember what program has been minimized to this area since it is no longer visible on screen.

Here is an image of what I'm talking about.
[IMG]http://imagizer.imageshack.us/v2/895x644q90/661/cc2b2c.png[/IMG]
The above image is a modified image of my desktop. The image has been cropped to fit better within the guidelines of this forum.
In the lower right hand side of the image, you can see the very top edge of the unresponsive purple icon.

**_Questions:_**
1.) Would this be considered a bug that I could file a bug report about?
2.) If this would not be considered a bug, then how can I describe this problem more clearly, and what should I do to find help in resolving the problem?
3.) If this is a bug, then what is the name of whatever that offscreen icon represents, what package is it associated with, and would I file the bug report on that package or on some higher level package like the Gnome3 desktop under which this icon appears?

---

### Post by Jesse_Campton on 2014-07-19
Just a thought, when you minimize your applications/windows to that purple icon, does alt+Tab allow you too see these applications in the switcher?

---

### Post by grahammechanical on 2014-07-19
If I remember correctly Gnome 3 shell has an Activities option in the top right corner and not Applications. Have you installed the Classic extension? If so I would suggest uninstalling the classic extension, rebooting and re-installing it. Have you set up any of the Ubuntu Gnome PPAs?

Regards.

---

### Post by landstander on 2014-07-19
> **Jesse_Campton said:**
> Just a thought, when you minimize your applications/windows to that purple icon, does alt+Tab allow you too see these applications in the switcher?

After minimization, pressing alt+tab does not show the minimized application in the alt+tab switcher's list of currently running applications.

---

### Post by landstander on 2014-07-19
> **grahammechanical said:**
> If I remember correctly Gnome 3 shell has an Activities option in the top right corner and not Applications. Have you installed the Classic extension? If so I would suggest uninstalling the classic extension, rebooting and re-installing it. Have you set up any of the Ubuntu Gnome PPAs?

Regards.

I'm not sure what the "classic extension" is. I have a few gnome-shell extensions loaded from extensions.gnome.org, all of which have a button on that website next to each installed extension for uninstalling that extension, but non of the uninstall buttons on that page seem to do anything.

As far as the "Activities" option, on a fresh install of Ubuntu running the Gnome3 desktop my "Activities" option was on the upper left corner of the screen, and my system stuff (logout, etc) was on the upper right corner of the screen with the clock at top center. I have since replaced my "Activities" option with a gnome-shell extension that shows my applications instead as I have never found a good use for the Activities viewing mode.

I will attempt to look up "classic extension" to see if I can figure out what you are referring to.

After the upgrade to Ubuntu 14.04, I was following a few different "some number of things to do after upgrading" website suggestions and have only installed those options that seemed like it might return most of the Ubuntu 12.04 useability features back that were removed in 14.04. Things like making Nemo the default file manager, using terminator instead of gnome-terminal to get transparency working again, and general stuff like this. In doing so I had to install a few PPA's that I've used in the past and haven't had any trouble with. As far as the Gnome PPA's I'm not sure if I've ever had those installed. Since I installed Ubuntu 12.04 with the Gnome3 desktop off of a disk, there was never any need to include a PPA for it, and when upgrading to 14.04 it recognized that I was using the Gnome3 desktop and I assume it just left it that way since it booted up into that desktop.

---

### Post by landstander on 2014-07-19
grahammechanical:
I've just checked both extensions.gnome.org, and the synaptics package manager and could find no record of a "classic extension". If you are referring to the flashback or classic login session, I'm using a standard Gnome3 session, no classic or flashback in use, although that type of session is available in the login menu.

---

### Post by buzzingrobot on 2014-07-19
Gnome Shell should display a Message Tray across the length of the bottom of the display when the cursor is pushed to the bottom edge.  Notification message pop up from the center position of the bottom of the display. The addition of Gnome extensions should not cause the message tray's disappearance. Are both those functioning in your install?

Minimized programs in Gnome Shell do not maintain icons in the Message Tray.  They don't maintain icons anywhere.  By default, clicking on the Dash icon of an app that is running opens that window, if it is minimized, and moves the focus of the display there.  Indicators and old-fashioned applets *do* put icons in the Message Tray.

Gnome Shell, in any version since the beginning, does not show the little purple icons that's in your image.

The Linux Mint team has removed most (all?) of Cinnamon's and Nemo's Gnome dependencies.  The flip side is that it might make it less compatible with Gnome Shell.

My suggestion -- you won't like it -- is to back out all the PPA's (install and use ppa-purge), comment out any non-Canonical source lines in /etc/apt/sources.list, and then do "apt-get update" and "apt-get upgrade".  If that works smoothly, and you have a standard functioning Gnome Shell, then uncomment non-Canonical lines in sources.list one at a time, and repeat the update/upgrade cycle until if/when you find something that breaks the display. When that happens, remove the culprit and the line in sources.list  

Then, repeat that exercise with the previous PPA's. Doing all that will help identify the specific packages that cause the breakage you see. 

Yes, it's an arduous task, so it might be easier just to reinstall and go from there.

(Also, note that PPA's are not always maintained and the packages on offer are not always available for the current Ubuntu releases. You would need to visit each PPA's launchpad.net page to check. If you used a PPA in 12.04 that replaced an important package, and the PPA did not make available the same package for 14.04, then an upgrade or dist-upgrade might have left your install relying on that outdated 12.04 package.)

---

### Post by landstander on 2014-07-19
> **buzzingrobot said:**
> Gnome Shell should display a Message Tray across the length of the bottom of the display when the cursor is pushed to the bottom edge.  Notification message pop up from the center position of the bottom of the display. The addition of Gnome extensions should not cause the message tray's disappearance. Are both those functioning in your install?
Ah ok, this confirms that this is the notification area I'm dealing with. Thanks for the info however, for whatever reason placing the mouse at the lower left, lower center, or lower right sides of the screen doesn't seem to do anything (even with key combinations of CTRL, ALT, SUPER and SHIFT). This was working before the upgrade from Ubuntu 12.04 by moving the mouse to the lower right corner of the screen it would show the notification area.

> **buzzingrobot said:**
> Minimized programs in Gnome Shell do not maintain icons in the Message Tray.  They don't maintain icons anywhere.  By default, clicking on the Dash icon of an app that is running opens that window, if it is minimized, and moves the focus of the display there.  Indicators and old-fashioned applets *do* put icons in the Message Tray.
This is actually incorrect, many torrent applications allow themselves to be minimized to this notification area along with at least a few other applications I've seen show up there when minimized (see image below).


> **buzzingrobot said:**
> Gnome Shell, in any version since the beginning, does not show the little purple icons that's in your image.
I've since discovered that this purple icon is the "Removable Devices" icon, and it has been on my Gnome3 desktop in the notification area ever since I installed Ubuntu 12.04. It may not be standard, but it feels standard to me since I can't remember where it came from, and I certainly don't remember installing it, and in fact I haven't had much use for it.


> **buzzingrobot said:**
> The Linux Mint team has removed most (all?) of Cinnamon's and Nemo's Gnome dependencies.  The flip side is that it might make it less compatible with Gnome Shell.
Yeah, gconf is not user friendly and I did screw up Nemo's ability to launch a terminal session from the right click menu on a currently active folder due to trying to get terminator to open at a predefined size via the default CTRL+ALT+T hotkeys, but thats just how Linux is if I want things to work the way I'm used to having them work, and I can't really complain any way because it's absolutely amazing that we have this stuff for free at all.


> **buzzingrobot said:**
> My suggestion -- you won't like it -- is to back out all the PPA's (install and use ppa-purge), comment out any non-Canonical source lines in /etc/apt/sources.list, and then do "apt-get update" and "apt-get upgrade".  If that works smoothly, and you have a standard functioning Gnome Shell, then uncomment non-Canonical lines in sources.list one at a time, and repeat the update/upgrade cycle until if/when you find something that breaks the display. When that happens, remove the culprit and the line in sources.list

Then, repeat that exercise with the previous PPA's. Doing all that will help identify the specific packages that cause the breakage you see. 

Yes, it's an arduous task, so it might be easier just to reinstall and go from there.
'Au contraire mon frere' pardon my french (I actually don't speak french at all) I enjoy these kinds of tedious tasks and would absolutely do this if there wasn't a better way, and in fact I still might do this just to clean up my system a bit any way.

> **buzzingrobot said:**
> (Also, note that PPA's are not always maintained and the packages on offer are not always available for the current Ubuntu releases. You would need to visit each PPA's launchpad.net page to check. If you used a PPA in 12.04 that replaced an important package, and the PPA did not make available the same package for 14.04, then an upgrade or dist-upgrade might have left your install relying on that outdated 12.04 package.)
Actually the synaptics package manager, and the default update manager in Ubuntu 14.04 have been really good at disabling PPA's that were not compatible with it and warning me about things that may have gotten me offtrack, and also note that I am taking what you are saying as really good advice and I might do a PPA purge and PPA re-add soon just to make sure I'm up to date on each of the PPA's that I do have installed.

As a final note, I did manage to fix the issue that the notification area was having without having to mess with the PPA's, although the solution is not satisfactory and might not help any one else looking here to solve a similar issue.
**_Problem re-described for clarity:_**
The entire notification area was not showing itself when the mouse was positioned at the bottom center of the screen (is this the default behavior?, on my 12.04 setup it was the lower right hand side). What was causing this problem has not been identified clearly. See below.

**_Solution:_**
After attempting to trigger the notification area by plugging in various stuff I had laying around, USB stick, Camera, mounting old hard drives, etc... non of this worked and just showed a relevant notification in the center bottom of the screen without showing the notification area. The description of how I got this to work is below the image below.

Shown here is an image of how the notification are should look when its maximized: 
(note this image has been cropped and edited to show the full desktop in a forum setting)
[IMG]http://imagizer.imageshack.us/v2/896x645q90/674/41d0c1.png[/IMG]
How I was able to get this notification area to show itself was by plugging in my Wacom tablet and after a few minutes I accidentally bumped the mouse towards the bottom of the screen and the notification area, as shown in the image above, had finally appeared. In retrospect this all started happening when I unplugged my Wacom tablet, however, unplugging the tablet did not allow me to reproduce the problem and so whatever caused this in the first place has not been definitively identified, but it seems like it might be an intermittent problem with the tablet... or something.

**_Last question remaining before closing this thread and marking it as solved:_**
What controls the notification area under Ubuntu 14.04, what the settings should be in gconf, and does the notification area have and use configuration files, if so is there a default file I can look at someplace? This question is here just to make sure I'm tying up any loose ends related to this issue. 

Please let me know if I'm forgetting to look into something or if I'm forgetting to try something.

---

### Post by buzzingrobot on 2014-07-20
I've used Gnome Shell extensively since the first version and don't recall ever see a Removable Device icon exposed by itself as shown in your image.

The behavior of the Message Tray has changed since the release of Gnome Shell, so the action to trigger its display may have been different in the version used in 12.04. A few extensions are available to tweak that.

Dunno if the Message Tray has a specific config file.  Gnome Shell's interface is built around CSS and javascript so I suspect its behavior is controlled there. A look through dconf-editor might find something, though.

---

### Post by landstander on 2014-07-20
I haven't found much useful in dconf or gconf when searching for the term "notification" because everything seems to be configured as it should be for it to work as it should. I also haven't found much yet searching on the web for how it is controlled and displayed by the OS yet but I'm still in the early stages of searching for that information.

**_Offtopic solution to a problem mentioned earlier:_**
I did however find a large clue to the issues of why Nemo (and probably also nautilus if I was still using it) does not open a terminal via the right click menu. It seems like Glib might have been updated to use the GIO (GAppInfo class) to open a terminal instead of gsettings (a.k.a. gconf editor settings). From information that is over a year old, what this would mean if its true, is that in order to use terminator as the default from right click menu's, Glib might need to be patched to include terminator as one of the few terminal applications it searches for. Here is a link to the source for this information: [https://bbs.archlinux.org/viewtopic.php?id=159139]("https://bbs.archlinux.org/viewtopic.php?id=159139")
The alternative to this is to use some other terminal program that Glib and GIO do search for, such as rxvt-unicode (a.k.a. urxvt) which can be configured to have transparency, and has a smaller resource footprint then terminator.

[UPDATE]: I have set urxvt as the default terminal emulator using (~/.Xdefaults) as its configuration file, and I now have a right click menu for accessing a terminal under Nemo that works.
I set urxvt as default using the compizconfig settings manager and navigating to --> Gnome Compatibility --> Commands --> Terminal Command Line --> Setting this to "urxvt".
As a reference, here it the code from my ~/.Xdefaults configuration file for urxvt:
```
/* This file was created for urxvt which is a terminal emulation program.
   Bellow is a list of settings for urxvt, for it's placement and color on screen.
   This file is used in Ubuntu 14.04, it should be named ".Xdefaults" and placed 
   in the home folder. */

URxvt*.depth: 32
URxvt.geometry: 157x86+0+0
URxvt.background: rgba:0000/0000/0000/dddd
URxvt.foreground: #91AB8C
```
This code produces a terminal with light green text on a true transparent background (where dddd represents how much transparency is being used).
For more information on how to use this program and the associated ~/.Xdefaults file see:
[https://wiki.archlinux.org/index.php/rxvt-unicode]("https://wiki.archlinux.org/index.php/rxvt-unicode")
and
[https://engineering.purdue.edu/ECN/Support/KB/Docs/UsingTheXdefaultsFil]("https://engineering.purdue.edu/ECN/Support/KB/Docs/UsingTheXdefaultsFil")

I'm going to go ahead and mark this thread as solved since no further information could be found on the notification area problem, and the problem appears to have resolved itself somehow.

---

### Post by nathan-linux-sa on 2014-11-01
Hi

I know this is solved, but I had the same problem. The solution is **SUPER+M**. This will allow you to see the notification area.

---

