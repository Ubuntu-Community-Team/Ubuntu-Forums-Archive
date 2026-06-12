---
title: "Format hard drive"
date: 2008-01-13
forum: General Help
---

### Post by timboellis on 2008-01-13
I just put in a new hard drive 250 gig, installed Ubuntu gabe the main OS 60 gig an left the rest howver all i can see is the other partition as 60 gig with a folder lost and found I can do nothing with .

Any suggestions

---

### Post by insane_alien on 2008-01-13
so ehh, whats the problem?

if your asking about the lost and found folder, it is from the filesystem and is used when it repairs itself after a crash or something that it can't fix without some data loss. hopefully it will never be used.

---

### Post by timboellis on 2008-01-13
Well no i need to delete it and format it it says it is 60gig but should be 189 gig

---

### Post by timboellis on 2008-01-13
here is a screen shot if this helps
[IMG]http://www.piggywig.co.uk/GParted.jpg[/IMG]
Its the SDA2 I want to store my MP3's

---

### Post by Keith Hedger on 2008-01-13
if you look at the mount points you will see you have your system installed on sd2 NOT sda1 so you will have to move your system to sda1 (probably a fresh install will be best)

---

### Post by timboellis on 2008-01-13
Nightmare just done a fresh install as well

---

### Post by timboellis on 2008-01-13
Thanks for that at least I know why it would nto let me format it :)

Will try to resize it if it will let me

---

### Post by Keith Hedger on 2008-01-13
sorry should have suggested resizing first, it should be ok if you boot from the live cd but resizing and moving a partition can actually take longer than doing a backup/restore or a fresh install, well have fun! :)

---

