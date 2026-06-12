---
title: "How do i get mkraid to work"
date: 2006-11-18
forum: General Help
---

### Post by CameronCalver on 2006-11-18
Hello i have set up raid and installed all the raid tools but still when i do
```
mkraid
``` it always says ```
bash command not found
```
i really need this to work so i need this mkraid command thanx

---

### Post by der_joachim on 2006-11-19
This may be a long shot, but if you're logged in as a normal user, you'll probably not see anything in the /sbin subdirectory (where the raid tools will probably be).  Does ```
sudo mkraid
``` work?

---

### Post by CameronCalver on 2006-11-20
nope but i tryed another thing i did this lng mdadm command and it created a drive /dev/md0 but i cannot install to it when the installer commes up all there is is /dev/sda and /dev/sdb

---

