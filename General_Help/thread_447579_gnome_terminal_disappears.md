---
title: "gnome terminal disappears"
date: 2007-05-18
forum: General Help
---

### Post by kornelix on 2007-05-18
I am trying to make a launcher to show the file .xsession-errors.

The man page for gnome-terminal led me to create a launcher with the following command:
```
gnome-terminal -x cat .xsession-errors
```
The window appears and disappears in milliseconds.
Adding the -hold option makes no difference.

Will someone kindly tell me the correct black magic to invoke?

thanks

---

### Post by Lieter on 2007-05-18
the -x option tells it to eXecute the command, try gnome-terminal without that  as launcher

---

### Post by kornelix on 2007-05-18
> **Lieter said:**
> the -x option tells it to eXecute the command, try gnome-terminal without that  as launcher

The whole point is not having to type in the command.

Generally, how do you pop-up a window, run an automatic command, and make the results not instantly disappear?

---

