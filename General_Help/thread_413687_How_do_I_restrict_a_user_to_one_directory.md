---
title: "How do I restrict a user to one directory?"
date: 2007-04-19
forum: General Help
---

### Post by rich.bradshaw on 2007-04-19
I have a folder in my home folder ~/ants, which I would like to let another user access via ssh. I have them set up as a user with this directory as their home dir, but I don't want them to get access to the rest of my machine. How do I lock them in this directory and it's subdirectories?

Rich

---

### Post by rich.bradshaw on 2007-04-19
bump?

Is chroot the thing I need? How do you use it? Can't find much info about what I want to do...

---

### Post by stimpsonjcat on 2007-04-19
yes, you need chroot. I haven't done it myself, but there's a howto on [howtoforge]("http://www.howtoforge.org/chrooted_ssh_howto_debian")

hope that helps..

---

