---
title: "Conky Question"
date: 2006-12-17
forum: General Help
---

### Post by dothedorky on 2006-12-17
I searched the forums for a HowTo installation of a conky, and so far it's been running great...

But there is one slight problem, the conky only runs when i type "conky" in the terminal, and when i exit terminal conky disappears. 

Is there anyway to consistently load conky on startup, and have it stay there until the end of my session?

---

### Post by kerry_s on 2006-12-17
Add it to the session startup. To make it stay from terminal is-> conky &

---

### Post by dothedorky on 2006-12-18
noob question, but how do i add it to the startup?

sudo gedit grub, or sudo gedit conky?

---

### Post by cactaur on 2006-12-18
No problem, just go under System>Preferences>Sessions

From there, go to the "startup programs" tab, press add and type in the command ("conky" in your case). Took me a while to finally get this too.

---

### Post by dothedorky on 2006-12-19
thankyou very much, worked perfectly!

---

