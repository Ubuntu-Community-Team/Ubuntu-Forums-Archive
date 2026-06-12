---
title: "New to Ubuntu"
date: 2007-12-22
forum: General Help
---

### Post by mrbubbles on 2007-12-22
Hi everyone!  I'm COMPLETELY new to linux, let alone ubuntu.  I've just gotten it working on an alternate HDD, so it's not on a partition on the HDD with windows.

I was wondering if anyone has a recommendation for which version of ubuntu (or any other distro, for that matter) would be good for getting used to linux.  i'm used to windows xp and i need something that'll do most basic tasks that i can in windows, and i'd even like to see if my wife can play sims 2 through linux :).

anyway, my hardware specs are:
2.8ghz celeron
10gb hdd (for linux, the one for windows is a 320gb)
512mb ram
XFX nVidia geForce 5200 (128mb)

currently, i have kubuntu installed (and i think it looks spiffy, but it'll take a while to get used to navigating it), but i've also downloaded/burned ubuntu 7.10 desktop, ubuntu 7.10 server, xubuntu 7.10, and freespire 2.0.8.

any help would be great.  Thanks!

:guitar:

---

### Post by cyrusrayne on 2007-12-22
For getting the basics down, I'd recommend either Kubuntu or Ubuntu given the specs, though other distros I find very good are openSUSE, Fedora and Damn Small Linux, though ultimately it's a matter of preference.

For running The Sims, it should run reasonably well under wine, you can find info on it and most other windows apps at [http://appdb.winehq.org/](http://appdb.winehq.org/)

Best of luck with Linux and welcome :)

---

### Post by TidusBlade on 2007-12-22
For new distros, you might wanna try PClinuxOS and SimplyMEPIS, Ubuntu and Kubuntu etc. are also really great for starting out, since they work straight out of the box. If you still need to use XP for some reason for some task or something, might wanna find a linux alternative, there usually is, or use WINE to run it under Linux, or Virtualbox to even run Windows XP, fully functional under Linux ;)
Sims can be run under WINE, Cedega if you pay up, and VirtualBox, not sure about VirtualBox though...

---

### Post by Wiebelhaus on 2007-12-22
[Mint ]("http://linuxmint.com/")will take care of the things noobs are worried about.

---

### Post by davidgarcin on 2007-12-22
I'd say you're off to a good start.  Kubuntu is based on the KDE desktop instead of the GNOME desktop like normal ubuntu.  Many people consider KDE to be closer to a Windows environment than GNOME is, and thus easier for a beginner.  That said, I do prefer GNOME over KDE.  It's really a matter of what you get used to.

I would not recommend ubuntu server, because it has a lot of features that you, as a beginner, will never use.  xubuntu is ubuntu with a stripped down graphical environment that is mostly meant for low-end machines.  You do have a decently fast machine, so you shouldn't have to settle for xubuntu.

I've never used freespire, but if you've already got kubuntu installed and running, I don't see much point in switching.  (k)ubuntu is a very user-friendly distro that takes care of a lot of things that beginners find difficult (codec installation, networking, etc).

So I guess my advice to you is to stick with what you've got.  As for playing Sims2, you will most likely need to look into a program called wine, which implements the Windows APIs on top of linux so that you can run Windows apps.  That's a whole different topic that someone more knowledgeabe can help you with when the time comes.  There are plenty of wine users in this forum.

-David

---

### Post by mrbubbles on 2007-12-22
Thanks guys, you've all been great.  I think I'll stick with Kubuntu for now and see what I can figure out :)

While I was waiting for replies, I tried to download the nVidia driver for my card.  I'm not sure if it's fully supported right now or not... but anyway, i found the right driver and i tried installing it using kate, running it as root.  

a little window popped up and asked for a password, so i typed in my password for logging onto kubuntu.  now when i try to run the silly installer, it comes up with an error message that says "Command not found!"  and then closes.  any ideas?

thanks!

---

### Post by mrbubbles on 2007-12-22
Oh, what's mint?

---

### Post by TidusBlade on 2007-12-22
Mint, a linux distro :p 
You can check [DistroWatch](http://distrowatch.com/) for info on almost every single Linux distro ;) And [here's](http://distrowatch.com/table.php?distribution=mint) the Mint page.
For the nVidia thing, why not try using the Restricted Drivers Manager? It's in K menu> System Settings> Advanced> Restricted Drivers Manager.

---

### Post by mrbubbles on 2007-12-22
okay, so i've added the wine apt thingy (still have NO idea what i'm doing :)) and followed the directions on the winehq website, but it's still not working.  it's trying to set up a fake windows drive, but ended up in an error.  it said the two possible causes are...
-An error occurred during your last kde upgrade leaving an orphaned control module
-you have old third party modules lying around

any ideas?

---

### Post by mrbubbles on 2007-12-22
okay, i think i've got wine working.  i'm trying to find the sims folder that's been installed on the other hdd, but kubuntu won't get into the other hdd.  is there a way that wine can load the program from program files in windows?

thanks guys

---

### Post by TidusBlade on 2007-12-22
I am pretty sure that WINE can load files from Program Files there, just make sure that you can read it. Or even better, use ntfs-3g or AKA NTFS Configuration tool from the repos to make the NTFS partition writeable, so you could save games and such.

---

