---
title: "If my system freezes how do I drop out of gui to raw cli?"
date: 2020-01-25
forum: General Help
---

### Post by david503 on 2020-01-25
If my system freezes how to I get to raw CLI? I thought it was [COLOR=#000000]Ctrl-Alt-F1 because that works at boot, but if the gui is frozen up that doesn't work.   But how do I get to cli and then get back?[/COLOR]

[COLOR=#000000]Note: I'm not talking about ending the session- Basically a simpler version of the question may be:  I want to keep the session open but kill chrome and then get back to the GUI in the same session after having killed chrome which is probably what was hogging the memory and freezing everything and every window and even mouse movement.[/COLOR]


[COLOR=#000000]m[/COLOR]

---

### Post by CatKiller on 2020-01-25
It used to be the case that the GUI session was on TTY 7, so 1-6 were available as text consoles. Now I think the login screen is on 1 and the GUI session is on 2, so 3-7 are available as text consoles. It's Ctrl-Alt and then the numbered F-key to switch between them.

---

### Post by The Cog on 2020-01-25
On Xubuntu 19.10, it's still Ctrl+Alt+F1 through Ctrl-Alt-F6. But of course if the whole system is frozen (not just the GUI frozen) then that won't help.

---

### Post by david503 on 2020-01-25
Well presumably I could ssh into it from another pc right?  

And if I did, could I see all the processes just with my user account or would I need to be root (which I can do) to see the processes running and kill the chromes right?

---

### Post by TheFu on 2020-01-25
yes, you can ssh in, then use any of the thousands of CLI tools.
No need for root. Use the same account you log into the GUI using.

---

### Post by The Cog on 2020-01-26
> **david503 said:**
> Well presumably I could ssh into it from another pc right?  

And if I did, could I see all the processes just with my user account or would I need to be root (which I can do) to see the processes running and kill the chromes right?
If only the GUI is frozen, yes. But in that case, Ctrl-Alt-Fn should work.
If the whole system is frozen then it won't be answering ssh calls either.

---

### Post by david503 on 2020-02-05
Quick update for others with the same question- last time it crashed I tried sshing in from my notebook laptop and it just hung on the ssh attempt.  haha. didn't say "no route to host", just hung.

---

### Post by Holger_Gehrke on 2020-02-05
I occasionally have the same problem with Firefox on a machine with 4 GB. Modern browser treat memory as if an infinite amount of it should be available. If I don't close and restart the browser at the first sign of slowdown due to swapping the system freezes in a similar way to your description. Ctrl-Alt-F1 **does** work but it takes a long time before something happens. In one instance it took two minutes until the screen blanked, a further minute or so for the prompt to appear and another minute until the system started accepting character entry for the user name. Using the Magic SysRequest combo and doing an emergency shutdown and reboot would probably be faster but is not an option if you have unsaved work in some other program you can't or don't want to redo after the reboot.

Holger

---

