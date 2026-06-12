---
title: "Switching Users - How do you without typing your password twice"
date: 2006-11-15
forum: General Help
---

### Post by Kerry Lange on 2006-11-15
Per the message title, how do you switch users without having to type in your password twice?

Assuming there are two sessions open, I need to click on "Switch Users," which brings me to the login screen.  Once the other user's username & password are typed in, you need to select from three options, including resuming a previous session (which is what I'd like to have as the default action).

Then, once you've chosen to resume a session, you're asked to unlock the screen by typing in a password.

Is there any way to make this more simple?  I share the machine with my wife and there's no way she's going to put up with this for very long.

---

### Post by dcstar on 2006-11-15
> **Kerry Lange said:**
> Per the message title, how do you switch users without having to type in your password twice?

Assuming there are two sessions open, I need to click on "Switch Users," which brings me to the login screen.  Once the other user's username & password are typed in, you need to select from three options, including resuming a previous session (which is what I'd like to have as the default action).

Then, once you've chosen to resume a session, you're asked to unlock the screen by typing in a password.

Is there any way to make this more simple?  I share the machine with my wife and there's no way she's going to put up with this for very long.

Simply open a terminal and run:
```
gdmflexiserver
```

You will have two independent X sessions running, one on CTRL-ALT-F7 and the other on CTRL-ALT-F8.

You may try putting that command in your session startup to see if it can always auto-run.

---

### Post by Kerry Lange on 2006-11-15
Hmmm...  When I do as you've suggested and then press Ctl, Alt, F8, (switching to the other session) the screen goes blank, except for a blinking cursor in the upper, left-hand corner of the screen.  Nothing else happens.  I can switch back to the session I was in, though, by pressing Ctl, Alt, F7.

---

