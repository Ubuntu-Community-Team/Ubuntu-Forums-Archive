---
title: "Looking Glass error during install!"
date: 2007-11-30
forum: General Help
---

### Post by doctorgreg on 2007-11-30
Hey there.  I installed looking glass and i get this error in the terminal.

/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

It shows up in the sessions menu but thats it.

---

### Post by Ashesz on 2007-12-20
Same problem here, as soon as I found a solution i'll post it. Now let's hope I'll find one. :)
For the record, I'm using the latest ATi driver (catalyst 7.11) and OpenGL 1.2 and have Compiz Fusion switched off.

**edit

I found the solution, partially in another topic on this forum.

All you need to do is to make a file in the "/bin" directory called "arch" containing just this line "uname -m"
How to:

In terminal:

$ cd /bin
$ sudo gedit
 - This opens the text editor -

In the text editor:
add the following line:

uname -m

Save the file as "arch" and close the text editor.
Close terminal

Then reinstall Looking Glass and reboot.

That did the trick for me, and I do hope it works for you to.

---

### Post by nutz on 2008-01-16
Same error here. AMD64 with Nvidia...

---

