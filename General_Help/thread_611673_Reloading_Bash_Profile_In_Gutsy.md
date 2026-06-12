---
title: "Reloading Bash Profile In Gutsy"
date: 2007-11-13
forum: General Help
---

### Post by kule on 2007-11-13
Hi There,

I've been setting up a virtual host with Gutsy over at slicehost - its been a breeze to setup albeit one minor issue.  I'm trying to figure out why the after updating the .bash_profile the following command doesn't work:

source ~/.bash_profile

As far as I can tell this used to work with Feisty but not on Gutsy.  If I log out of the ssh session and log back in it loads the profile changes correctly - but I can't seem to do this within the current session.

Any ideas?

Many Thanks
Luke

---

### Post by kule on 2007-11-16
Managed to figure out the .bash_profile issue. All you need to do source the .bashrc file instead to update the settings. i.e.

source ~/.bashrc

From what I've read the .bash_profile is only read once when you first login (fortunately there's a line in that file to read your .bashrc too). When you run any interactive shells (e.g. screen) only the .bashrc is used.

The default gutsy .bash_profile includes a few lines to include the .bashrc.

Luke

---

