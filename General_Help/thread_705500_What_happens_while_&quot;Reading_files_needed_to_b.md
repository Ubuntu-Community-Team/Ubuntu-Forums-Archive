---
title: "What happens while &quot;Reading files needed to boot&quot; ?"
date: 2008-02-23
forum: General Help
---

### Post by Adnarim on 2008-02-23
Hi,
while my system is booting the most time-consuming thing is "Reading files needed to boot". About 5 or 6 seconds just on this screen. What happens in this time? Which scripts are executed? And of course can I reduce this time?

greets

---

### Post by DieB on 2008-02-25
well, while booting enter grub menu with [Esc], move with the cursor to the appropiate entry and type [e] (for edit), then switch with the cursors to the line starting with "kernel" and once again type [e] now delete "splash" and "quite" press [enter], so you return press now [b] (for boot) and you get everything your kernel does while booting.

P.S. the changes are not persistent.

---

### Post by Iowan on 2008-02-25
Yes, you can probably reduce startup time - there's a "How-to Optimize..." around here somewhere.  You can turn off (actually, just don't start) processes you don't need anyway.

---

