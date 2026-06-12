---
title: "Lost ability to Logout or Shutdown"
date: 2015-01-03
forum: General Help
---

### Post by WB0HYQ on 2015-01-03
Sometime over the last few days (my computer runs 24/7) I've lost the ability to use the drop-down menu items Logout and Shutdown.  I used to use them all the time to do both, but now I can't.  My account is the only one on the computer and is listed as an Administrator.  I created a new account, set as administrator, and it can do both of the functions.  When I go back to my normal account, the functions fail again.

The only way I can shut the system down and reboot (from my primary account) is to open a terminal and issue the shutdown -r call.

I do have XFCE4 on the system, and if I change to one of those sessions, I can logout and shutdown.  If I change back to a Ubuntu session (default), it fails again.

Any advice here?

EDIT:  Sorry.  Running Ubuntu 14.04.  And by the way, no mattere what search terms I put into the search box, I always get the same results.  Is search working?

Bill

---

### Post by DuckHook on 2015-01-03
See solution in [this]("http://ubuntuforums.org/showthread.php?t=1993329&p=11992518#post11992518") thread. Do you remember doing anything involving your OS (upgrading, etc) just prior to your buttons going AWOL?

---

### Post by WB0HYQ on 2015-01-03
That thread, although having the commands in them, isn't relevant to my problem.  I already CAN logout and shutdown from XFCE4.  It is Ubuntu (default session) that I can't do a thing with.

I don't remember any updating, but it is always possible as there are updates almost every few days.  It used to work, and now it doesn't.  The UI completely ignores the Logout and Shutdown commands.  I've watched the task manager and nothing appears at all.  I thought maybe that something would pop up and get smacked down by the OS, but nothing appears.

Bill

---

### Post by DuckHook on 2015-01-03
Sorry. Did not read carefully enough, just saw the reference to XFCE and assumed Xubuntu. First, try resetting your unity panel with:```
killall unity-panel-service
```These problems are hard to diagnose, but there appear to be a number of possible causes. Did you install any docking app prior to disappearance? Say, cairo-dock or anything else?

---

### Post by WB0HYQ on 2015-01-03
Well, the command caused the top menu to blink, clear, and then come back.  Nothing else changed. I installed Cairo Dock along with XFCE4, but that was many months ago and up until a few days ago, it all worked just fine.  As a double-check, I killed Cairo Dock and tried the killall comand again.  Still no dice.

For some unknown reason, my typing in this edit box is lagging way behind - by as much as several words.  I do type fast, but this has never happened before. I have to stop and let the words catch up with me.

Bill

---

### Post by DuckHook on 2015-01-04
> **WB0HYQ said:**
> ...I installed Cairo Dock along with XFCE4, but that was many months ago and up until a few days ago, it all worked just fine.  As a double-check, I killed Cairo Dock and tried the killall comand again.  Still no dice.I don't use *Cairo Dock* so am just helping you by proxy here, but there is a known bug with *Cairo Dock* that affects the shutdown/reboot/logout functions. Details and fix are [here]("http://askubuntu.com/questions/451070/cant-shutdown-and-logout-from-top-panel-in-ubuntu-14-04-lts"). In particular, following the further *launchpad* bug [link]("https://bugs.launchpad.net/cairo-dock-core/+bug/1242112") is very informative. I would suggest trying to implement the fix contained in the link, since it is understandable, easy to do and innocuous enough, and see if that doesn't fix your issue. Simply killing Cairo Dock ex post facto would not be sufficient if it was its initial invocation that broke *LauncherEntry*.> ...my typing in this edit box is lagging way behind...Could be the result of resetting Unity Panel. Log out and log back in and see if that doesn't fix lag.

---

### Post by CantankRus on 2015-01-04
If you run ...
```
gnome-session-quit
```
does the unity logout dialog come up.

---

### Post by WB0HYQ on 2015-01-04
If i issue the 'gnome-session-quit' command, the logout dialog does come up and I am able to use it.

Logging out and back in did, in fact, fix the lagging problem.  Thanks for that.

I have found that if I add the delay to the start of Cairo Dock (or if I simply wait until the desktop is up and issue the command manually) I have no problems at all.  So, it would appear that the bug is still active and the measures taken to work around it until fixed are adequate.

Thanks to all who help me here.

Bill

---

### Post by DuckHook on 2015-01-04
Good to hear. For benefit of others, please mark thread "solved" using thread tools at top of thread.

Good luck and Happy Ubuntuing!

---

### Post by WB0HYQ on 2015-01-04
I marked it [solved] the moment I posted my last. You must have missed it. :)

Bill

---

### Post by DuckHook on 2015-01-04
Must be this New Year's hangover.

Cheers!

---

