---
title: "Firefox crashes"
date: 2005-10-14
forum: General Help
---

### Post by Reducer on 2005-10-14
Just installed Breezy AMD64.  Firefox will block a pop-up, when I click the yellow bar to tell it not to notify of any more blocked pop-ups, Firefox shuts down.  Happens every time.

Let me know if you need more info.

Firefox is also shutting down at random times, even when not in use.

---

### Post by todolopuedo on 2005-10-22
I have the same problem with a Centrino laptop (i386).  I suspect of a firefox extension problem or some critical bug with JavaScript code.  Right now I am running Galeon because Firefox crash always with many different pages.

---

### Post by Trab on 2005-10-23
i would reccomend runing it under terminal (not sudo) and to see what it says, and then try it under terminal with sudo, my sudoed firefox works fine on some things that give my regular one crashes... 
copy n paste what the terminal says here...

---

### Post by Dolphin on 2005-10-23
There's a new FF 1.5 beta on the firefox website you could try too.

---

### Post by Reducer on 2005-10-23
For me, it turned out that it was the GPL-Flash plugin I was using.

---

### Post by Marco Modesto on 2006-06-25
In my Ubuntu 6.06 (Dapper Drake) the problem was with Flash, the follow link describes the problem:

[http://www.brainonfire.net/2006/05/25/firefox-crash-on-flash-content-in-ubuntu/](http://www.brainonfire.net/2006/05/25/firefox-crash-on-flash-content-in-ubuntu/)

Solution

    The libflash0c2 seems to be the source of the problem, and uninstalling it and its dependants appears to solve this particular flash-Firefox problem.

       1. Close all Mozilla-family browser windows (Mozilla, Firefox, Galeon, Epiphany, etc.)
       2. Uninstall libflash0c2 using Synaptic package manager or apt.


[]s

Marco Modesto.

---

