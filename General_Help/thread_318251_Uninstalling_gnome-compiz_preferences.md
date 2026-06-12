---
title: "Uninstalling gnome-compiz preferences?"
date: 2006-12-13
forum: General Help
---

### Post by pissedoffdude on 2006-12-13
I have been using compiz for quite some time but the other day I decided to install the gnome-compiz preferences. As soon as I ran the command gnome-compiz preferences my window borders have disappeared.  I also got a GL Desktop Icon (uses the command gnome-compz preferences) on my system>preferences.  Does anybody know how I can uninstall it?  Any help will be greatly appreciated.  BTW I have tried beryl but I have been happier with compiz's stability.

---

### Post by pissedoffdude on 2006-12-13
Are there any files that i can delete to fix this problem. I have attached the tar.gz that i used to install it.

---

### Post by justinjstark on 2006-12-14
> **pissedoffdude said:**
> Are there any files that i can delete to fix this problem. I have attached the tar.gz that i used to install it.

The make file probably has an uninstall target.  So,

```

tar xfvz filename.tar.gz
cd filename
make uninstall

```

Let me know if that works.

---

