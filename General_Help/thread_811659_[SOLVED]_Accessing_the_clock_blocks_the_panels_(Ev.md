---
title: "[SOLVED] Accessing the clock blocks the panels (Evolution+google calendars?)"
date: 2008-05-29
forum: General Help
---

### Post by eltama on 2008-05-29
I am having a serious problem that I guess is related to Evolution.
If I click the clock applet most of the applets freeze: the main menu, the launchers, the shut down bottom (but not the system monitor) can not be clicked anymore. The bottom panel also becomes unclickable and it does not refresh.
Also, starting Evolution displays a message box saying that it crashed before and that the preview panes will be hidden, but the buttons Ignore and Recover can not be clicked.
If I restart GNOME (ctrl-backspace-delete) and log in again, the top and bottom panel do not appear. I have to restart the computer.

Today there were many upgrades, including a new kernel, before the update everything worked fine.
I guess that the problem is that some days ago I added some google calendars, but it looks that the feature is buggy. Probably the problem with the clock is that it is trying to show the events from these calendars. I tried deleting the folder .evolution but it didn't fix the problem.

I will really appreciate any help since I can not access my email anymore.
By the way, I am running Hardy Heron on a Dell Latitude 420.

---

### Post by george9233 on 2008-05-29
I've got the same problem weeks ago, but it now doesn't exist any more. There is a simple way to fix the panel freeze problem: press Alt+F2 and enter "gnome-terminal", in the terminal type "killall gnome-panel" and the panel will be restarted. After that it will return to normal state.

---

### Post by eltama on 2008-05-29
> **george9233 said:**
> I've got the same problem weeks ago, but it now doesn't exist any more. There is a simple way to fix the panel freeze problem: press Alt+F2 and enter "gnome-terminal", in the terminal type "killall gnome-panel" and the panel will be restarted. After that it will return to normal state.

Thanks for your answer, I just discovered that too, and I was going to post it :)

But the best part is that Evolution opened up and when I unclicked the google calendars I could access the gnome clock again. So, my suspicions are confirmed.

---

### Post by fsm on 2008-12-16
Well, I've been searching for a solution to this problem and have found all kinds of reports and leads, but no real fix.  Part of the problem is I think that people will report some fix has worked, when it hasn't really.  See 4th point below:

What I know:
- if I boot up, and click on the clock, the task bar (gnome-panel) freezes completely.  The only way to get it back is to switch to another display, kill gnome-panel, then switch back and ctrl-alt-backspace.  Killall gnome-panel may also work.

- This only occurs if I have evolution synching with google calendar

- If I uncheck google calendar in evolution, all works fine

- If I run evolution, and check the calendar *before* I ever click on the clock, the calendar and clock with both work fine.  Clicking on the clock does become much slower however, but no lockup.

So the workaround appears to be to either remember to check the calendar in evolution first, or just never use google calendar from within evolution...which sucks.

Any other suggestions?

---

