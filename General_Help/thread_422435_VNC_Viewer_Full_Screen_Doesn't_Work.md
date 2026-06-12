---
title: "VNC Viewer Full Screen Doesn't Work"
date: 2007-04-25
forum: General Help
---

### Post by musther on 2007-04-25
If I select use full screen mode in the Terminal Services Client and then try to connect, via VNC, I get the attached error:

I remember having this issue in earlier versions of Ubuntu, on a different machine too, very odd.

Seems to me the TSClient is issuing the wrong vncviewer command, but I can't believe this hasn't been fixed.

---

### Post by jinx099 on 2007-04-25
try installing and using xvnc4viewer

---

### Post by Aetherius on 2007-04-25
try ```
vncviewer -fullscreen {IP ADDRESS}
``` from the terminal

---

### Post by musther on 2007-04-25
Thanks, both seem to work now, but the switch isn't -full-screen, it's -fullscreen.  So that could be the problem with the TSC, it could be issuing the wrong command?

---

### Post by FromFPan2Fire on 2007-05-06
I'm trying to resolve the same problem.  (Connecting to a Windows 2000 Pro from a Ubuntu laptop with VNC I can't get a full screen).

Upgrading to xvnc4viewer - which seems to have helped some - made no change for me.

The line:    vncviewer -fullscreen {IP ADDRESS}        Resulted in my my Ubuntu screen going black, except for the remote window - which is still not fullscreen.  (In addition, I can't find a way to get control back to Linux, every command executes on the 2000 machine - Cold boot time.)

Any help would be much appreciated.  Repeated is the post I was drafting when I found this post:

I've seen this problem posted and have searched for a few hours, but haven't found a solution.  Your assistance is much appreciated.

ISSUE:  Using Terminal Services Client on an Ubuntu Laptop to connect to a Windows 2000 Pro Desktop.  The VNC window on the laptop will not run in full screen - when maximized the VNC screen showing the windows desktop will use only about 1/3 of the laptop's screen.  If selecting the "Full Screen" option on the Display Tab an error message occurs when trying to connect.  (The message shows "how to" without any indication of the reason for the error.

PROBLEMS:

- The main problem as described above - Terminal Server Client window on Ubuntu won't expand beyond about 1/3 of the Ubuntu screen; full screen mode won't work.

- When scrolling and highlighting on the Windows 2000 machine through the Terminal Server Client window the Terminal Server display does a poor job of keeping up and accurately reflecting the actual Windows display.

- When closing the Terminal Server window an error message always occurs.

ATTEMPTS:

- Upgraded VNC from version 3.3 to 4.1 on both Ubuntu and Windows machines - no change.

- Tried selecting RDP and RDPv5 protocols from Terminal Server Client - Received "Connection Refused" error.  (Perhaps related to lack of a RDC server for Windows 2000 Pro.)

- Tried a command line rdesktop command - received the same "Connection Refused" error.

---

