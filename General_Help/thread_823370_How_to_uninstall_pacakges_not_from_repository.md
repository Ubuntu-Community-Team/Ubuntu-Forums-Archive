---
title: "How to uninstall pacakges not from repository"
date: 2008-06-09
forum: General Help
---

### Post by Silpheed2K on 2008-06-09
Just curious i installed a game i dont want anymore via a package and not  the repositories... just double clicked and it asked me if i wanted to install it...
how do i uninstall something i installed from a package?

edit: specifically i want to uninstall a game called PainTown I got from [http://getdeb.net](http://getdeb.net)

---

### Post by Tom--d on 2008-06-09
I guess its from a .run file.

What i did was, 
```
gksu nautilus
```
and go to the directory, 
normally /usr/local/games/ and delete the folder. simple really.


Ah, you now have said its from a .deb file. 

Its located in the Synpatic Package Manager.

---

### Post by geirha on 2008-06-09
```
sudo aptitude remove paintown paintown-data
```

---

### Post by kpkeerthi on 2008-06-09
Anything installed using .deb files are automatically managed by the package manager. You can use aptitude, apt-get or synaptic to uninstall the package.

---

### Post by Silpheed2K on 2008-06-10
> **kpkeerthi said:**
> Anything installed using .deb files are automatically managed by the package manager. You can use aptitude, apt-get or synaptic to uninstall the package.

I didnt see it under Add/Remove (that's the package manager right) but some of the other suggestions worked.. I really appreciate you alls help.

---

### Post by cariboo on 2008-06-10
No, synaptic is located under System-->Administration-->Synaptic Package Manager. There way more programs listed there than in Add/Remove.

Jim

---

