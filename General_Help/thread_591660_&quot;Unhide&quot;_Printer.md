---
title: "&quot;Unhide&quot; Printer"
date: 2007-10-25
forum: General Help
---

### Post by Hatty on 2007-10-25
My grandma just updated to gutsy today and she accidentally hid the printer icon that shows up in the notification area.

How do I "unhide" it?

I tried google but all I found was this bug report;
[https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/151360](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/151360)

where it says:
> 
- If you hide the applet (via right-click on the icon and selecting "Hide"), you can't show it again, and it no longer shows when you print a document. There's no easy way to return back the icon again.


Is this true? Is it impossible to change it back or does it require some CLI wizardry?

-Hatty

---

### Post by feenstra on 2007-12-31
> **Hatty said:**
> My grandma just updated to gutsy today and she accidentally hid the printer icon that shows up in the notification area.

[...]

Is this true? Is it impossible to change it back or does it require some CLI wizardry?

-Hatty

Apparently, yes. And, yes with some CLI voodoo you can resurrect the icon without logging out and in, but it is a bit of a long ritual:

First you
```
ps -f | grep system-config-printer-applet
```
and from the output get the second word, which is the process ID (5306 in this case):
```
feenstra  5306  1783  0 11:24 pts/4    00:00:00 grep system-config-printer-applet
```
then you
```
kill 5306
```
and, finally, start the new applet:
```
system-config-printer-applet
```
The icon doesn't appear right away, but will when you print something (or some other printer event occurs, I presume).

Hope this helps you, I just had to find out by myself...

---

