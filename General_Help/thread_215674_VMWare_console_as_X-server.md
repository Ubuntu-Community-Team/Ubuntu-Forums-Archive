---
title: "VMWare console as X-server"
date: 2006-07-14
forum: General Help
---

### Post by Unknowndeepness on 2006-07-14
Hello there.

Ive installed VMWare, and a windows 2000 virtual machine.
Now i wonder if i can start computer into a console (not start the x-server), and start the virtual machine from there, and then start an x-server that just connects to VMWare (No KDE or Gnome or whatever running in the backround).

Is this possible?

---

### Post by .t. on 2006-10-14
It may be possible with a lttle hacking about, but if you want to do this, then why are you running Ubuntu?

---

### Post by Unknowndeepness on 2006-10-14
Well, there is just a lot of software, windows-only software, that i like to run. And having X and VMWare running at the same time takes alot of CPU.. :/

---

### Post by .t. on 2006-10-14
Actually, I think you'll be pleasantly surprised! VMWare doesn't emulate anything. It merely runs the XP (or whatever virtual machine you have running) instructions in a "sandbox" on the host CPU. This means it doesn't really use much more processor time than running natively!

---

