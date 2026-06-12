---
title: "can't clear files in wastebasket"
date: 2008-04-24
forum: General Help
---

### Post by stu2004 on 2008-04-24
hi,

I have some files in the wastebasket that are owned by my user. i can't remove them though.  

How can i clear them? 
where are they actually on my machine?

thanks

---

### Post by retrow on 2008-04-24
The deleted files are under ~/.Trash

If you had logged in as root (or used sudo) and/or had deleted them from a different partition, they could be under .Trash on that particular partition. You may have navigate to the appropriate .Trash directory and then delete them. If if denies permission, then you'll have to sudo to remove them.

---

### Post by chrisccoulson on 2008-04-24
What Ubuntu version are you using? If it's Hardy then the deleted files are no longer in ~/.Trash. They are in ~/.local/share/Trash as per the Freedesktop spec.

---

### Post by soxs on 2008-04-24
simplest way to find any trash:
```
sudo updatedb
locate .Trash
```
and simply cd to the depending directory and delete all subfolders of .Trash* folders

---

### Post by retrow on 2008-04-24
Thanks for the heads-up and info about the new location of Trash, Chris.

---

