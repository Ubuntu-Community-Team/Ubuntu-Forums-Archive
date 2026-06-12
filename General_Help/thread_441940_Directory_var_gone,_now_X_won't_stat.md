---
title: "Directory /var gone, now X won't stat"
date: 2007-05-13
forum: General Help
---

### Post by ghetto2ivy on 2007-05-13
Help. Somehow I messed up my /var directory while changing apache permissions. Now /var seems to be gon, in place is just an empty dir.

Tried this [http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-rescue-var](http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-rescue-var)
 to no avail.

Any thoughts? or resinstall time?

---

### Post by 542 on 2007-05-13
Hi there,

Can you be more specific about what you changed with Apache permissions? 

Also, do you know if /var is on a separate partition? It maybe that it isn't being mounted. If you're unsure you could post your /etc/fstab file.

---

### Post by ghetto2ivy on 2007-05-13
Its not on a different partition. I must have had some typo in my chmod command. I'm not sure how I messed it up. I used a "chmod a+rx" command, which should not have messed things up. So maybe its unrelated. I'm going to try and get to my command history and post back later today.

Either way it seems like /var directories occasionally crash and that there are recover methods, and skeleton directories that can be put in place. I'm trying to resist the usual windows urge -- reinstall, which I'm learning is usually not the answer in linux.

Perhaps some dpkg command?

---

### Post by ghetto2ivy on 2007-05-13
I gave in and reinstalled. Luckily I had a separate home partition and all went smoothly. Used the same username  and I can access everything the same as before. Simply have to reinstall some apps. Even that was nowhere near as painful as windows.

FYI - the var directory problem showed up after I issued this command
```
$ sudo chown -r steven /var/www 
```

---

