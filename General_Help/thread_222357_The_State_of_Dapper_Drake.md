---
title: "The State of Dapper Drake?"
date: 2006-07-24
forum: General Help
---

### Post by Donshyoku on 2006-07-24
This is mostly for me, but I think it could address a lot of concerns for other users.  So, if you want to, chip in!

I ran Dapper Drake from January until May, but dropped it in May until it became stable.  I downloaded the final and got it up to date, but found a lot of the same problems persisted.  I forgave it as a beta product, but once it hit final, I considered these problems a big issue.

I had problems with Totem Movie Player.  It would crash immediately upon opening, so could only be accessed whilst playing a video.  Also, it had problems playing Quicktime videos as the color scheme would alter itself to really bright with high contrast, making trailers unwatchable in my terms.  I do choose to use this player, and didn't want to resort to another player to fix these problems when I wanted to be satisfied by the default.  How is Totem these days?

Flash video, or rather, sound was a big problem.  I tried the mozilla-flashplayer packages and the flash-nonfree packages, but both caused randomly for the sound to drop.  Sometimes it wouldn't work at all (fixed by a reboot) and sometimes it would die in the middle of playback (also fixed by reboot).  Is Flash much improved? (BTW, Adobe is releasing Flash 9 for Linux, just not on a timely fashion... good news regardless!)

Finally, I had issues with the Gnome wireless/networking manager.  I visit friends, school, and my own home (odd phrasing, forgive me...) so create multiple profiles to use at each house as everyone is using some sort of encryption.  Creating a profile is fine, but once my computer is set on one, it takes a few minutes (literally) to load the next.  If I want to hop on to check my mail at school, a 30-second venture becomes a 3 minute and 30 second venture.  It is not enticing when other operating systems around me are in and out before I have switched to the new profile.

WPA encrytpion was a problem.  WPA-PSK is used in my home, and I cannot connect wirelessly to the network at home unless I modified config files.  By no respect am I shy with text or the terminal, but I could never get it working to a good degree.

Alas, I tried SUSE 10.1 and Fedora Core 5 distros but found them lacking.  Hardware support wasn't good (no audio buttons in either distro) and I was even required to install drivers for my populaer IPW2200 wireless chipset.  I've been on Windows for a while and have it working fairly well, but am really missing the speed, programs, and consistency I experienced (to some degree) with Ubuntu.  

So, have my problems been cured via updates?  Are there better or known workaroundst these days?  Do they still persist?  Is this post waaaaay too long?

These questions and more will be answered in the following replies (or so I hope!).

Thanks, everyone!

---

### Post by reacocard on 2006-07-24
I have never had any trouble with totem in Dapper.

There's a [workaround]("http://ubuntuforums.org/showthread.php?t=186594") for the firefox flash sound problem in the HOWTO section on these forums.

I use Network Manager to manage my wireless. It works flawlessly, even with WPA (you'll need wpasupplicant to enable it). I also have the intel 2200 wireless.

Hope this helps!

---

### Post by Sef on 2006-07-24
What is your hardware?  Some of the problems could be hardware related.  Best if you just installed it and posted any problems that you were still having.

For sound on Flash, you need to download alsa-oss.

Open the Terminal

sudo apt-get update

sudo aptitude install alsa-oss

---

### Post by Donshyoku on 2006-07-24
Yes, dist-upgrading is easy, but for time's sake... is there an updated ISO I can download?  One that has patches up to today or more recently than the final release two months ago?

---

### Post by reacocard on 2006-07-24
unfortunatly not. i installed ubuntu onto another computer the other day and had to wait 2 hours while the 230MB of updates downloaded and installed. that's four times longer than it took to install ubuntu itself. :sad:

---

### Post by Donshyoku on 2006-07-24
The disc I have is a RC1, but is close enough to final, I suppose...

I just heard that wonderful drumbeat, so I am going to dist-upgrade and theme a little bit before examining or addressing any problems.  

I'll post back here if I need help if only for consistency's sake.  No one wants 4 or 5 threads by me (and I am hoping it doesn't come to that!).

Thanks, again.

---

### Post by MarinaraOfDeath on 2006-07-24
I assume you're using totem and not totem-xine? I started out form Kubuntu, and I too had that problem with totem until I thoroughly ripped out all the multimedia crap that comes with ```
apt-get install ubuntu-desktop
``` (including the version of totem linked to gstreamer, which Just. Doesn't. Work right. Seriously, google it...). I then reinstalled the various programs I actually wanted, including totem-xine. Works much better for most things, and in particular it would handle the trailer to Superman, an m4v that either choked the other players or was badly washed out. I still occasionally get the unwatchable washed-out effect, but restarting X ```
Ctrl+Alt+Backspace
``` fixes that.

As to the larger part, issues I've seen are updating the kernel without asking me, problems matching the current version of Lyx when updating, not necessarily installed the restricted packages even though the meta package has been installed from day one, occasional problems with this or that service not hibernating properly, and being unable to see my 4-in-1 card reader, and the two-day epic struggle to do away with the impressively resilient yet truly shitty spatial browsing mode in nautilus (the instance of nautilus used for the Places menu in Gnome ignores the preferences you set, so you have to figure out which things to set in gconf-editor, which would have been very intimidating if I wasn't an old hand at windows registry hacking/tweaking). Plusses are Automatix, which is an unparalled ease-of-installation utility, amazing support on the boards, and a number of packages that I feel are superior to their Windows/OS X counterparts (amaroK, Firefox except for flash 8, fish terminal instead of DOS box, konqueror file management/browsing combination, both winefish and bluefish, kate's syntax highlighting, and the Alacarte menu editor.

As you can guess, I am not your standard windows user, so I really like Ubuntu. If we had proper ActiveX support/emulation (maybe through wine in the future?), currrent versions of flash, and an end to the perennial wireless and monitor configuration issues (automatic -- ***and correct!***-- configuration of projector or second monitor) that plague all linux distributions, I'd have essentially nothing at all to boot into Windows for.

---

### Post by Donshyoku on 2006-07-24
I was actually using totem-xine as it supports a lot of the codecs that I seek out.  It is too hard to live on Linux with no proprietary codecs thanks to the Internet.

Perhaps for troubleshootings state, I will launch totem-gstreamer and see if it crashes.  Grab totem-xine and see if it does.  Trial and error isn't bad.

BTW, does gstreamer support many new formats now?  DVD?  MOV, WMV, DIVX, M4V?

---

### Post by reacocard on 2006-07-25
> automatic -- and correct!-- configuration of projector or second monitor)

how? i'd love to have that.

as far as i know, gstreamer supports pretty much everything xine does, except dvd. gstreamer can't handle dvd menus, but xine can.

---

### Post by zxee on 2006-07-25
Having used this distro since hoary I am a big fan of Ubuntu and have used plenty of other distros so have a basis for that. However dapper was horrid-it isn't simply a hardware issue because networking and internet works great again in edgy-but it never did in dapper. I mean that although I could get internet connection in dapper it was slow inconsistant and just plain buggy. None of that is true with edgy.

---

### Post by Donshyoku on 2006-07-25
I am glad to have a good report!

Totem-gstreamer is working great.  It plays all my formats (that I have tried) and doesn't crash.  I guess that must have been an xine-backend problem.  Regardless, it is fixed.

I've got the flash-nonfree plug-in installed and working.  I haven't come across any audio in Flash yet, but I'm going to visit YouTube and check out a few videos.  Hopefully, that will work.

Network Manager has WPA support now that works great.  It is a lot better than the Windows utility as it shows you your signal strength from the icon in the tray.  Good for a quick look and it seems really stable (Windows would disconnect me occasionally and I would have to reset my hardware switch, reconnect).

Good news!

---

### Post by mattkenn4545 on 2006-07-25
Just so you know there is a way to user totem-gsteamer with the w32codecs it is a gstreamer plugin with a name something like pitfall

(sorry at work and had to use windows for a month (darn school))

---

### Post by bastubis on 2006-07-25
Positive stuff first - Dapper looks great, VGA resolution much better, nice. Love the Avahi implementation (as a windoze refugee it makes my life complete). I don't find Dapper slow, if anything it's more streamlined. 

Bad stuff - Dapper seems to have some kind of pervasive hardware problem. All of the stuff listed below was working fine in Breezy but is broken in Dapper: 

1. Creative SBLive card listed correctly in pci, alsa-base, xine, gstreamer, sound plugins and codecs etc seem installed fine, sound is turned on in mixer, but no sound - not even a system beep - and no player will play any music format.  

2. Electricsheep broken, can't figure this one out either. ATI Rage 128 seems to be working fine, have done any tweak I can find in any forum but it's seriously dead. Some people say it'll work with mplayer running - if only I could get *any* player running, I'd test this :-?  OK it's trivial but I love electricsheep :-(

3. Power saving doesn't suspend the screen - I've tried various settings, including "never" but it just ignores me. 

4. The upgrade shredded my existing installation, had to start again and do a clean install. 

5. Rhythmbox crashed so many times whilst I tried to load and navigate a music library it's really unuseable. All other players behave sensibly except for the sound problem. 

Dapper seems generally very very very buggy around hardware - otherwise Dapper is great.

---

### Post by MarinaraOfDeath on 2006-07-26
reacocard, 

That was kinda the point. It doesn't "just work", and it damn well should to be useful to anyone other than people geekier than I (and the geek is strong with this one).

---

### Post by reacocard on 2006-07-26
MarinaraOfDeath, just reread your post. i thought you said you had that. :oops: The way i understand it, the current Xserver is too inflexible to allow this. it's being worked on though. maybe in a year or two.

---

