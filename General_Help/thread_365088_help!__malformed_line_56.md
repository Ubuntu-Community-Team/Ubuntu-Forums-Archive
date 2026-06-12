---
title: "help!  malformed line 56?"
date: 2007-02-19
forum: General Help
---

### Post by thewatts on 2007-02-19
trying to update stuff such as my video drivers: get this error - tried to go to add/remove, got the same error - and package manager says same thing... please help 

"

E: Malformed line 56 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

"

thanks very much

---

### Post by Spr0k3t on 2007-02-19
Open up sources.list and look at line 56.  You may be able to hash out that one line and everything work like a charm.  Give it a go and post your findings.

---

### Post by kerry_s on 2007-02-19
sud gedit /etc/apt sources.list
set gedit to show line numbers and just scroll down to line 56.

---

### Post by 3rdalbum on 2007-02-19
> **Spr0k3t said:**
> You may be able to hash out that one line and everything work like a charm.

That means, put a hash symbol # at the very beginning of that line.

---

### Post by Spr0k3t on 2007-02-19
> **3rdalbum said:**
> That means, put a hash symbol # at the very beginning of that line.

Yeah, what he said...  8^)

---

