---
title: "Glitchy and insecure behavior from 16.04 lock screen"
date: 2017-03-19
forum: General Help
---

### Post by fuhsjr00 on 2017-03-19
I recently installed Ubuntu 16.04.2 on an Asus Zenbook Flip UX360C, and I'm seeing a lot of odd behaviour from the lock screen when I suspend-resume via closing and opening the notebook.

From the most serious to the least:


[LIST]
[*]Lock screen is completely bypassed, returning to the desktop session. When this happens it looks like it briefly attempts to bring up the lock screen and then returns to the desktop. Seen infrequently. 
[*]Briefly shows the desktop before bringing up the lock screen. This is behaviour that I've seen in previous versions of Ubuntu (14.10) on other Zenbooks (UX305FA). It looks like someone tried to address it... incompletely. Seen infrequently. 
[*]The lock screen shows up with no way to interact. Password box is missing, No controls available to interact with. Restarting lightdm makes things usable again, but the desktop session is gone. Only seen once. 
[*]Auto-login to guest account. The original user session is still there. Only seen once. 
[*]Lock screen appears with upper-right control selected. Sometimes the password box has focus, sometimes not. Seen frequently. 
[*]Lock screen flickers when it first appears. 
[/LIST]

I think the first one deserves a bug. I've been trying to find out if there's something I can do to provoke it into showing more often.

Does anyone have insight into any of this?

---

### Post by fuhsjr00 on 2017-03-19
For the lock screen bypass, it looks like when close the laptop with a Terminal, System Settings, and Firefox open, I can make the problem appear much more often.

I also see this with 16.10, though it seems a little more difficult to repro.

---

