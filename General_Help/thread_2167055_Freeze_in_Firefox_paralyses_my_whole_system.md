---
title: "Freeze in Firefox paralyses my whole system"
date: 2013-08-12
forum: General Help
---

### Post by halfbeing on 2013-08-12
This question relates to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-meta-lowlatency/+bug/1211283").

Hello.

I have twice today had my system freeze up on me in a very particular way.

In both cases it started with Firefox freezing on me. At this point I could still swap between windows on the desktop and switch between virtual desktops. However when I clicked the little x at the top corner to close the Firefox window, everything became unresponsive. I could still move the mouse pointer, but nothing happened when I clicked on anything. Then I switched to another virtual console. I was able to type my name at the prompt, but when I hit return the cursor moved to the next line, but nothing else happened. I could still switch between virtual consoles and I could still move the mouse pointer.

After a while 8 or 9 messages came up on the console of the form "INFO:task mount.ntfs:2725 blocked for more than 120 seconds" followed by ""echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message". The messages related to firefox, socket thread, DNS Res~ver (three of them), cron, xfwm4 and getty. But the system became no more responsive and I had to force a reboot.

Is there anything I can do to work round this and prevent these freezes? Could NTFS have anything to do with it? At the time I was doing a backup to an external NTFS volume.

---

### Post by halfbeing on 2013-08-12
I have noticed two more things about the freezes. Firstly if I hover the mouse pointer over the edge of a window it changes to the resize pointer. However the contents of the screen remain frozen. For instance the animation in my Fish the Fish applet doesn't move.

Secondly there is still disk activity according to the disk activity indicator light.

---

### Post by halfbeing on 2013-08-13
I have just had an interesting variant on this issue. I had been using my machine for a while when I noticed that the XFCE panels were frozen. When I say they were frozen, nothing responded to mouse clicks, but the animation of my Fish the Fish panel item continued playing. (Remember that in the previous incidents this animation froze.) I could still use the keyboard and the mouse to switch between windows and switch between desktops.

I had a XFCE4 terminal window open with two tabs. In the first I entered 'ps -A' and it hung. In the second I entered 'echo "hello"' and the command worked as it should and I was returned to a command prompt afterwards. I then entered 'ls' and it hung too. I ordered a new window via the File menu and the whole application froze, but other applications remained responsive. I switched to another virtual console, entered my name to log in, and it hung. At this point I forced a shutdown with the power button.

---

