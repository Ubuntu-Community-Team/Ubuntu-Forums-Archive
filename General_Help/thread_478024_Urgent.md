---
title: "Urgent"
date: 2007-06-18
forum: General Help
---

### Post by shadows85 on 2007-06-18
When I start the computer I get the following error and cant do anything:

Kernal panic -not syncing: VES: Unable to mount root fs on unknown-block(0.0)

How can I fix this?

---

### Post by fdrake on 2007-06-18
i think you shuld use the live cd and try to fix the problem taking a look at the fstab and mtab files on /etc/.

---

### Post by shadows85 on 2007-06-18
> **fdrake said:**
> i think you shuld use the live cd and try to fix the problem taking a look at the fstab and mtab files on /etc/.

I used internet update to get 7.04 the only live cd I have is 6.06.1 LTS so can I anyway?

---

### Post by fdrake on 2007-06-18
i found this link very similar to your case. [http://www.linuxquestions.org/questions/showthread.php?t=468222](http://www.linuxquestions.org/questions/showthread.php?t=468222)
i think you have to change the grub config. when you boot and you see the grub press "esc" and enter the recovery mode. follow the instructions on the link hope it works.

---

### Post by fdrake on 2007-06-18
another one: [http://ubuntuforums.org/showthread.php?t=421479&highlight=kernel+panic](http://ubuntuforums.org/showthread.php?t=421479&highlight=kernel+panic)

---

