---
title: "Adding a terminal with a customization"
date: 2007-12-31
forum: General Help
---

### Post by ottothecow on 2007-12-31
I'm in the process of moving a system from FreeBSD to ubuntu-server.  What I am trying to do is add another tty terminal with a custom start script instead of getty.

In FeeBSD, I do this from a scrpt with
```
echo "ttyv8   \"/usr/local/bin/custom-script\"       xterm   on  secure" >> /etc/ttys
```
This adds a line to /etc/ttys which enables an extra terminal on ctrl-alt-f8 (since f7 is used for x)

It seems like in ubuntu, each tty has it's own file with a lot more information so I can't quite figure out how to emulate this behavior.

I'd be fine with reusing tty6 or something but I am unsure about how to give it a custom script.

Thanks for the help

---

### Post by ottothecow on 2007-12-31
I know that this would be simply editing a line in inittab but ubuntu no longer uses it.

with upstart and the files in /etc/event.d I can't figure it out.

---

### Post by ottothecow on 2008-01-01
bump

any ideas?

---

### Post by ottothecow on 2008-01-01
*bump* again

hoping someone can help as it was obviously someone's brilliant idea to move from the lovely inittab to upstart

---

### Post by ottothecow on 2008-01-02
still hoping for some help adding a terminal like with inittab

---

### Post by sumguy231 on 2008-01-02
I don't understand upstart in the slightest either, but if you haven't already you could try thumbing through the documentation in /usr/share/doc/upstart-compat-sysv, which supposedly explains how to do common sysvinit tasks in upstart.

---

### Post by ottothecow on 2008-01-03
thanks, in that documentation it looks like I can add another tty by copying the already existing ttyNN file to another name (ttyNN+1 or whatever) and making my changes.  It should then work on reboot.

Not quite as elegant as inittab, especially since I can't just echo a line to the file and have a new terminal.

---

