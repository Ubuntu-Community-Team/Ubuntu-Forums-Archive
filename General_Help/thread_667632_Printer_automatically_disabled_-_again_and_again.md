---
title: "Printer automatically disabled - again and again"
date: 2008-01-14
forum: General Help
---

### Post by vancouverite on 2008-01-14
Hello,
I seem to have a unique problem in that whenever I want to print something I have to go System -> Admin -> Printing -> [printer] -> policies and check "enable".  Every time the computer is restarted the printer must be re-enabled.  Once the printer is enabled it works well.

Is there something that I can do to keep the printer enabled when the computer is restarted?

System info:
Ubuntu 7.10 (gusty)
Printer: HP Deskjet 5740
PPD file: Deskjet_5700.ppd (recommended by ubuntu)

Cheers,
Seth

---

### Post by paperdiesel on 2008-01-14
Exact same problem here.  HP laserjet 3380.  If I check that box it works perfectly.  When I reboot, my settings are lost and I can't print until I re-enable it.  What gives?

---

### Post by Teasdale on 2008-02-10
I was going to post about this exact same problem. I see that I'm not the first to have this problem, but I don't see any solutions.

Mine re-sets itself all the time, not just when I re-boot. It resets itself in the middle of a print job and then just stops printing before the whole document is finished printing!

---

### Post by jahLux on 2008-02-11
Please add my voice to this chorus. Same symptoms - requires going into System -> Administration -> Printing -> Policy and check 'Enable', to allow printer to do it's thing. All is lost on shutdown and reboot!

---

### Post by beczka2005 on 2008-02-12
Same here, but what's even worse is that the only account which has administrative access is mine and I don't have physical access to the machine. So every time this happens I need to ask a non-administrative user to log in as me (with my administrative password) to go and check that enable box!

Is there a CLI equivalent of this enable command? Or can I give users access to this enable button?

---

### Post by bakechad on 2008-03-15
Me too.

HP Laserjet 1012

Has this been logged as a bug yet?

---

### Post by Aidin Sabetian on 2008-03-15
please report this problem at [launchpad]("http://launchpad.net/").

---

