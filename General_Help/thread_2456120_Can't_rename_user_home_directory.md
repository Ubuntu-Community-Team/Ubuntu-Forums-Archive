---
title: "Can't rename user home directory"
date: 2021-01-04
forum: General Help
---

### Post by veloo on 2021-01-04
I have to rename my user and consequently the home directory in /home. I have installed ubuntu with zfs whole disk, and it seems the user home directory is a zfs mount. How can I rename the user home directory? Thanks

---

### Post by TheFu on 2021-01-04
I don't know the zfs answer, sorry.

You do know that the HOME directory name and the account username are not tied together, right?
It is controlled by the passwd entry.

Just providing the option assuming that learning ZFS to address this isn't easy.

---

### Post by veloo on 2021-01-05
i know how to change home directory, and i did that. but as per op, ubuntu created zfs mounts for each user. when it didn't find the old home directory, it creates that old home directory and mounts into that old directory ignoring the directory in passwd.

---

### Post by TheFu on 2021-01-05
> **veloo said:**
> i know how to change home directory, and i did that. but as per op, ubuntu created zfs mounts for each user. when it didn't find the old home directory, it creates that old home directory and mounts into that old directory ignoring the directory in passwd.

What I'm saying is that you don't need to change the HOME directory, just change the username in the 3 files where needed.
[LIST]
[*]passwd
[*]shadow
[*]group
[/LIST]
Leave the HOME directory were it was.

---

