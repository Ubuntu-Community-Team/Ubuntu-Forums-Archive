---
title: "GNOME freezing completely, cannot figure out how to fix"
date: 2016-01-10
forum: General Help
---

### Post by bvargo on 2016-01-10
I posted this in the desktop environments forum but received no responses and still haven't been able to figure it out so I thought I'd ask here.  Help is appreciated.

Until about a week ago, I was running 12.04 LTS w/GNOME classic and  had no practical issues.  I started having some lagging with my  streaming services Icecast/MPD and MiniDLNA.  I assumed I just needed to  reboot and then was not able to even get into the computer.  Being one  who does not regularly make backups, that was the first thing I tried to  do so now I have a separate drive that has my "old" system on it (used  ddrescue from live USB).  From the login, I would try to log in to GNOME  Classic and nothing would happen, it would just change screens and  hang.  I decided with a backup in hand I would simply upgrade to 14.04  LTS and everything would work itself out.  Not so.  I can get into GNOME  but after a short period of time the desktop manager freezes and locks  they keyboard out.  I think the mouse still moves and I know the system  is still working since I can still hear the music, SFTP in, access MPD,  MiniDLNA, etc.  I have tried to get into a shell with CTRL ALT F7 but  nothing happens, the Caps Lock key doesn't work, the only thing I can do  is CTRL ALT PrtSCN and the REISUB to reboot the computer (other than  the case reset key).  I installed xubuntu desktop and am presently able  to do *most* things with that though generally Google Chrome locks the system  up in short order.  I don't particularly want to change and cannot  stand how it suspends music playback when I lock the screen.  I think  there is a workaround for that but the biggest problem is with GNOME.

In addition to doing the release upgrade, and installing xubuntu, I've  tried to get rid of all traces of GNOME and then reinstall.  GNOME still  locks up within a couple minutes of booting into it.  I really do not  want to have to rebuild the system from scratch since it has been a  while since I got everything working on the back end, etc.  The system  I'm on now is the 14.04 LTS/Xubuntu.  I had planned on upgrading at some  point anyway so that is fine, but I would like to be able to use the  classic gnome as well as to be able to use chrome.

I've been running Ubuntu for a while now but am generally limited to  knowing enough to get by.  The things I've set up on the "server" side  of the system are working the way I want and I'm really hoping I don't  have to try and recreate that from scratch (users, services,  permissions, etc.)  I don't like xubuntu and just want to figure out  what is wrong with GNOME and get back to where I was two weeks ago. 

Also, upon login to my system I get a dialog box that says "System  program problem detected / Do you want to report the problem now? /  Cancel / Report problem..."  It doesn't tell me what the problem is.   This has been going on for years and hasn't seemed to be anything but a  minor annoyance (I said above "no practical issues").  As everything  worked, I just assumed it was probably something to do with NVIDIA or  something (which took me a while to get working, another reason I do not  want to mess with my current setup).  Additionally, during the startup  prior to entering into LightDM, I've started getting beeps from the  computer that I don't remember occurring a few weeks ago.  I don't think  they were there since during this whole process, I was surprised by  them.  As I rarely rebooted my computer, it is possible that I just  never really noticed them but I don't think that is the case.

---

### Post by bvargo on 2016-01-22
It appears sudo rm ~/.Xauthority solved the problem.  Still haven't tried chrome yet.

---

### Post by bvargo on 2016-01-22
No, chrome still looks up the UI but the music still plays and the mouse moves.  No idea how to completely remove and reinstall chrome because no guide I've ever tried worked.

---

