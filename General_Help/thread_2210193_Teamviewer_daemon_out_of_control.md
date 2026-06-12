---
title: "Teamviewer daemon out of control"
date: 2014-03-09
forum: General Help
---

### Post by Tristan_Williams on 2014-03-09
I am running Ubuntu Minimal 13.10 with Xfce4.
I installed Teamviewer with the Deb from their website.

There is an option in the Teamviewer preferences menu that says "Start teamviewer with system", it is unchecked. So it should not be starting automatically.

When I boot my computer, and login, there are 10 instances of teamviewerd (the teamviewer daemon)
Apparently (since I am running lowlatency kernel) they are on the "realtime" V.I.P. list.

They are getting out of control because I have to wait 2-3 times longer for everything to happen (clicking, scrolling, firefox, everything) because they are hogging resources.

Right now, when I boot, I have to immediately open a terminal, and issue "sudo killall teamviewerd" 10 times in order for anything to work.

How do I keep this from happening?

---

