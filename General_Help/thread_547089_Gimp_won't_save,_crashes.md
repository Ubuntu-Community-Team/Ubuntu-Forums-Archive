---
title: "Gimp won't save, crashes"
date: 2007-09-09
forum: General Help
---

### Post by wyth on 2007-09-09
Gimp doesn't want to save anything for me anymore.  I've purged it and reinstalled it a few times, with the same results.

Here's what happens:

I open an image, do my edits, then go to "Save As" and try to save it as a png/jpeg/name-your-file-type.  Then nothing happens.  It just hangs.  It never asks if I want to export it as a certain file.  After a little bit, I hit cancel, to no effect.  Eventually I have to kill Gimp.

I really kind of need Gimp.  In the meantime I'm using Krita, but I'd rather use Gimp.  Anyone have any ideas?

(And why doesn't Gimp just have an Export dialog in the menu?)

---

### Post by Alex1770 on 2007-09-09
That's odd. Have you tried a really simple operation, like creating a small image then saving it?

If that doesn't work and the gimp is a clean install then I'm guessing (without much certainty) that the problem isn't with gimp itself.

What happens if you look at the ends of the message logs (/var/log/messages, /var/log/kern.log, /var/log/syslog) while gimp is in the hung state? Just wondering if there are records of failures to access the filesystem or suchlike.

---

### Post by wyth on 2007-09-09
Ah, nice suggestions.  But the messages didn't show anything, and the same problem occurred.  I'm thinking of just re-installing; there's a few little hassles I'd like to take care of.  I ripped KDE off this and went back to Gnome, and since then I've had some little things going on.  

But thanks, I appreciate it.

---

### Post by wyth on 2007-09-10
I re-installed, and Gimp is working beautifully.  I have a feeling it had something to do with a hack I used in KDE to make GTK apps use a KDE file menu option -- I forgot about it.

So consider this problem
SOLVED.

---

### Post by kooldino on 2008-03-04
I just made an image only to have the save dialog never fully draw in.  the program responds perfectly otherwise, but refuses to draw in the save screen.

See attached.

---

### Post by kooldino on 2008-03-06
I ended up doing a duplicate of the image, and the save dialog worked for that one.  :confused:

---

