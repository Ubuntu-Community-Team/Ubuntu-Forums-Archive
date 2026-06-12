---
title: "Inconsistent disk usage stats"
date: 2008-05-25
forum: General Help
---

### Post by Marco_Polo on 2008-05-25
I'm running Hardy on a Dell 1420n with a 160 GB drive.  The 'df' command and GParted both report > 90% disk usage on sda1.  The disk usage analyzer 'baobab' reports ~50 GB, which seems closer to the amount of files I have stored. (See attached image.)

For a specific application, (to run an older version of root-system with gcc < 4), I have repeatedly altered the partitions.  I added a second partition to install Gutsy.  Then I added a third one to try it with Scientific Linux.  Eventually I got the software running with Fedora 6 installed through VirtualBox OSE.

So I suspect that somehow I've rendered a large portion of the drive unwritable with those partition changes.  Another possibility may be that one of the VMachines I created (I played the same game of try/fail/delete/retry) is claiming the space.  The VMachine that I now use is assigned 60 GB and appears to be using only ~25 GB.

Any ideas on how to track down the usage?

One additional note is that the graphical disk usage analyzer does print "Used 135 GB - available 4.4 GB," even though it only finds 50 GB of storage under the root folder '/'.

---

### Post by Marco_Polo on 2008-05-25
Anyone? - I'm all out of disk space!

---

