---
title: "[SOLVED] One User cant log off Ubuntu 8.04"
date: 2008-07-08
forum: General Help
---

### Post by Jimtuv on 2008-07-08
I have one user that can't log off. It takes hitting the power button which then does a normal shut down. When I try to log them off it hangs right after pressing the log out button. Everything except the desktop background disappears and if left it will just sit there with out ever going back to the log in screen. All other users are fine and can log in and out. I am not sure what they were playing with to get it stuck.

---

### Post by p_quarles on 2008-07-08
Do you get any kind of feedback when attempting to log out? How are you logging out? Via the panel button, or with ctrl-alt-backspace? Can this user perform other login-manager functions (e.g., shutdown or reboot)? 

What's the output of "who" in the terminal?

---

### Post by Jimtuv on 2008-07-08
> **p_quarles said:**
> Do you get any kind of feedback when attempting to log out? 

None. All that can be seen is the desktop background.

> How are you logging out?

The only way to get out of that is to hit the power button. Which then goes through a normal shutdown. (Ubuntu screen and bar)

Haven't tried Crtl + Alt + Backspace 

The user is fully functional but can not do any login manager function (restart, log out, shut down) but can switch users.

jim      tty7         2008-07-08 13:54 (:0)
jim      pts/0        2008-07-08 14:08 (:0.0)

---

### Post by Jimtuv on 2008-07-08
> **p_quarles said:**
> Do you get any kind of feedback when attempting to log out? 

None. All that can be seen is the desktop background.

> How are you logging out?

The only way to get out of that is to hit the power button. Which then goes through a normal shutdown. (Ubuntu screen and bar)

Haven't tried Crtl + Alt + Backspace 

The user is fully functional but can not do any login manager function (restart, log out, shut down) but can switch users.

Output of who
jim      tty7         2008-07-08 13:54 (:0)
jim      pts/0        2008-07-08 14:08 (:0.0)

---

### Post by kdorf on 2008-07-08
You could try adding killall -9 -u jim to the .bash_logout file. That'll kill everything being run by that user. It would almost certainly force a logout.

---

### Post by Jimtuv on 2008-07-08
I think I have tracked down what is happening but I don't understand why. They installed a program called Keytouch to enable some of the extra keys on the keyboard and it was this program not allowing the log off. I used the synaptic package manager to uninstall it and now I can log them off. The other thing I noticed was a delay in keystrokes and some stuttering keys when typed it would repeat keystrokes. What I figure is that it was fighting with the keyboard driver.

---

### Post by sayakb on 2008-07-08
If you don't have any further problems in this context, please mark the thread as solved :)

---

