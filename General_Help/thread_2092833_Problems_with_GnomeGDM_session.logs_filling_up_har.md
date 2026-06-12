---
title: "Problems with Gnome/GDM session.logs filling up hard drive"
date: 2012-12-09
forum: General Help
---

### Post by number six on 2012-12-09
OK I've been having this crazy problem.

It started about a month ago. I kept running into low disk space on my Ubuntu 11.04 install (was avoiding newer versions because i hate unity). There was no reason for it, the Ubuntu partition was 30gb and it's a file server that doesn't get used for much other than files. 9 times out of 10 a reboot would free up the space.

This was a Wubi install under WIndows XP. I figured the Wubi aspect was causing problems and I never use XP so I just did a re-install of a full-on 11.04 figuring it would be better in the long run. 

Within 2 days the 11.04 fresh install starts doing the same thing. OK fine, upgrade to the latest/greatest 12.10 as it seems there are ways to avoid Unity (yay!) and certainly that will fix the problem. Nope.. once again, it starts happening again.

This time i actually looked into what was causing the problem. .cache/gdm/session.log is ballooning up to fill the entire partition. The full partition is 80gb so it needs to get to about 74gb before it crashes it, but it's done this repeatedly.

Doesn't seem to be doing it incrementally either.. it's just like something snaps it and it blows up randomly (but frequently.. ). When the file system fills up it crashes VNC and other things making my file server basically useless.

Crazy thing is i have nothing installed right now. Total fresh copy of 12.10. The only installed apps are Gnome and X-Chat. That's it.

Any ideas? Ubuntu has been rock solid for me for years but this is killing me. It's gotta be some bug because it's followed me from a complete fresh re-install and even an upgrade. Is there anyway to just disable the creation of the session.log files completely? I really don't care about the logs. Security isn't a concern where this file server is.

---

### Post by DDRFreak21 on 2012-12-14
Bump. I'm having the same issue and would appreciate some help.

---

### Post by Mopar1973Man on 2012-12-14
You could install Bleachbit and do some clean up of logs and such with it.
[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by mcduck on 2012-12-14
If the logs are filling your drive, the best bet is pretty much always to open the log file in question, take a look at what's causing all the error messages, and solve the actual problem...

---

### Post by EthanFHarris on 2013-01-26
Bump ~ similar problem with 12.10 64-bit but where the GDM cache suddenly fills the entire SSD boot drive.  "gdm-restart" will usually clear the GDM cache.  The GDM restart however causes the system lose HDMI Audio output!  Asus Maximus V Extreme motherboard, Nvidia 610 graphics card.  Same thing also happens on the motherboard's Intel based HDMI, where the boot drive is suddenly completely full with GDM cache.  Gotta be a bug and not a config issue.

---

### Post by ljochemczyk on 2013-05-27
I have similar problem. "gdm" file in "Cache" folder gets bigger and bigger until it fills up the entire disk - over 70 GB.

---

### Post by ljochemczyk on 2013-05-27
It seems that I solved my problem. Perhaps it can help other who had similar problems. 
First I launched "System monitor" and found out that my processor is mostly occupied by a script that I receantly added to the *Startup applications. *Script was supposed to rotate my ThinkPad screen automatically whenever I change the position of the screen. I used the script from this thread: [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830) from the section ***_[SIZE=3]Method 2[/SIZE]_**:  **Tablet PC Automatic Rotation** Script*.
After I got rid of the script everything seems to be ok :-)

---

