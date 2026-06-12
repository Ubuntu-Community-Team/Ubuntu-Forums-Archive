---
title: "One last thing...."
date: 2005-10-19
forum: General Help
---

### Post by Ocxic on 2005-10-19
I'm trying to configure fstab to mount my newly formated 120BG drive,
I wrote in the line in fstab:
/dev/hdb1      /home/admin/Desktop/120GB Storage    ext3    defaults  0      0
but it says line 10 is bad when i: mount -a in teminal??? what am i doing wrong?

thanks in advance

---

### Post by Pablo_Escobar on 2005-10-19
"120GB Storage" is a problem.
As i recall You need to tell Your comp that there is a space between 120GB and storage.
It should look like "120GB\\ Storage" as I recall (or maybe only one "\").
Someone correct me if I'm wrong.

---

### Post by Ocxic on 2005-10-19
[QUOTE=Pablo_Escobar]"120GB Storage" is a problem.
As i recall You need to tell Your comp that there is a space between 120GB and storage.
It should look like "120GB\\ Storage" as I recall (or maybe only one "\").
Someone correct me if I'm wrong.[/QUOTE]

It still doesn't work, is there anything to do with spacing the line out properly
or should i remove the space in "120GB Storage"?

---

### Post by Pablo_Escobar on 2005-10-19
Try loosing the space.
And do You "sudo" while mounting ?

---

### Post by Ocxic on 2005-10-19
[QUOTE=Pablo_Escobar]Try loosing the space.
And do You "sudo" while mounting ?[/QUOTE]
 yes i do sudo

and removing the space worked, Thanks for the help

---

### Post by Ocxic on 2005-10-19
ok now, I have edited my fstab to mount my new HD and it worked, almost... now it's there mounted, but i cannot write to it at all i can only view it here is my fstab line for the drive:
/dev/hdb1       /home/admin/Desktop/120GB_Storage   ext3    defaults   0      0
is there something i missed?

---

