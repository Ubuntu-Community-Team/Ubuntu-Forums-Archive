---
title: "rsync symbolic links with different $HOME trees"
date: 2007-02-05
forum: General Help
---

### Post by reader4 on 2007-02-05
I have a laptop and desktop with Ubuntu.  I keep the two sync'd with rsync, but have a problem with symbolic links.  The directory tree for each home directory is different (since the desktop uses a remote directory), so symbolic links don't point to the right places.  For example, I have a symbolic link for on the desktop that is something like:

/data/desktop/pubs/pub1/figs --> /remote/home/desktop/imgs/figs/pub1/

but on the laptop the target should be:

/home/desktop/me/imgs/figs/pub1

Basically, I need $HOME/imgs/figs/pub1 to be the target on both systems.  So, is there any way to get rsync to recognize the home directory and pass the information this way, or to get the symbolic link to be stored using the $HOME variable instead of the actual directory tree?

---

