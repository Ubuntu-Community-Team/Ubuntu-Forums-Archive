---
title: "No password textfield when switching users"
date: 2014-08-23
forum: General Help
---

### Post by RayDeCampo on 2014-08-23
Intermittently when switching users the password textfield is missing from the login screen, preventing users from logging in.  There are various work-arounds that sometimes work and sometimes do not.  First I try to use Ctrl-Alt-F7, Ctrl-Alt-F8, etc. to try to find a user that has the password field available.  If that works, I log out all but one user and that typically gets me back to a working state.  If not, I'll try Ctrl-Alt-F1 and see if I can open a terminal.  Then I'll restart the lightdm service.  If X is not responding to the Ctrl-Alt prompts, I'll try to log in remotely and do the same.  Last resort is to restart the box.

If you have any ideas, I'd appreciate it.  Mostly I want to file a bug report but I can't run ubuntu-bug when I am in this state as I have no GUI.  So any guidance on how to file an effective bug report would be appreciated.

---

