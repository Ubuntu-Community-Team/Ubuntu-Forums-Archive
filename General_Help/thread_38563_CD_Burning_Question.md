---
title: "CD Burning Question"
date: 2005-06-01
forum: General Help
---

### Post by makisupa123 on 2005-06-01
I have an ATAPI burner connected to my laptop via USB.  Without an entry in the fstab, pmount seems to work as its supposed to.  I can burn with k3b, but this is a less than eloquent solution.  Is there a way to burn with gnomebaker without an entry in fstab (specifying a mount point)?

The only way i could get a entry in the "computer" folder where the burner is identified as an "external CD Burner" is have an fstab entry in for both sr0 and scd0.  This creates some problem and is obviously not how this should be done.  Is there a way to set up a symbolic link or some way to tweak pmount and the fstab so that I get this when I plug the burner in?  Any suggestions as to what should be the mount point?


Thanks in advance for the help.

Mak.

---

### Post by ad noiseam on 2005-09-05
I think I have more or less the same issue.
I am using an external CD / DVD drive. I can read from it without any problem and without having to do anything, but Gnomebaker doesn't want to write to it. It recognizes it automatically (even as a DVD burner), but tells me that there is no entry point for it. Now, I can put something in the fstab for the drive, but this is getting slightly cryptic to me. How do you I know what I should put there?

---

### Post by frodon on 2005-09-06
Don't expect gnomebaker to be as complete as k3b, it isn't. If you can burn with k3b why do you want to use gnomebaker which not include as many functionalities as k3b ?
I also try graveman, i got some problems with dvd-rw with both graveman and gnomebaker but never with k3b, that's why i use k3b even if i'm using gnome.

---

