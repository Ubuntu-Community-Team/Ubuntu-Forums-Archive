---
title: "[SOLVED] File Status: Zonbie"
date: 2008-01-09
forum: General Help
---

### Post by Bruce M. on 2008-01-09
What does file Status: Zombie mean?

Considering changing my computer name to:
**Resident Evil P-III "Code Name: CPU"** :lolflag:

No seriously, as seen in the image, I'm not joking.

What does "Zombie" mean?

**EDIT:** Spelling in Title: **File Status: Zombie**

---

### Post by dcstar on 2008-01-09
> **Bruce M. said:**
> What does file Status: Zombie mean?

Considering changing my computer name to:
**Resident Evil P-III "Code Name: CPU"** :lolflag:

No seriously, as seen in the image, I'm not joking.

What does "Zombie" mean?

It means the process was spawned by another process that no longer runs - so the "child" process no longer has a "parent" process controlling it, so it exists as a mindless (and useless) "zombie" just taking up memory in the system.

---

### Post by Bruce M. on 2008-01-09
> **dcstar said:**
> It means the process was spawned by another process that no longer runs - so the "child" process no longer has a "parent" process controlling it, so it exists as a mindless (and useless) "zombie" just taking up memory in the system.

Thanks dcstar ... I notice it's gone now anyway.  :)

---

### Post by TheWizzard on 2008-01-09
thanks. i didnt know that. i always thought that killing the parents also kills the child processess.

---

### Post by mcduck on 2008-01-09
> **dcstar said:**
> It means the process was spawned by another process that no longer runs - so the "child" process no longer has a "parent" process controlling it, so it exists as a mindless (and useless) "zombie" just taking up memory in the system.
Actually that's the definition for orphan process, not for zombie process.. ;)

Zombie process is a process that has completed execution but still has an entry in the process table. So, the process has died but it has not been reaped :D

---

### Post by Bruce M. on 2008-01-10
> **mcduck said:**
> Actually that's the definition for orphan process, not for zombie process.. ;)

Zombie process is a process that has completed execution but still has an entry in the process table. So, the process has died but it has not been reaped :D

In other words, nothing to worry about.  Right!

---

### Post by mcduck on 2008-01-10
> **Bruce M. said:**
> In other words, nothing to worry about.  Right!

Correct. Zombie processes are not running any more, and no memory is assigned to them, so unless you get so many zombies that the process table gets full they are not going to cause any problems. 

(..and if you ever find your system having that many zombies there sure is some bigger problem on your system than couple of 'undead' processes..)

---

