---
title: "Home Partition"
date: 2007-04-14
forum: General Help
---

### Post by JimS on 2007-04-14
...
Resently I installed Ubuntu Edgy over the top of Breezy after first
successfully creating and populating a seperate home partition.
I used the method from Psychocats.

I want to find out if with my install of Edgy there isn't 2 homes.
How would I do that?  If there are 2, how do I make sure that
my seperate home partition is the only working one.

Thanks in advance,
JimS
[email]workfromhome@pobox.com[/email]
...

---

### Post by taurus on 2007-04-14
Applications -> Accessories -> Terminal
```
df -h
cat /etc/fstab
```

p.s.  Not a good idea to include your e-mail in a message unless you don't mind getting spams.

---

