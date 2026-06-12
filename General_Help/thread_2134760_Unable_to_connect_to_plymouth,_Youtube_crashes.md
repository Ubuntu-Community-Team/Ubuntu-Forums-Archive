---
title: "Unable to connect to plymouth, Youtube crashes"
date: 2013-04-12
forum: General Help
---

### Post by Zukaro on 2013-04-12
I was watching YouTube and then all of a sudden everything exploded (literally (okay, almost literally)).  X froze completely so I restarted my computer (went to another terminal and reboot it with the command rather than by pressing the reset switch on my computer).  Now when Ubuntu starts I get to the start page just fine but when I try to login I end up at a black screen which says something is unable to connect to plymouth (I couldn't see what it said as it was cut off); the screen only appeared for a second.  To try and fix this I went into another terminal (ctrl+alt+F1) and typed ```
sudo restart lightdm
``` to try and see if that'd fix the issue but it didn't help.  So then I tried stopping lightdm and starting it again in that terminal; the login page came up but I've got the same issue.

Right now I'm just switching terminals and starting x then once x starts pressing ctrl+alt+t to bring up the terminal and then starting Unity so I can still use my computer (I could just boot into Windows but bleh, Windows is slow).  But I want to fix this problem so I can use my computer normally.

Also, when I start x it tells me that some authentication thing timed out.


Does anyone have any ideas of how I can fix this, and why it even exploded like this in the first place?  Rebooting my computer does nothing to fix the issue so something's really broken.\


edit:
It appears that everytime I run YouTube in full screen it crashes X now; but it takes a few seconds before it does that.  I wasn't having this issue earlier today however; but for some reason all of a sudden I'm having this problem and I've got no clue whats wrong.

---

### Post by Zukaro on 2013-04-13
Anyone have any ideas?  I've been looking around on Google a bit but I've been unable to find anything.

Also, the specific error is "mountall: unable to connect to plymouth"

---

