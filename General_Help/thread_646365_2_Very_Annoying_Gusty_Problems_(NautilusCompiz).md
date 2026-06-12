---
title: "2 Very Annoying Gusty Problems (Nautilus\Compiz)"
date: 2007-12-21
forum: General Help
---

### Post by zman0900 on 2007-12-21
I am running gusty with all the latest upgrades as of 12/21/2007 and I have recently developed two very annoying problems.  First, when I log into gnome, the toolbars on top and bottom, as well as all menus are surrounded by a wide white boarder.  This only happens on the first login after a restart.  See the attached file Before.png for an example of how the toolbars look.  I can make the boarders go away by either hitting Ctrl-Alt-Bksp and logging in again, or by opening "System>Preferences>Advanced Desktop Effects Settings" and disabling and reenabling the Window Decoration Plugin. See the attached file After.png for an example of how it looks after fixing.  I have tried changing the setting in "System>Preferences>Appearence" from Custom to Extra and None, and when it is set to none and I restart, everything appears correctly on login.  This makes me think the problem must be with compiz.  I tried to fix this by doing a complete removal of all compiz components with Synaptic to remove all the configuration for it and then reinstalling, but that did not help.  

My other problem, which began happening about the same time and may or may not be related is with Nautilus.  When I log out, the nautilus process is not ended, so next time I log it, the new nautilus process does not start correctly.  If i do pgrep in tty1 after logging out, there will be a running nautilus process.  When I log in again, a second nautilus is created, but it doesn't show my desktop or icons.  Instead I get a blank background with no icons, but working toolbars above and below.  The only way for me to log in again after logging out is to do 'pkill nautilus' in a tty first.  This happens both with and without compiz enabled, although it does have rare occations where it doesn't happen.  

:confused:I'm lost trying to fix this.  I have no more ideas.  I would really appreciate it if someone could help me figure this out.

---

### Post by pointone on 2007-12-21
You should first attempt to determine whether this problem is due to your personal settings or an application problem. Try creating a new user account and see if it is affected.

---

### Post by zman0900 on 2007-12-21
OK, I created a new user account, and after logging in and setting compiz to extra in the appearance dialog, and then restarting, when I log into that account, it does not have the problem with the white boarders around the toolbars and menus and such.  But when I log out of that account and then back into it again, it still has the problem with nautilus not stopping.  After logging in and out of that several times, I then logged into my normal account, and it still had the white boarder problem that it has on its first log on after startup.  So it seems that the white boarder thing is due to something in my settings, but I have already reset all the compiz setting so I'm not sure which settings would cause that.  It seems that the nautilus thing is a system wide problem.

---

