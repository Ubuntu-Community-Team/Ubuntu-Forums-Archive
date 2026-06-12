---
title: "Trash owned by root in XFCE"
date: 2006-12-19
forum: General Help
---

### Post by Kimm on 2006-12-19
I have some trash in my wastebasket that is owned by root... deleting them from Thunar doesnt work, and I cant find the folder that XFCE stores the trash in to delete it from terminal...

I even tried running chown -R kim:kim /home/kim

but that didnt seem to work...

---

### Post by raul_ on 2006-12-19
Maybe 
```

sudo thunar

```

and deleting from there? Or that's what you've tried?

---

### Post by Kimm on 2006-12-21
> **raul_ said:**
> Maybe 
```

sudo thunar

```

and deleting from there? Or that's what you've tried?

Nope... that will let me see roots trash unfortunently :/

But sudo chown -R kim:kim /home/kim/ actually did seem to help, it only took such a long time to delete the files that I assumed that it failed in doing so (to my suprise I had over 10 Gbs in there)...

---

