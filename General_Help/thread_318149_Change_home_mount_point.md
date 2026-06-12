---
title: "Change /home mount point"
date: 2006-12-13
forum: General Help
---

### Post by klayn on 2006-12-13
I have my /home directory mounted on a different partition than the rest of my system, and now I decided I want it mounted on the same partition as the rest of my system (I know, I know...). I know I need to edit /etc/fstab to do this, but I want to make sure I do it without destroying my entire system. Would deleting the line that specifies the /home mount point from the file be enough, or is there something else I have to do?

Any help is appreciated...

---

### Post by taurus on 2006-12-13
If you just delete an entry for /home in /etc/fstab, then you cannot log in because there is no /home anymore!!!  Therefore, you need to boot with the LiveCD, copy /home from original partition to new /home under/, remove an entry for /home in /etc/fstab, and reboot...

---

### Post by bodhi.zazen on 2006-12-13
> **klayn said:**
> I have my /home directory mounted on a different partition than the rest of my system, and now I decided I want it mounted on the same partition as the rest of my system (I know, I know...). I know I need to edit /etc/fstab to do this, but I want to make sure I do it without destroying my entire system. Would deleting the line that specifies the /home mount point from the file be enough, or is there something else I have to do?

Any help is appreciated...

first move /home to your root partition.

Then comment out the /home line in fstab (in case you need it) by adding a # at the front of the line:

> **[color=darkred]#[/color]**/dev/hdxy /home auto ......

---

### Post by klayn on 2006-12-15
Worked like a charm, thanks!

---

