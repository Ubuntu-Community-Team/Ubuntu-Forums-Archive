---
title: "Lubuntu 18.04 Can't install Doom Emacs"
date: 2020-11-22
forum: General Help
---

### Post by steve234 on 2020-11-22
Afternoon, 

My nOOb self wants to try out org-mode, so I've ssh'd in to a tmux session on an old laptop running 18.04 from termux on my android phone (because I have a baby strapped to me having a nap).

I've cloned the doom git and tried to install, but my Emacs version is too low.

I've followed the instructions on the Ubuntu guide here for installation of 26 and 27 via a ppa but have run out of ideas: [https://github.com/hlissner/doom-emacs/blob/develop/docs/getting_started.org#on-linux](https://github.com/hlissner/doom-emacs/blob/develop/docs/getting_started.org#on-linux)

The 27 install seemed to go well. However, the install of doom still reports I have Emacs 25- which ain't good enough.

Installing 26 from the ppa just throws errors. Plus, the two depends emacs git ripgrep an fd-find say "not available".

Any help will be appreciated.

---

### Post by steve234 on 2020-11-23
Fixed by autoremoing Emacs25 (rather than "Emacs")

---

