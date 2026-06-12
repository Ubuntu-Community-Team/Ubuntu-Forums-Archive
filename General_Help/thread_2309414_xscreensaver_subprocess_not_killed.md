---
title: "xscreensaver subprocess not killed"
date: 2016-01-10
forum: General Help
---

### Post by ggordon on 2016-01-10
Several times lately I have noticed that one of the graphics demo subprocesses continues to run after I log back on through the xscreensaver interface.  My display comes up normal, but I notice slow response.  The system monitor will show one of the xscreensaver graphics demo subprocesses continuing to run, using significant CPU time.  I kill the process and then everything is fine.  xscreensaver apparently keeps running and starts a new graphics demo subprocess the next time I'm idle.

It looks like for some reason xscreensaver is not killing the subprocess when I log back on, although the subprocess is not displaying to the monitor.  This problem may have started about the same time that I installed the Chrome Remote Desktop application.

---

