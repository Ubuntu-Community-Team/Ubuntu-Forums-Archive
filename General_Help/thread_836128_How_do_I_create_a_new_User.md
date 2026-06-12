---
title: "How do I create a new User?"
date: 2008-06-21
forum: General Help
---

### Post by G.Warrior107 on 2008-06-21
Okay, the problem here is that I somehow managed to break something about my first user, which I tried everything everyone said, it's apparently a broken X11 something or other, but anyway, I figured if what everyone else says doesn't work, why not create a new one?  I had made an account for someone else, but the problem is it seems to not have permission to do anything, so how do I create a user that has all those nice permissions of the first user created during installation?

---

### Post by hal8000 on 2008-06-21
Assuming youve broken Gnome, from a terminal:

sudo useradd -m -G adm, dialout, cdrom, floppy, audio, dip, video, plugdev,
fuse, lpadmin, admin -s /bin/bash tux

This creates user tux with default Ubuntu groups, then
passwd tux (userpassword)

to set tux's password, dont use brackets. Also change "tux" to desired username. The -s sets the shell to bash.

Hope that helps.

---

### Post by G.Warrior107 on 2008-06-21
Thanks, though before I try that, I didn't break Gnome I don't think, because I'm pretty sure I've got KDE on my Kubuntu, does that in any way effect if what you said would work?

~<>~
EDIT:
~<>~
I can get to a Root Terminal thing (I think it says it's root) if I boot up Kubuntu in some recovery mode or something, and I can get my old broken user's Terminal going by starting it in that (not sure what it's called, but I found something that does that) so I can get to a Terminal that does that, just need to know if that's right for KDE...

By the way, if anyone knows, after that how do I get rid of the old user that doesn't work?

---

