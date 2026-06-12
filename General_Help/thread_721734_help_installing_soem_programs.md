---
title: "help installing soem programs"
date: 2008-03-11
forum: General Help
---

### Post by oerllikon on 2008-03-11
hello, ive been using ubuntu for awhile. i run it on an old windows ME computer with 256 megs of ram. i was trying to install samba in terminal, and i got this. i also got this when i tried to open synaptic package manager. any help appreciated, thanks.
[IMG]http://i115.photobucket.com/albums/n309/oerllikon/untitled-1.jpg[/IMG]

---

### Post by kellemes on 2008-03-11
Open a terminal and type..
```
sudo dpkg --configure -a
```

---

### Post by luisromangz on 2008-03-11
Do as the error says, run "sudo dpkg --configure -a" in a terminal.

---

### Post by forestpixie on 2008-03-11
I bet it would make life easier for people if the error actually made some reference to needing to do it as root :)

---

### Post by sajro on 2008-03-11
> **forestpixie said:**
> I bet it would make life easier for people if the error actually made some reference to needing to do it as root :)

True, but in fairness to programmers, dpkg/Synaptic/apt-get/aptitude, etc. are root-privileged programs and thus to some degree assume you are root or know to use sudo. It's relative; it was run by root, so it thinks it's talking to root, who wouldn't need to do anything extra (like sudo) to run the program.

---

