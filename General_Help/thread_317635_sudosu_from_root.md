---
title: "sudo/su from root"
date: 2006-12-12
forum: General Help
---

### Post by twitchku on 2006-12-12
Ok, i have a question about how sudo works. When i set up some scripts to be run from root automaticall, a couple of them need to sudo as a user (to auto start apps, etc.). I've noticed that logging in as root from another VT, or via su -, i can run the exact commands (sudo -u USER SPECIFIC-COMMAND, sudo -H -u USER SPECIFIC-COMMAND2 -arg), and they'll work to a certain extent.

One in particular that is bugging me is a resume.d script i have set to wait for the user to enter his password to unlock gnome-screensaver - it checks "gnome-screensaver-command -q" for "inactive." It all works exactly how i need it to, except for when the system actually runs it in a realistic scenario - i.e. resume from suspend.

I did a little probing and have found that most sudo commands are indeed working properly except, in gnome-screensaver-command's case, it returns about six blank spaces instead of "The screensaver is in/active."

I see that running gnome-screensaver-command as root returns dbus error, and the "sudo -u" command i've set up works outside the script. Anyone have any idea what i need to do to fix this?

---

### Post by aysiu on 2006-12-12
I've moved this to a more appropriate forum.

---

### Post by twitchku on 2006-12-13
Thanks.

---

