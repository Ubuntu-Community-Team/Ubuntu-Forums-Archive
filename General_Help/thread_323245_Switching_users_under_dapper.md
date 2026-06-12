---
title: "Switching users under dapper"
date: 2006-12-21
forum: General Help
---

### Post by malius on 2006-12-21
Today I created a new user account on my Dapper installation.

When I attempted to switch users, Ubuntu hard locked the system (i.e. The only way to free the system was to hit the reset button).

Here are the steps I followed:
[LIST=1]
[*]Quit/Lock Screen.
[*]Switch User.
[*]Select new user account and press OK.
[*]System locks up.
[/LIST]

In an alternate attempt, I tried simply selecting Quit/Switch User (Note, I did not lock the screen first).  This worked the first time, but after further attempts, it was pretty hit or miss.

Does anyone have any idea what could be the issue?

I've searched the forums and nothing I've found thus far seems to work.

---

### Post by rowanparker on 2006-12-22
Have you tryed doing it again to see if it was a one-off or not?

---

### Post by dannyboy79 on 2006-12-22
> **malius said:**
> Today I created a new user account on my Dapper installation.

When I attempted to switch users, Ubuntu hard locked the system (i.e. The only way to free the system was to hit the reset button).

Here are the steps I followed:
[LIST=1]
[*]Quit/Lock Screen.
[*]Switch User.
[*]Select new user account and press OK.
[*]System locks up.
[/LIST]

In an alternate attempt, I tried simply selecting Quit/Switch User (Note, I did not lock the screen first).  This worked the first time, but after further attempts, it was pretty hit or miss.

Does anyone have any idea what could be the issue?

I've searched the forums and nothing I've found thus far seems to work.

why are you locking the screen? when ever I want to switch users, I simply click on log off and then log on as the new user.

---

### Post by milton1 on 2006-12-22
When your system locks, can you switch to a terminal login? (ctl-alt-F1)

I have seen many problems with user switching stem from graphics driver problems. X can end up crashing hard.

---

### Post by malius on 2006-12-22
When the system locks, I've tried:

[LIST=1]
[*]All virtual terminals (ctrl + alt + function keys).
[*]Restarting the XServer (ctrl + alt + backspace).
[*]and finally (ctrl + alt + delete).
[/LIST]

None of the above work.

In fact all the indicator lights on the keyboard have been disabled at this point.

P.S.
The reason I'm locking the screen: I want to enumlate the sequence of events that can occur when another user wishes to log in when I'm not home and the machine is locked.

---

