---
title: "Apt Problem"
date: 2006-07-08
forum: General Help
---

### Post by JoshHendo on 2006-07-08
I tried to insatll gnome-main-menu from [this file](http://ubuntuforums.org/showpost.php?p=1203615&postcount=130), and ever since I have not being able to get into Synaptic. Every time I try to open it, it comes up:

```

E: The package gnome-main-menu needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

Is there a way that I would be able to fix this without re-installing Ubuntu?

---

### Post by zerwas on 2006-07-08
Hi,
> **JoshHendo said:**
> Is there a way that I would be able to fix this without re-installing Ubuntu?
Umm...try to move the untarred .deb-file into the directory /var/cache/apt/archives
It might help :confused:

Greetings,
zerwas

---

### Post by JoshHendo on 2006-07-08
> **zerwas said:**
> Hi,

Umm...try to move the untarred .deb-file into the directory /var/cache/apt/archives
It might help :confused:

Greetings,
zerwas
Thanks for the reply.

I tried that but it didn't seem to work :(

---

### Post by JoshHendo on 2006-07-08
> **JoshHendo said:**
> Thanks for the reply.

I tried that but it didn't seem to work :(
Why didn't I think of this before >.<

I simply opened gdebi and re-installed the packaged, and that fixed it :p.

---

### Post by zerwas on 2006-07-08
That was easy :D
And also apt said what you have to do XD.

---

