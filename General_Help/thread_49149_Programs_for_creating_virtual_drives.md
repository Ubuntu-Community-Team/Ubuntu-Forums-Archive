---
title: "Programs for creating virtual drives?"
date: 2005-07-15
forum: General Help
---

### Post by soul on 2005-07-15
I'm looking for something to mount an image file to without actually burning a copy. What are some programs for this that are fairly simple to use? I'm mostly looking for ones I could get though apt-get or the synaptic package manager since I'm fairly new to linux and I haven't been having much luck with installing programs by other means. Thanks.

---

### Post by Juergen on 2005-07-15
The funtionality to mount iso files to a directory is 'built in'.

Here's a small HOWTO: 
[http://www.frozenblue.net/tools/howtos/?v=iso-mount](http://www.frozenblue.net/tools/howtos/?v=iso-mount)

Change the directories as you need and consider that you need to be root, that is, put a 'sudo' before each command - if you mount to a directory in your $HOME, you probably don't need to be root (but I'm not sure ATM).

---

