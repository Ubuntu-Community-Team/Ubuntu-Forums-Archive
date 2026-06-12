---
title: "remove 2x password prompt when Switch User?"
date: 2007-04-28
forum: General Help
---

### Post by maphew on 2007-04-28
Hi,

Is there a way to remove the double password prompt when Switching Users? 

Currently  when Switch User is used I get plonked back to the main login screen, enter the user & pass to switch to, and then immediately get prompted again to Unlock the session for that user.  "I just did that darn it! Why are you asking me again?"

thanks in advance for your thoughts.

---

### Post by Schalken on 2007-04-28
When you switch users, it sets up a second login screen (under Ctrl+Alt+F8) and locks your old one (under Ctrl+Alt+F7). You could go to your locked one and enter your password only once by hitting Ctrl+Alt+F7, but yes I agree that it should unlock your session for you when you are returned to it from the second login prompt. I coudln't find an option for it under System > Administration > Login Window.

Maybe file a bug if there isn't one already.

---

### Post by maphew on 2007-04-30
thanks for the alternate route. I didn't know about that and I think I will file a bug. 

For those following, the first keyboard shortcut which was eaten by a smiley is [ctrl-alt-F8]. With some playing around I learned that using [ctrl-alt-F#] one can also switch between users without a  password prompt at all if the respective target sessions have not been locked.

F1-F6: tty login consoles (text mode)
F7: first graphical desktop login
F8: text mode messages about Starting and Enabling services (bluetooth, battery management, etc.)
F9: second desktop login
F10: third desktop login
F11-12: possibly 4rth and 5th desktop logins? I only have 3 users to test with so F10 is as far as I got.

---

### Post by maphew on 2007-04-30
removing the double password prompt is (wishlist)  Bug #41333, first reported on 2006-04-25  by Irios ( [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/41333](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/41333) )

---

