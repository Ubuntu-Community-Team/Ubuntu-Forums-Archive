---
title: "Cygwin XWin loses cursor intermittently"
date: 2007-06-21
forum: General Help
---

### Post by dcymbal on 2007-06-21
I doubt very much this is an Ubuntu problem, but I've googled around with no luck so wondering if anybody has any ideas to try.

Using the latest cygwin (but have had this problem for several versions now) on an XP SP2 system to XDMCP to an Ubuntu 7.04 box (problem also used to happen with 6,06 and 6,10 as well).  

Things work well for some period of time, but I inevitably wind up losing the cursor in my X window.  Sometimes I can run for 2 days before it happens, sometimes only for 2 hours,  I can't discern a pattern on when it happens.  The cursor is just hidden, as moving the mouse about will highlight X widgets/buttons/etc. and you can click on buttons and actions will fire.  If I move the cursor off the X session and back onto the XP desktop it shows.  It is only lost when over the X window.  I assume it is some sort of cursor hide/show bug in Cygwin's X server, but I would have thought others would have reported similar behavior and like I say I wasn't able to find any reports googling.  Any ideas?  Anybody else seen any similar behavior?

---

### Post by dcymbal on 2008-03-07
This is a known issue with the cygwin XServer.  There is a workaround:  when you lose the cursor, you can right click the 'X' icon in the Windows task bar and select "Show Cursor" to force it to display.

---

