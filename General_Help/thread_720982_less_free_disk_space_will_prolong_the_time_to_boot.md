---
title: "less free disk space will prolong the time to boot?"
date: 2008-03-10
forum: General Help
---

### Post by chunchengch on 2008-03-10
I heard that less free disk space will prolong the time to boot, is it correct? thanks!

---

### Post by astrotech226 on 2008-03-10
Less disk space should not affect the amount of time to boot.  Unless you run out of disk space where certain things happen during the boot process.  Like in the /var directory.  If that happens, it could prolong the time to boot indefinitely.  :)

---

### Post by chunchengch on 2008-03-10
Thanks!

I don't think less free disk space will affect the boot time either, that should be a misunderstanding of Linux.

---

### Post by ibuclaw on 2008-03-10
In a small way this is related to fragmentation in Linux.

Which the answer is, in theory, yes.

Though we are talking about huge drives (80GB+) being squeezed with as much data as possible (say the partition only has 400MB left.)

As long as you are sensible, It will never happen.

And before someone starts going off into it. No, Linux doesn't fragment files that easily.

Unlike $indows that treats the filesystem as a line, and packs everything back-on-back to each other. Causing ample of problems and fragments everywhere.
Linux treats it more as a circle, scattering files all over the partition, leaving ample round for files to grow and NOT fragment.

Though as the filesystem grows and space runs out (as I said before, this happens with a huge filesystem being squeezed heavily), fragments will begin to happen, and quite possibly, they may just slow down the boot process.

Again, this is in theory. I'm sure linux (just as all other UNIX-based systems that are built for multiple users) have their own way to speed up and optimise file usage and loading, even if it is fragmented. (Again, unlike $indows).

So to turn the answer on top of itself, I could 90% positively say:
>  "No, less free disk space will not prolong boot time, but that doesn't mean that a filesystem being pushed to its limits won't" 

Hope that helps.

Iain

[EDIT]
Just thought I may point out, you may actually find that Linux will infact SPEED UP in loading/booting times the more frequently it is used!

---

