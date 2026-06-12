---
title: "Bash command question"
date: 2008-02-28
forum: General Help
---

### Post by uberlube on 2008-02-28
Which command can i use to show me what the address of my dvd drive is? I have a lightscribe dvd burner that no longer work and a regular dvd drive. I am trying to play a DVD in the regular drive but VLC keeps trying to read from the broken one which is hda1

---

### Post by uberlube on 2008-02-28
Bump

---

### Post by uberlube on 2008-02-28
Bump

---

### Post by lloyd_b on 2008-02-28
Try "lshw -C disk".  This should show you every disk (hard drive or CD/DVD) in the system.  Once your find the right entry, look at the "logical name".

Lloyd B.

---

### Post by hhhhhx on 2008-02-28
lshw -c disk

also, like the new avatar uberlube :)

EDIT: too slow :)

---

### Post by lloyd_b on 2008-02-28
> **xhhux said:**
> lshw -c disk

also, like the new avatar uberlube :)

EDIT: too slow :)

That's the way it goes :)

And be aware that it's "dash capital C" - "dash lowercase c" will just get you an error message.

Lloyd B.

---

### Post by uberlube on 2008-02-28
Thanks alot guys! Nothing is more irritating than not being able to find a simple code like this. Glad you like my new Avy! xhhux, even though yours is awsome dont you think maybe it's time for a change to?

---

