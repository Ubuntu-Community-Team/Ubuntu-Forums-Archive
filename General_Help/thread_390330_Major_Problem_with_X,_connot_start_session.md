---
title: "Major Problem with X, connot start session"
date: 2007-03-21
forum: General Help
---

### Post by malfist on 2007-03-21
I booted up my computer this evening and came across a very upleasent message, X server could not be started blah blah blah...
At first I thought Video card is loose so I made sure it was securly in the AGP slot. Then rebooted, greated by same message.

The detailed X report talked about problems with fonts so I followed it's directions and ran mkfontdir in the desired locations, but that didn't fix it.

It got rid of most of the errors but it is still giving this:

Fatal server error:

Could not open default font 'fixed'
XIO : fatal IO error 104 (connection reset by peer) on X server ":0.0"
after 0 request (0 known prossesed) with 0 events remaining.

That's in root, if I logon and run startx or let it run it I also get:
xauth error: (something about couldn't get a lock on /home/jerome/.Xauthority

Please, how do I fix this?

---

### Post by Aeriuz on 2007-03-22
Got the same problem i can start startx with sudo...

---

### Post by malfist on 2007-03-22
I fixed it, reinstalled xfonts-base and install xfs and Xubuntu is up and running again (but for some reason aptitude uninstalled thunar on me and I had to reinstall it :(  )

---

