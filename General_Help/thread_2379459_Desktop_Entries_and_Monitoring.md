---
title: "Desktop Entries and Monitoring"
date: 2017-12-05
forum: General Help
---

### Post by electrosteam on 2017-12-05
I have added three  [Desktop Entry] icons to my LXDE desktop, and they work fine.

Two set/reset a keyboard map that swaps the Menu key to Esc and back, used when I am drawing in LibreCad.

The third initiates a log file that records the date/time every 10 seconds.
Part of a current investigation of occasional freeze of the desktop, hoping to see the kernel continue to operate with a frozen screen.
(A frozen screen hasn't happened for several days now, ever since I started writing/testing/correcting the logging script !).

Questions arising:
1.  The icons show as busy for 13 seconds when selected  -  why ?

2.  When I entered 'top' on the command line, the task for the logging does not list, but the logging is continuing.
     If then launch Task Manager, the top display immediately lists the logging as "lxtask".
     Task Manager lists the logging executable and the occasional 'sleep10' entry from the script.
     When Task Manager is closed, lxtask in the top display disappears.
     Each cycle of Task Manager launch/close shows on the top display with lxtask list/not list, but with a different PID each time.
     Note that the logging continues throughout this time.
     
Why does lxtask list/not list ? with a different PID ?

John

---

### Post by electrosteam on 2017-12-05
Sorry, a few minutes away helps clear the mind.
The lxtask listed in the top display is most assuredly the Task Manager itself.

But I cannot find the logging job listed under top, it does show in Task Manager.
As Task Manager is listed as lxtask, perhaps the logging executable file lists as something else.
More research.

John.

---

