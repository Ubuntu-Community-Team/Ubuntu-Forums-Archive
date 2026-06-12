---
title: "Locking up"
date: 2007-05-04
forum: General Help
---

### Post by OniAnubis on 2007-05-04
Ok I'm going to try to explain this so it's understandable. I've been running Ubuntu on my HP Pavillion ze5300 series laptop (Acutally ZE5375us if you need to know) I've been able to run edgy, dapper, and feisty on it and use it well, however my  desktop randomly slows to a crawl to the point where I have to hard reboot. When this starts to occur my mouse icon will start flashing on and off at a steady interval. Once this happens I know a few more clicks and then I'll have to reboot. Once the desktop is locked I can switch to a console using the ctrl-alt F keys and I can type, and run commands with no problems. If I try and ctrl-alt F back to the gnome desktop my screen turns almost fully white with multicolored thin lines running up and down it. At this point my laptop is totally locked and I have to hard reboot. This has happened with all three versions of Ubuntu however it DOES NOT occur if I run Kubuntu so I think its something related to gnome, but whatever it is, its been persistent for the last three releases of Ubuntu. I really don't want to have to run Kubuntu because I really don't like KDE that much. Is anyone else having problems like I've described? The random slow down and locks ups suck, and so does the inability to change to a console and then back to the gnome GUI. 

Laptop Specs:
Intel Pentium 4  2.4Ghz
512MB Ram
ATI Radeon IGP 345M


Edit: 
When I said that the problem does not occur in Kubuntu I mean the problem with the GUI slowing down and then freezing. If I switch to a text console and then switch back to the KDE desktop then I get the white screen with the colored thin lines and the computer completely locks up. Also the white line lockup happens if something changes my screen resolution, like switching a vmware session from full screen back to windowed mode and that happens with both KDE and Gnome

---

### Post by OniAnubis on 2007-05-05
I'm thinking its the ati driver...

Ugh this is driving me crazy. With the default ati driver in xorg.conf I don't get hardware acceleration. Has anyone been able to get an ATI IGP 345M working with hardware acceleration? with fglrx or something?

---

