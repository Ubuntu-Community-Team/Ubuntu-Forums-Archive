---
title: "Logoff dialog LONG delay"
date: 2007-11-06
forum: General Help
---

### Post by Bogus83 on 2007-11-06
Hi all,

This is a weird issue that has been present since I installed Gutsy (7.10).  When I click the power icon on the toolbar (top right), the system hangs for upwards of two minutes before displaying the dialog where I have the option to log off, power down, reboot, etc.  I have tried this with nothing running at all, so I don't believe that it's an issue of having to stop too many processes.  I'm running an Athlon 1.6ghz with a gig and a half of RAM- not blazing fast by any means, but I think that should be sufficient to handle bringing up the shutdown screen?  I don't have any other slowdown issues, even when there are multiple windows open.  Any thoughts would be great.

As a side note- if I execute "Shut down" or "restart" from the deskbar launcher, the effect is immediate.  Like, as soon as I hit enter, boom, it goes.  So I think it's a problem with calling up that shutdown screen.  Weird.  :confused:

---

### Post by sawback on 2007-12-03
I have the same problem, but only with domain users (from AD) on Edubuntu. Local users do not have delays. My delay is anywhere from 30 seconds to 2 minutes. At first i thought it just wasn't working, but then was surprised when it finally popped up.

---

### Post by Bogus83 on 2007-12-03
I'm still having this problem.  I only have one user, and it is local.  I don't suppose anyone out there has come across a solution?

---

### Post by mawdryn on 2008-02-11
I've recently found that problem and it was caused by some effect in Compiz (not sure which one as I customised it quite heavily)... Try turning off some of the visual effects within system->preferences->appearance. (setting to 'off' resets the effects back to their defaults)

---

