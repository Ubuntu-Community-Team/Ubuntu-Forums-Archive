---
title: "xscreensaver customization not persisting after shutdown/reboot"
date: 2014-01-19
forum: General Help
---

### Post by EnglishElectricAndy on 2014-01-19
In 13.04 I was able to work out how to configure my screensaver to pull photos from a particular sub-directory and run a selection of these if the computer was idle for a while. these settings remained persistent even when I shut down and later rebooted.

I've recently upgraded to 13.10 (using the 'Upgrade' option in a live USB session) and have noticed that the screensaver reverts to its default blank screen after a reboot instead of running a photo sequence from my selected sub-directory.

I have looked into the GUI for the screensaver and everything that seems like it needs to be checked or unchecked is OK. 

Is there a (hopefully fairly simple) command for the terminal that I can use to make my customization persist beyond a shutdown? The directory path, if that is the right terminology, is /Home/Pictures/Cornwall 2013/ .

---

### Post by ajgreeny on 2014-01-19
> The directory path, if that is the right terminology, is /Home/Pictures/Cornwall 2013/ . 						If that really is the path to the pictures it could be the reason for your problem, as I think you need a folder in your own home, ie /home/*username*/Pictures/Cornwall2013/ and not another /home folder.  Perhaps that is a minor error in the way you have written the pathway.

Can you also check that the hidden .xscreensaver file in your home is owned by you, by running ```
ls -la .xscreensaver
``` which should show output something like ```
-rw-rw-r-- 1 *username username* 7657 Jan 12 22:52 .xscreensaver
```

---

### Post by EnglishElectricAndy on 2014-01-19
@ajgreeny, the newbie in me realised a bit later that I hadn't included my username in the path.

Here is the output from the command (hopefully in a code box, if I've clicked the correct icon)

```
tulyar@Sony-VGN-NR32L-S:~$ ls -la .xscreensaver
-rw-r--r-- 1 tulyar tulyar 7683 Jan 19 19:30 .xscreensaver

```

Supplementary: the noob in me is probably barking up the wrong tree at the wrong cat, but I'm tentatively guessing that output is referring to different levels of  permissions.

---

### Post by ajgreeny on 2014-01-20
Your permissions are absolutely correct so I honestly don't know why your screensaver configuration will not stick as you want it.  Sorry about that.

Just a quick thought, however.

Try renaming the **Cornwall 2013** folder to Cornwall2013, ie no space, reset the configs to take account of the new name, and see if that makes any difference; I don't see why it should but I'm grasping at straws here.  I don't use spaces in file and folder names if I can avoid it as it makes typed pathways so much easier to deal with.

PS: have you set the GUI of xscreensaver to "Use only one screensaver" at top left of the GUI dialog.

---

### Post by Peter Maunder on 2014-01-20
a very quick thought. Did the upgrade re-install Gnome-Screensaver? This would just blank the screen rather than run Xscreensaver. Hence any changes to Xscreensaver settings would not persist after shutdown.

---

### Post by EnglishElectricAndy on 2014-01-20
@ajgreeny, thanks for your assistance. 

I confirm that I have only 1 screensaver option active, this being OpenGL Slideshow. In the 'Advanced' settings my desired sub-directory is active, the other options available in this window are unchecked.  Somewhat confusingly, the Preview option in the GUI window starts running, and displaying photos from the selected sub-directory without any intervention or fiddling on my part.

I briefly wondered if I'd missed an update somewhere```
:tulyar@Sony-VGN-NR32L-S:~$ apt-cache policy xscreensaver
xscreensaver:
  Installed: 5.15-3ubuntu1
  Candidate: 5.15-3ubuntu1
  Version table:
 *** 5.15-3ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status


```

Looks coherent to me.

@Peter Maunder, thanks for your contribution. I upgraded from a live USB session so I didn't knowingly install or re-install anything that I didn't have in my 13.04 set-up, but just for confirmation:
```
tulyar@Sony-VGN-NR32L-S:~$ apt-cache policy gnome-screensaver
gnome-screensaver:
  Installed: (none)
  Candidate: 3.6.1-0ubuntu7
  Version table:
     3.6.1-0ubuntu7 0
        500 http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/main amd64 Packages
     3.6.1-0ubuntu6 0
        500 http://gb.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
tulyar@Sony-VGN-NR32L-S:~$ 

```

It seems very odd that a function which worked faultlessly in 13.04 seems to be causing unexpected difficulties in 13.10. At the moment I'm reluctant to go down the route of filing a bug because I have no evidence that issue affects other users, it may well turn out to be something in my personal configuration as I'm only just over six months into my Windows detox!

---

### Post by EnglishElectricAndy on 2014-01-22
This is proving a ticklish little issue to track down a solution for.

Steps taken so far;
- browsing the Web. Didn't return anything specifically useful, a lot of stuff about multi-monitor and server environments, not applicable to my case. Also some entries referencing full-flavour Ubuntu versions from '08 and '09, again not applicable.
- looked into the man pages for xscreensaver. Noticeably, the developer is keen on the GUI being used for the purposes of managing the app. Other than that, there's a lot that is way above my current paygrade.
- revisited the GUI, hovered the pointer over '_F_ile', clicked on 'Restart Daemon' and rebooted. This had the side-effect of deleting my personalized Desktop wallpaper. Reinstalled this with Settings manager and rebooted. Wallpaper persists, deliberately wait the alloted 10mins for xscreensaver to liven up to see if the desired slideshow starts. Nope, no-go, the BSoND (Black Screen of Near Death) reappears.

Steps I am considering;
- purge and reinstall xscreensaver. Before doing this I'll look into the 'apt-cache depends' and 'apt-cache rdepends' just to see if this gives a newbie some hints about what breakages I might cause myself.
- even more drastically, go for a clean install of 13.10. I'd rather not do this as the whole reason for upgrading via a live session was to avoid having to manually install heaps of data that already exists and largely successfully ported across from 13.04.

---

### Post by EnglishElectricAndy on 2014-01-22
```
tulyar@Sony-VGN-NR32L-S:~$ apt-cache depends xscreensaver
```

>snip<
```
  Conflicts: funny-manpages
  Conflicts: <funny-manpages:i386>
  Conflicts: gnome-control-center
  Conflicts: gnome-control-center:i386
  Conflicts: <suidmanager>
  Conflicts: <suidmanager:i386>
  Conflicts: <xscreensaver-gnome>
  Conflicts: <xscreensaver-gnome:i386>
  Conflicts: <xscreensaver-nognome>
  Conflicts: <xscreensaver-nognome:i386>
  Conflicts: xscreensaver:i386
tulyar@Sony-VGN-NR32L-S:~$ 
```

Not too sure where to go from here, can I safely purge these conflicting items?  'gnome-control-center' in particular reads like it might be something fundamental.

Am I correct in reading the above as including some 32bit packages?  If so, I have no idea where they came from as I run 64bit architecture exclusively since migrating to Xubuntu.

---

