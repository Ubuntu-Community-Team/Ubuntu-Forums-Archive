---
title: "I kinda, sorta...deleted /usr....."
date: 2007-06-30
forum: General Help
---

### Post by Johnny K on 2007-06-30
[please take this moment to get all the laughing out]

Moving on...

So there was a protected folder on my Desktop called usr. I wanted to delete it, so I did:
```
cd ~/Desktop
sudo rm -r /usr
```
When I realized what I had done it was too late. Who would have thought that one forward slash could cause such a problem...

So what do I do now? Is there any way to undelete /usr, or is a fresh install my only option? If latter, could anyone please run me through the process of backing everything else up to CD via terminal, if that's even possible?

**_Summary:_**
**:~/Desktop$ sudo rm -r usr** = good
**:~/Desktop$ sudo rm -r /usr** = bad

---

### Post by meatpan on 2007-06-30
This is the kind of mistake that many of us have made after a very LONG day.
All well, it builds character ;)

Unless you make regular disk backups, I think you are going to need to repair the OS installation.  Use your install disk.  If you used a separate partition for your home directory, there shouldn't be a need to re-write all of your files.

---

### Post by Technophobia on 2007-06-30
maybe rm should just be rerouted to .trash

the world isn't perfect

---

### Post by Adramelech on 2007-06-30
I know this software can help 

[R-Studio]("http://www.r-studio.com/")

---

