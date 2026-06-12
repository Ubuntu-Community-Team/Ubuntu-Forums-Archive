---
title: "VMWare file locations"
date: 2007-10-26
forum: General Help
---

### Post by rsd.za on 2007-10-26
I'm trying to find out the default location for VMWare virtual hard drives to be stored under ubuntu.

Gutsy broke my VMWare and I seem to have misplaced the hard drive files... *cough* 

I've tried searching for them to no avail, so I'm really hoping they weren't killed.

---

### Post by zvacet on 2007-10-26
```
locate package_name
```

or after you are on the top of filesystem (**cd /** )

```
sudo find / -name *package_name*
```

or 

```
whereis package_name
```

---

### Post by rsd.za on 2007-10-26
Thanks!

Someone else actually just gave me the answer, which is probably obvious to someone who's more used to the linux/ubuntu file structure: "/var/lib/vmware/Virtual Machines"

The reason I couldn't find the files is because I was wrong about the filename. The machine's hostname is totally unrelated to what i called it in the VMWare console, so I was searching on the wrong thing.

Good news is I didn't lose any work! Yay!

---

