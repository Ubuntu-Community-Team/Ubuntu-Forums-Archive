---
title: "How do I acces other folders than /media and /home"
date: 2007-03-07
forum: General Help
---

### Post by airix on 2007-03-07
Hello

I'm new to Ubuntu (and Linux) and I have a very frustrating experience concerning this aspect: I tried burn some stuff which is on my windoze mounted_and_accesible partition but in k3b I can see only /media and /home. How do I turn this off?
and other applications, via file--> open--> browse for ... I can see only /media and /home, although via shell I can have acces everywhere as the same user (read at least)

big thank you

---

### Post by chavo on 2007-03-07
The reason you can't see the files in a file browser or the open file dialog is they are hidden by default. There is a file in / called .hidden, in this file is a list of files and folders that should be hidden by the browser or file dialog. The command line programs don't use the .hidden file thing.

However your windows directories should be mounted under /media anyway., shouldn't they. Well if they aren't you can either edit the .hidden file as root, or just type the directory directly into the address bar of the file dialog.

---

### Post by ubu fubar on 2007-03-07
ctrl+h

in-a-nautilus-window-shows-the-hidden-files.

(Sorry-for-formatting,-broken-space-key)

---

### Post by airix on 2007-03-07
now that was an constructive quick answer problem solved :) 

:popcorn:  4 2 of u

---

