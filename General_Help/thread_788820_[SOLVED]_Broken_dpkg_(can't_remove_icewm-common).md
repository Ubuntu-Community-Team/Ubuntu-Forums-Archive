---
title: "[SOLVED] Broken dpkg? (can't remove icewm-common)"
date: 2008-05-10
forum: General Help
---

### Post by johnraff on 2008-05-10
I want to clear out a lot of unused software before upgrading, and a couple of weeks ago removed icewm with Aptitude purge. However today I noticed icewm-common is still around and tried to remove it with Synaptic, but the system froze: full cpu activity, ram (128MB) and cache (256MB) both filled up and the hard disk thrashed on and on... Had to force a reboot with the SysRq key to get out.

Tried reinstalling it before removing, tried installing icewm again, tried using aptitude instead of synaptic - everything ends in the same frozen state while "setting up icewm-common" or the like. Worse still, the same now happens whenever I try to install or remove anything... :(

Can I just go in and delete all the files listed as belonging to icewm-common manually, or will that make things worse?

(I really don't want to do a system-upgrade while this isn't fixed.)

---

### Post by Xiong Chiamiov on 2008-05-10
Since aptitude freezes, what about
```

sudo apt-get autoremove

```
assuming that icewm-common is an orphaned package now.

---

### Post by Kevbert on 2008-05-10
You could also try the following:

```
sudo apt-get clean
sudo apt-get autoclean

```

[COLOR="Red"]**A more dangerous command. Use with care**[/COLOR]

```
sudo apt-get remove --purge icewm-common
```

---

### Post by johnraff on 2008-05-10
> **Xiong Chiamiov said:**
> Since aptitude freezes, what about
```

sudo apt-get autoremove

```
assuming that icewm-common is an orphaned package now.Well, there is an interesting error at the end of the output from that, so the orphans weren't removed - fortunately as it happens as some of them (I realized after hitting "enter") were actually needed by apps I'd compiled and installed with checkinstall:
```
john@raffles2:~$ sudo apt-get autoremove
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-musicbrainz2 python-gst0.10 linux-headers-2.6.20-15-generic
  libdiscid0 dict python-ctypes recode libiso9660-4 linux-headers-2.6.20-15
  icewm-common gstreamer0.10-gnomevfs
The following packages will be REMOVED
  dict gstreamer0.10-gnomevfs icewm-common libdiscid0 libiso9660-4
  linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic python-ctypes
  python-gst0.10 python-musicbrainz2 recode
0 upgraded, 0 newly installed, 11 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not open file /var/lib/apt/lists/debian.linux.org.tw_ubuntu_dists_feisty_main_i18n_Translation-en%5fGB - open (2 No such file or directory)
john@raffles2:~$ 
```Anyway I don't know if that error gives a clue?

---

### Post by johnraff on 2008-05-10
> **Kevbert said:**
> You could also try the following:

```
sudo apt-get clean
sudo apt-get autoclean

```This seemed to go, but after running it```
aptitude show icewm-common
```said its state was "partially configured", which doesn't sound good.> [COLOR="Red"]**A more dangerous command. Use with care**[/COLOR]

```
sudo apt-get remove --purge icewm-common
```Why is that dangerous? Doesn't it just mean remove that package along with its configuration data? And in what way should it be used with care? 
However, I'm very afraid if I run it dpkg (or apt?) will go into that hard-disk-thrashing freeze state again, so I'll post this first, as it's 2AM and I don't have time to shutdown, reboot... 

If you don't hear from me for a day or two fear the worst... :)

---

### Post by Kevbert on 2008-05-10
Dangerous command is remove or rm. If you type in the wrong thing by accident you could damage you (software) system.  If you look around the forum there are warnings about using rm or remove especially with wildcards (*, I'm not sure about ?, it may just be a windows thing).
If these don't work (especially with purge) I don't know how to sort you're problem.

> Could not open file /var/lib/apt/lists/debian.linux.org.tw_ubuntu_dists_feisty_main_i18n_Translation-en%5fGB - open (2 No such file or directory)
A feisty fawn directory has somehow been manually deleted (rather than an uninstall, which was expected).

Best of luck.

---

### Post by johnraff on 2008-05-10
I'm afraid the purge command went into freeze again.

As soon as it got to "removing icewm-common" the hard disk started thrashing, RAM usage started to climb, the cache started to fill up and after about a minute tne keyboard and mouse were being ignored and I had to hit the power switch to get out. (Yesterday, if I just left it to its own devices, after 40 min or so the X server crashed, or something timed out, and it dropped back to the login screen.)

I don't know if this might be relevant, but just before all this started I had some trouble with mplayer and had to reboot and do a file system check. fsck found a lot of bad stuff to remove, and after it was done I had to reinstall a couple of libaries to get mplayer working again. 
Could it be that something else important was lost at that time?

Any suggestions on how to get dpkg/apt back to its normal state would be much appreciated. :)

---

### Post by Kevbert on 2008-05-11
You'll probably need to check all your system logfiles.  These can be found in /var/log.  I'm not really conversant with these.  You may need to repost, if you find any problems.
Sorry I can't help with these.

---

### Post by Kevbert on 2008-05-11
Maybe this might work to fix damaged packages:

```
sudo apt-get install -f

```

Then try uninstalling.

---

### Post by johnraff on 2008-05-13
Kevbert, thanks for your suggestions.
I've looked around /var/log and found these lines st the end of dpkg.log```
2008-05-13 12:53:27 remove icewm-common 1.2.30-1ubuntu1 1.2.30-1ubuntu1
2008-05-13 12:53:27 status half-configured icewm-common 1.2.30-1ubuntu1
2008-05-13 13:52:46 status half-configured icewm-common 1.2.30-1ubuntu1
```If I run ```
sudo dpkg --configure -a
```it finishes without any error messages, but```
sudo dpkg -C
```shows icewm-common as half configured:```
john@raffles2:~$ sudo dpkg --configure -a
Password:
john@raffles2:~$ sudo dpkg -C
The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 icewm-common         wonderful Win95-OS/2-Motif-like window manager
```Running the suggested commands makes the machine freeze up as before. Likewise, if I run```
sudo apt-get install -f
```it gets to a line that says "configuring icewm-common" and then goes into that same freeze state.

Here's the entry in /var/lib/dpkg/status about icewm-common:```
Package: icewm-common
Status: purge ok half-configured
Priority: optional
Section: x11
Installed-Size: 2572
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: icewm
Version: 1.2.30-1ubuntu1
Config-Version: 1.2.30-1ubuntu1
Replaces: icewm (<< 1.2.14)
Recommends: menu
Suggests: icewm-themes, icepref, iceme, grun, xlockmore
Conflicts: menu (<< 2.1.9-1)
Conffiles:
 /etc/X11/icewm/toolbar 767f5e1ed3f3021346296c43bbb746c2
 /etc/X11/icewm/menu dc6424aa3d65de9068360601fcfd70e2
 /etc/menu-methods/icewm-common 4c751332b4fad1f4889a247418bfdd65
Description: wonderful Win95-OS/2-Motif-like window manager
 IceWm is a Window Manager for X Window System. Can emulate the look of
 Windows'95, OS/2 Warp 3,4, Motif. Tries to take the best features of the above
 systems.
 Features multiple workspaces, opaque move/resize, task bar, window list,
 mailbox status, digital clock. Fast and small.
 .
 This package provides the common files for icewm, icewm-experimental and
 icewm-lite binary packages.
Original-Maintainer: Eduard Bloch <blade@debian.org>
```

I just want to get the **** thing off my computer!!
I was hoping to do a system-upgrade some time soon, but if this isn't fixed first it'll probably pull the same freeze in the middle of the upgrade process... :(

---

### Post by Kevbert on 2008-05-13
Do you get problems with the PC freezing when running other programs (not installing) ?  If so, you may have an overheating problem.  It might be worth running the memory checker (available on start-up) for a while.
I've had a look on launchpad and there's only one bug on there which freezing occurs with icewm-common - see [https://bugs.launchpad.net/ubuntu/+bug/155003]("https://bugs.launchpad.net/ubuntu/+bug/155003").  It might be worth raising a bug report (with as much info as possible).  Let the experts have a go at resolving the problem.
The only other way I can see you'll get rid of this is to do something drastic and re-install the OS.
Are you using Fluxbox instead of icewm ?
This problem must be solvable!!!

---

### Post by johnraff on 2008-05-13
Hi Kevbert, thanks for sticking with this!> **Kevbert said:**
> Do you get problems with the PC freezing when running other programs (not installing) ?I've never had freezing while installing/uninstalling before. Swiftweasel (kind of Firefox) often freezes with sites using Flash, but it's only that program - xkill will get it - and that seems to be a fairly common issue. I do sometimes get freezing while logging in; I put that down to some gdm bugginess, and a restart fixes it.> If so, you may have an overheating problem.Hmm... don't want to rule anything out, but it *feels* different: activity gradually builds up - cpu, ram and cache usage climb up over 15 seconds or so, at which point the system is unresponsive. (The [SysRq key stuff](http://ubuntuforums.org/showthread.php?t=617349) does work though.) So it looks as if some kind of endless task is being run through over and over...> It might be worth running the **memory checker** (available on start-up) for a while.Aah... I'd like to try that- how do you do it?
> Are you using Fluxbox instead of icewm ?Right now I'm using Xubuntu. I only tried icewm briefly in the search for something lighter (I've only got 128MB of RAM) but now I think eventually I'll move to Openbox.> The only other way I can see you'll get rid of this is to do something drastic and re-install the OS.Yes, that's an option. I've system-upgraded this box step by step from Breezy to Feisty, so a clean install of Gutsy or eventually Hardy would probably get rid of a lot of messy stuff. It would be a lot of work getting the software and settings back though, and it seems so... *windozeish*...

I think now I'll try and understand the dpkg manual a bit better, then scour the net for some tutorials.

If nothing comes up I might just delete (or rename) the files listed by synaptic as belonging to icewm-common, edit the */var/lib/dpkg/status* file's entry for icewm-common to not-installed, then see what happens...

> This problem must be solvable!!!

exactly! :)

---

### Post by Kevbert on 2008-05-14
Hi again.
Yes, Firefox is a problem for me.  I tried FF 3b5 when I installed Hardy and had the PC freeze solid as soon as I browsed anything with flash.  That's why I now have Gutsy again and FF 2.0.0.14.
The memory check is menu option when you boot-up (a Grub menu item).  I'm not clued up on Feisty having been recently converted from Windows.  If you don't get this menu item then an easy way is to get hold of a Gutsy Live CD, or a Hardy  one (from [https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")) and use that. Unfortunately Shipit only seem to send out Heron CDs now.  How to get Gutsy CDs seem to be a bit of a problem, you may have to buy one locally.  Personally I don't think you've got a memory problem.  When you first turn on the PC, the computer runs a power on self test (POST) which performs a very basic memory test (but of course the PC is cold and therefore memory faults are less likely to show up). 
I wouldn't touch Hardy at present until it's a little more stable,  somethings are an improvement on Gutsy, some are not.
Good luck.

---

### Post by johnraff on 2008-05-15
Yay!!! Finally fixed it.:)
man dpkg and Google weren't very much help, but the person in [this thread](http://ubuntuforums.org/showthread.php?t=70441) had a similar problem, and solved it by deleting all the files, so I ignored the Dire Warnings I'd seen, bit the bullet and had a go:

*Got a list of all the files installed by icewm-common from Synaptic (the list's in /var/lib/dpkg/info/icewm-common.list too) and renamed them to *whatever*-disabled.

*Opened /var/lib/dpkg/status, found the bit referring to icewm-common and changed it (using the entry for icewm as a guide) to:```
Package: icewm-common
Status: purge ok not-installed
Priority: optional
Section: x11
```
This seemed to fix it! All the error messages went away, and I'm able to use Synaptic, apt-get and dpkg as normal. :)

*For good measure I also renamed all the icewm-common related files in /var/lib/dpkg/info

If no problems turn up in the next couple of days I'll delete all those files and mark the thread "solved". Thanks for your help and encouragement, Kevbert.

> **Kevbert said:**
> Firefox is a problem for me.  I tried FF 3b5 when I installed Hardy and had the PC freeze solid as soon as I browsed anything with flash.  That's why I now have Gutsy again and FF 2.0.0.14.You might want a look at [this thread](http://ubuntuforums.org/showthread.php?t=766683) if you haven't already.> The memory check is menu option when you boot-up (a Grub menu item).aah, yes - now I remember seeing it flash by.Thanks> Shipit only seem to send out Heron CDs now.  How to get Gutsy CDs seem to be a bit of a problemWhat I'll probably use if I do a clean install is [unetbootin](http://ubuntuforums.org/showthread.php?t=427540) which does it all online without a CD.> I wouldn't touch Hardy at present until it's a little more stableThat's how I feel. Maybe I'm now ready to upgrade to Gutsy! Feisty/Xubuntu has been quite good on the whole really, but software is starting to come out that needs Gutsy...

---

### Post by Kevbert on 2008-05-15
Congratulations.  This should be filed somewhere useful as I'm sure others will come across the same sort of problem.

---

### Post by johnraff on 2008-05-22
Well, no issues seem to have come up so I've marked this as "solved".
Now to delete all those renamed files.

As to publishing this "solution" more than just having it here on the forum, I'm not sure...

1) I still don't really know what the problem was, just how to "fix" it.

2) I'm not sure if it's such a good idea to encourage people to go in with *sudo* and delete files, at least not without a lot of thought and research first.

 Anyway, cheers! :)

---

