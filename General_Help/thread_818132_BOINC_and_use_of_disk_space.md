---
title: "BOINC and use of disk space"
date: 2008-06-04
forum: General Help
---

### Post by Cadmus on 2008-06-04
I've got a machine with a small root partition (~10GB) and an LVM (any size I like) for providing space to apps as they need it.

I'd like to put BOINC on it but I can't seem to find out where it stores work units on Ubuntu so I can mount a piece of the LVM in the right position.

Can anyone help me a little on the anatomy of the Ubuntu BOINC installation.

---

### Post by Kevbert on 2008-06-04
By the look of it they are saved in /var/lib/boinc-client(according to the messages tab).  In this directory there are two further directories called slots and projects which I can't get into as they are locked and I don't have the privileges to open them (at least in Nautilus)!  The data sizes I have are currently 125Mb in total according to disk stats.  Projects are Predictor, Seti, lhca, malariacontrol and rosetta.
When you install do this from terminal as it can be a pain to connect up the first project using
```
sudo apt-get install boinc-client boinc-manager
```

---

### Post by Cadmus on 2008-06-04
Thanks for the quick response, I won't be needing boinc-manager (as I understand it) as I'm on a gui-less server and you can attach to projects using boinc-cmd which is in boinc-client.

---

### Post by Cadmus on 2008-06-04
Took a look in /var/lib/boinc-client and what you said makes sense, I've not attached to anything and I don't have those two directories, so they must be produced on demand when you receive your first work units.

---

