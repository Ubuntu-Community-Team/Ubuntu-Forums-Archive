---
title: "help me fix my aptitude! (wants to uninstall critical packages)"
date: 2007-08-29
forum: General Help
---

### Post by MustNotSleep on 2007-08-29
bear with me now, i may have done something stupid..

it all started when i wanted to install Gnome Commander on my Feisty today (not really checking if i had it installed or not.. heh).. as i didn't find it in the repositories i have activated, i went to their official site and downloaded me their Ubuntu package.. i ran the installer with dpkg and it said it was missing some dependencies (newer and unstable versions of libart, libgcc, libc6, libpango, etc..).. so being the overly confident newb that i am, i proceeded to download these from Debian's package site.. and then i did [FONT="Courier New"]dpkg -i *.deb[/FONT] in the directory i downloaded them to..

when i saw that it complained about unfulfilled dependencies, even though they were in that same dir, i ran dpkg -i a couple more times.. nothing worked, and aptitude was already forcing me to do a sudo apt-get install -f to fix broken packages.. i do that, and you can see what it wanted to do:

[http://memmnoc.swifthost.net/temp/apt_screwup.txt](http://memmnoc.swifthost.net/temp/apt_screwup.txt) (sorry for the external link, it's 22kB in size and the forum's limit is 19.5kB)

needless to say, it ain't pretty.. it wants to remove my whole system!

so basically what can i do to override this, fix the broken packages without uninstalling everything and have my APT back?

thanks in advance!

(sorry for being a complete moron, i just saw Gnome Commander was already installed... :mad: serves me right...)

---

### Post by MustNotSleep on 2007-08-29
i think it's solved. thanks to aptitude (which i previously thought was the backbone to apt-get.. heh). seems to be a lot smarter than apt.

seriously, though, what's the point of having 4 different package management systems (dpkg, apt, Synaptic and aptitude)? this is the same thing that hosed my openSUSE installation a month ago (conflicts between YaST and ZMD.. arrghh).

so far, aptitude is by far the most capable of them all. instead of offering to *_remove_* my whole system (like Synaptic and apt did), it instead proceeded to simply downgrade those conflicting packages, snatching everything it needed from the active repos and cleaning up my system. why not simply make a GUI frontend for aptitude and call it a day? what's the reason apt is the most widely used and promoted Ubuntu PM?

sorry for the rant. i was just panicking in fear of losing my 3rd Ubuntu installation in the past month.

i'm now actively using sbackup, so i hope this sort of thing doesn't freak me out as much if it happens again. :D

---

### Post by ThrobbingBrain66 on 2007-08-29
Aptitude is "smarter" than apt-get, no doubt about that.  But on occasion I've run into troubles where aptitude also gets a little over-zealous and wants to remove all sorts of packages which would lead to even bigger problems.  I don't know if that's an official reason for not using aptitude as a backend, but that's my experience with it.

---

