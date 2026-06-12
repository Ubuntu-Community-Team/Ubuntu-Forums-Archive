---
title: "emacs with and without X"
date: 2006-11-01
forum: General Help
---

### Post by agrimstad on 2006-11-01
I've just begun to use Ubuntu (Dapper Drake), my first exposure to Debian-flavored Linux. I've run into an annoying emacs installation problem.

I've been a Slackware user for years and there gnu emacs can be installed with X, without X or both. I prefer both for different circumstances.

In Ubuntu, as far as I can see, when I try to install emacs-nox I am forced to uninstall emacs with X in the process. I don't want to make such a choice. Do I have to? Is there a simple way to deal with this?

Thanks in advance for any clues.  -- al

---

### Post by mbeierl on 2006-11-01
I think you want the emacs (for console) and xemacs-21 packages, not emacs-nox.

Both should install without conflicting each other.

---

### Post by agrimstad on 2006-11-01
Thanks. I'm too old to start messing with xemacs; and I couldn't find anything called "emacs (for console)." That's what emacs-nox is, I thought.

For now, I guess I'll live with running with the -nw option when I don't want X.

---

### Post by agrimstad on 2006-11-05
Since I asked the question, I guess I ought to finish this tread.

I uninstalled the ubuntu emacs packages and installed the emacs-snapshot packages, version 20060707-1~dapper1. They have no problem permitting emacs with and without X to be installed simultaneously.

It seems that Ubuntu has some kind of emacs attitude problem. -- al

---

### Post by krismatth3 on 2006-11-05
emacs -nw


:)

---

