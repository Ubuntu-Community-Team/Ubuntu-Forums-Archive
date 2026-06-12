---
title: "I've broken my terminal"
date: 2007-11-15
forum: General Help
---

### Post by sipickles on 2007-11-15
Hi,

I am pretty new to all this, but beginning to get the hang of it.

Unfortunately, I've been fiddling, and now my gnome terminal has been affected.

I used to be able to use the arrow keys to move through a line of text, and use up arrow to recall previous commands.

Now up arrow prints this:

^[[A

What have I done? All I was trying to do was create my own terminal profile. I tried reinstalling using synaptic but its still the same.

Also:

My prompt is now $ instead of simon@ubuntu-laptop $

Thanks

Si

---

### Post by taurus on 2007-11-15
Did you change your ~/.bashrc or ~/.bash_profile?

---

### Post by sipickles on 2007-11-15
I was fiddling with that too yes!

I thought I'd put it back in USERS>EDIT>ADVANCED to

/bin/sh


Wjhat should it be?

---

### Post by kpkeerthi on 2007-11-15
/bin/bash

---

### Post by taurus on 2007-11-15
Try removing whatever you edited and restart gnome-terminal again.  Or you may even need to log out and back in.

---

### Post by sipickles on 2007-11-15
Genius! Solved!

Thank you very much!

Can't guarantee I won't keep fiddling tho ;)

---

