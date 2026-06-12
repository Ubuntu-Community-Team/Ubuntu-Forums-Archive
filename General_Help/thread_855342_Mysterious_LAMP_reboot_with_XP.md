---
title: "Mysterious LAMP reboot with XP"
date: 2008-07-10
forum: General Help
---

### Post by orangey on 2008-07-10
Hi, I'm looking at a very weird scenario.  I have a LAMP webserver running every day, and yesterday (7/9) at 15:53, it rebooted.  I can see the reboot logged in the logs, but no indication as to why.  Process error?  Power failure?

Now the really weird part.  I have a normal Windows XP box on the same network.  It rebooted at the SAME time, 15:53.  Now that system is in another part of the house, so not even on the same power circuit.  Similarly, I'm looking at the event viewer on that windows box, and again, it said it rebooted, but doesn't say why.  None of those "the previous shutdown was unexpected" nor "your system was recently updated" messages.

Any ideas how this could possibly happen?  And please don't tell me my network has been hacked into.  I've attached the messages and syslog files from the webserver.  I booted it normally at 6:42AM in the morning, and then it spontaneous rebooted at 15:53.

---

### Post by Fire_Chief on 2008-07-10
If neither box is on a battery backup, then I would suspect a power failure to the home or the neighborhood.

---

### Post by orangey on 2008-07-10
I suspected that as well, since we've been under a sorta heat wave lately and everyone in the neighborhood has been blasting AC all day and night.

But none of my alarm clocks were flashing when I got home, and I checked my NAS box and the router and neither of those were rebooted.  And I'm not sure about ubuntu, but windows usually tells me that the "previous system shutdown was unexpected" if it were a power outtage.

---

### Post by Fire_Chief on 2008-07-10
Hmm...that is pretty weird. Not sure why that would happen so specifically on both systems if they are directly plugged into the wall.

---

