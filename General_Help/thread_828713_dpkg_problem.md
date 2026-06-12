---
title: "dpkg problem"
date: 2008-06-14
forum: General Help
---

### Post by phearis on 2008-06-14
I'm sure it's been asked and solved but I can't seem to find my question


I'm getting the "dpkg --configure -a" error when I try to update, so I went into the command to run it manually and I got this:

sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/updates/0202' near line 1:
new line in field name 'untu 2'



ummmmmm.... huh?? :(

---

### Post by iaculallad on 2008-06-14
> **phearis said:**
> I'm sure it's been asked and solved but I can't seem to find my question


I'm getting the "dpkg --configure -a" error when I try to update, so I went into the command to run it manually and I got this:

sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/updates/0202' near line 1:
new line in field name 'untu 2'



ummmmmm.... huh?? :(

Create an empty  **/var/lib/dpkg/available** file and redo the command:

```
sudo dpkg --configure -a
```

---

