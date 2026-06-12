---
title: "Error while installing Netflix Desktop?"
date: 2014-03-23
forum: General Help
---

### Post by ilikecolors on 2014-03-23
Hey, I was trying to install Netflix accordingly to this guide:
[http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/](http://www.howtogeek.com/130372/how-to-watch-netflix-on-ubuntu-with-the-netflix-desktop-app/)
However, on the last command line, I get this error after putting my user password:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

And I don't have absolutely any idea what that means. ANy help?

---

### Post by ilikecolors on 2014-03-23
nvm i got this

---

### Post by sammiev on 2014-03-23
Others will run into the same problem as yours and on a search will bring up this solved post. Please let ppl know how you solved your problem. TY :)

---

### Post by deadflowr on 2014-03-23
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

This is typical of what to expect if apt or dpkg has a crash.
the dpkg -confugre a command basically resets it(dpkg).
Otherwise it'll be stuck in the broken non-functional state.

What caused the crash is anybodies guess.
the dpkg log might say something.
look in /var/log/dpkg.log
or also, /var/log/apt/term.log, and /var/log/apt/history.log

those places might throw you some clues.

---

