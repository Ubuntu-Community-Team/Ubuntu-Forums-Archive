---
title: "fdisk -l shows nothing"
date: 2006-12-30
forum: General Help
---

### Post by jordilin on 2006-12-30
When I type ```
fdisk -l
``` it should show all the partitions in my hard disk, but I get nothing, Is this a bug? Do you get the same?

---

### Post by angkor on 2006-12-30
Hmmm, strange, didn't realize that the fdisk -l command needed root privileges. It works with sudo

---

### Post by jordilin on 2006-12-30
> **angkor said:**
> Hmmm, strange, didn't realize that the fdisk -l command needed root privileges. It works with sudo

Oh, yes, it's really weird, it must be run with sudo to get the results. It must be a bug.

---

### Post by taurus on 2006-12-30
Personally, I don't think it's a bug.  You need to be root to view your harddrive or manipulate it...

---

### Post by jordilin on 2006-12-30
> **taurus said:**
> Personally, I don't think it's a bug.  You need to be root to view your harddrive or manipulate it...

I am not sure, but I wrote ```
fdisk -l
``` in a Debian box without su privileges and it worked. But I'm not sure, I should try it again. In any case, you are right, it should be run as a root user, but Ubuntu runs the command without warning, when it normally does when something needs sudo privileges.

---

### Post by taurus on 2006-12-30
Well, I just checked with our Red Hat Enterprise Linux AS release 4 (Nahant Update 4) server and "fdisk -l" didn't show anything and it didn't complain about not being root either...

---

### Post by jordilin on 2006-12-30
> **taurus said:**
> Well, I just checked with our Red Hat Enterprise Linux AS release 4 (Nahant Update 4) server and "fdisk -l" didn't show anything and it didn't complain about not being root either...

Then, all must be ok. We have learned something new today. :-D

---

### Post by angkor on 2006-12-30
> **jordilin said:**
> Then, all must be ok. We have learned something new today. :-D

Yeah! :)

I've learned that typing sudo isn't a hassle at all. Apparently I'm typing it and entering my password without even realizing it.

---

### Post by ~LoKe on 2006-12-30
Yep, something I ran into a while back, too.  I thought it was odd that it didn't even say that I needed root privileges.  Kind of stupid, really.

---

### Post by melancholeric on 2006-12-30
I tried on a debian etch box, first withour privileges:
bash: fdisk: command not found

Then as root and it worked fine. Strange.

---

### Post by taurus on 2006-12-30
> **melancholeric said:**
> I tried on a debian etch box, first withour privileges:
bash: fdisk: command not found

Maybe because fdisk is in /sbin and /sbin is not on your PATH!!!

---

### Post by melancholeric on 2006-12-30
> **taurus said:**
> Maybe because fdisk is in /sbin and /sbin is not on your PATH!!!

Sometimes I feel like a complete idiot. Wonder why.

---

### Post by taurus on 2006-12-30
> **melancholeric said:**
> Sometimes I feel like a complete idiot. Wonder why.

Don't beat yourself too hard on that.  It happens to all of us, mate.

---

