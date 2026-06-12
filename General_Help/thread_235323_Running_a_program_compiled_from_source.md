---
title: "Running a program compiled from source"
date: 2006-08-12
forum: General Help
---

### Post by cactaur on 2006-08-12
I just downloaded Flash for Linux (f4l), and installed it using checkinstall. Everything went well, and I can see it in Synaptic, but now, I have no idea how to run it, since there are no icons or anything, can someone help me?

---

### Post by Dr. Nick on 2006-08-13
if you open synaptic and search for it right click it and hit "installed files" look for one in /bin and try and run it.

Are you sure its a standalone program and not a plugin? most standalones make icons

---

### Post by croak77 on 2006-08-13
Pretty sure the executable is f4l. Run it from a terminal, just type f4l or from a run dialog, Alt-F2.

---

### Post by cactaur on 2006-08-13
I looked in the Installed Files, and all I got was this
> /.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/f4l-0.2.1
/usr/share/doc/f4l-0.2.1/COPYING


And that file is just the copyright. I'm not sure if something went wrong with checkinstall, but apparently something's not right. I tried running from the terminal, but it says it can't find the command. Maybe I should try reinstalling it.

---

### Post by Dr. Nick on 2006-08-13
yeah, that doesnt look right, you can try to reinstall the checkisntall package, or you may have to recompile and rebuild it again.

---

