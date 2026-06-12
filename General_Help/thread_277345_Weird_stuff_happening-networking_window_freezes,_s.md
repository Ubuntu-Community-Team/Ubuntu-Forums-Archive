---
title: "Weird stuff happening-networking window freezes, sudo gedit doesn't work"
date: 2006-10-14
forum: General Help
---

### Post by dmb on 2006-10-14
Hello, for some reason, some weird things have been happening and I haven't been able to figure out what or why this is ha penning. To start off, I can't seem to run the Networking program.  I try running it, the window comes up, but its a non responsive windows which is white with no content in it. Then, when I try to run sudo gedit or even gedit after running su, gedit just never comes up. Also, when I try to stop bind, it just hangs:
 * Stopping domain name service. 
Speaking of that, the dns server just seems to have stop working as well and I have to use my isps. Can someone please help me! Im sure all of these problems are related, because they all happened towards the same time. I tried running fsck and that found no errors, so no corrupt files. Please help me, thanks!

---

### Post by taurus on 2006-10-14
```
gksudo gedit
```

---

### Post by dmb on 2006-10-14
nope, that doesn't seem to work, that just makes the gedit look like the gnome-networking window, white and non responsive.

---

### Post by dmb on 2006-10-14
found the solution, for some reason, lo wasn't comming up do to a weird problem in /etc/network/interfaces. Once i got lo going again, it starting working.  Thanks for the people on irc for helping me out.

---

### Post by fdoving on 2006-10-15
You're welcome :)

---

### Post by foxer on 2006-10-15
> **dmb said:**
> found the solution, for some reason, lo wasn't comming up do to a weird problem in /etc/network/interfaces. Once i got lo going again, it starting working.  Thanks for the people on irc for helping me out.

What did u change in /etc/network/interface to make lo load?

---

