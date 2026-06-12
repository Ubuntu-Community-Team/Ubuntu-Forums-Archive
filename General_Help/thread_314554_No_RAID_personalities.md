---
title: "No RAID personalities"
date: 2006-12-07
forum: General Help
---

### Post by randomphrase on 2006-12-07
All the RAID doco I have seen starts with "make sure your /proc/mdstat" contains the RAID personalities you want to use.

Unfortunately, mine doesn't:

```
alastair@pierre:~$ cat /proc/mdstat 
Personalities : 
unused devices: <none>
```

How do I rectify this?

---

### Post by randomphrase on 2006-12-09
OK here's the answer. In fact there are two answers:

1. In the case that you want to set up a raid array and you don't have the module loaded, you probably want to do the obvious insmod raid1. This will get you up and running enough to do mdadm --create.

2. In the case that you have set up a raid array but the raid1 module is not being loaded at boot time, the *wrong* answer is to edit /etc/modules. (I've learned that editing /etc/modules is almost always the wrong answer to any given module-loading problem in Ubuntu :)

Here's what you do instead:

sudo dpkg-reconfigure mdadm

That's it. Easy really.

---

