---
title: "Call me dumb"
date: 2007-01-22
forum: General Help
---

### Post by MT_Head on 2007-01-22
I seem to have this problem. How to get to a different dirictory.
trying to setup lightscribe.
Have installed Alien and downloaded the 2 files to my desktop. Its called tret.
But can't find it or my files in the termial.
This has been a major problem in keeping me in Linux. things that should work don't for me.
Can someone please tell me how to do this. 
Thanks for listening to a dumb person.

---

### Post by enopepsoo on 2007-01-22
Files usually download by default to the Desktop.  Open a terminal and type
```
cd Desktop
```
It is case sensitive, so make sure to capitalize the 'D.'

The easy way to install alien is through the repositories though.  Just type
```
sudo apt-get install alien
```
and that will do it, or if you want to avoid the CLI, just use the Synaptic package manager under the admin menu.

---

