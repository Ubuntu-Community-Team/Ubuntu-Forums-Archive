---
title: "Gaim doesn't start up"
date: 2007-03-16
forum: General Help
---

### Post by SnotRocket on 2007-03-16
Hey I'm having a problem with Gaim.  The whole program was working fine earlier in the day, but now when I start up gaim, nothing shows up.  However, it is running in the background.  My taskbar shows no instances of the buddy list, or anything like that.

If I start up kopete and start talking to people, the gaim chat window will open and display messages alongside the kopete chat window.

Is there any way that the buddy list could just not show up at all?  Is there any way to fix this?

---

### Post by scxtt on 2007-03-16
open a terminal and type **killall gaim**, that'll stop all running instances of it {do a **ps -ef | grep gaim** to check} ... then type **gaim** in the same terminal and see how it performs - it'll also write any errors to your terminal so you can see what, if anything, goes wrong ...

---

### Post by SnotRocket on 2007-03-16
Yeah, running it in terminal shows no errors, it just does the same thing.  When I typed out killall gaim though, the buddy list appeared and vanished in a very short period.  It's like the buddy list is loading behind the desktop and not giving me anything in the taskbar. 

I also found out if I do the terminal commands in this order

killall gaim
gaim
killall gaim

Then it says that no process of gaim is running... so gaim isn't starting up through terminal.

I found out when I delete .gaim from the home directory and startup gaim it works again, but if I close gaim and try to load it up again after it's created a new .gaim the same bug happens.

---

