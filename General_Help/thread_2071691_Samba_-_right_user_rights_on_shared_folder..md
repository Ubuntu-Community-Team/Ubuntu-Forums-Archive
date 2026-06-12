---
title: "Samba - right user rights on shared folder."
date: 2012-10-16
forum: General Help
---

### Post by marjoh05 on 2012-10-16
Hello!

I've made a shared folder, and i need it to be write only for guests.

By that i mean guest can move files to the shared folder, but not open/remove/config files in the shared folder.

At first i tried:
browsable = no
guest ok = yes
writable = yes

didnt work.

Thanks.

---

### Post by marjoh05 on 2012-10-16
Lunch bump

---

### Post by marjoh05 on 2012-10-16
Got it!

Sulotion:
read only = No
create mask = 0333
directory mask = 0333
guest ok = Yes

But i can still delete folders and files as a guest!

Anyone got a line to add like i only can add folders and files and not delete any?

---

