---
title: "Assigning users' home directories to different disks"
date: 2018-03-01
forum: General Help
---

### Post by brendand2 on 2018-03-01
I would like to assign each user's home directory to a different disk. I can think of three ways offhand.
[LIST]
[*]assign home directory upon account creation
[*]mount each user's home directory in fstab
[*]symlink each each user's home directory
[/LIST]

Is there a best practise? The third way seems like the worst but it is the only way that ```
ls /home
``` would behave as expected.

---

### Post by vanadium on 2018-03-01
> 
Is there a best practise? The third way seems like the worst but it is the only way that
Code:

ls /home

would behave as expected. 

I don't know what you are expecting here. The symlink approach where you link to each user's home folder on a different storage would work well and would by far be the simplest. Also mount bind in fstab will work. These are the two options to maintain a conventional file structure. Your first option is also valid, but would lead to non standard locations for the user home directories.

---

