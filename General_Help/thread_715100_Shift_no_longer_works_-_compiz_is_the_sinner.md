---
title: "Shift no longer works - compiz is the sinner"
date: 2008-03-04
forum: General Help
---

### Post by nors on 2008-03-04
Hi all.

Suddenly my shift key no longer works. Narrowed it down to that my compiz is causing this problem as when i turn it off the shift key goes back to normal.

I have no idea what in compiz is causing the problem. I tried to do a filtered search for "shift" on actions, but none of the bindings is on shift alone... 

So... I absolutely don't get why it's not working.


Anyone have any ideas?

---

### Post by nors on 2008-03-04
I just tried to disable one all settings i had enabled one by one to see if one of them were causing the described error but with no luck. None of them generated the error - at least not directly, so it seems the be compiz in general.... :(

---

### Post by simple_simon46 on 2008-03-06
I experienced the same thing on my first Ubuntu install in a damn long time, I just figured it was compatible and carried on. 

However after some digging around I found a way to fix it and have compiz running. 

Follow [these]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml") instructions to install a different version of compiz. Then run it from the terminal. 

Then goto appearances and you should see an option for "custom" with a "preferances" button beside it go there. Then goto "General Options", then the tab marked "actions" and remove the entries there that contain the shift key (note: you can't disable the first one so you have to remap it, it's the slow animations one). Close the windows and you should be all set ... let me know if it doesn't work for you. 

~ss

---

### Post by simple_simon46 on 2008-03-06
Also, as a temporary work around, if you press control before you press shift the shift key will work (seems to arrest the bindings temporarily).

~ss

---

