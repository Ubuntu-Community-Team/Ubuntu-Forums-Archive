---
title: "How do I remove startup programs from console"
date: 2006-10-29
forum: General Help
---

### Post by alek66 on 2006-10-29
I added beryl programs to startup programs, and it doest work fine, i want to get them out, but i cant access via X server. 
How do i erase programs from the session startup programs from console?

---

### Post by dr.lnx on 2006-10-29
let's try to install and use sysv-rc-conf

---

### Post by .t. on 2006-10-29
I assume you are running Ubuntu.

Perhaps deleting ~/.gnome2/session might do the trick...

---

### Post by .t. on 2006-10-29
Oh, and delete the related files in ~/.config/autostart (if you're not sure, delete the whole directory: "rm -r ~/.config/autostart").

---

