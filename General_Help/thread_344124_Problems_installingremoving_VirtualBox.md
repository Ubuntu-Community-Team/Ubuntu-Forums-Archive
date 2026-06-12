---
title: "Problems installing/removing VirtualBox"
date: 2007-01-22
forum: General Help
---

### Post by _asc_ on 2007-01-22
Hello!

I installed VirtualBox but something went wrong. Whenever I want to reinstall or remove it with apt-get, I get the following error:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

```

I have copied the VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb file to /var/cache/apt/archives, but that did not change anything.

Any idea what I can do to remove this package?

---

### Post by palmerthegeek on 2007-01-23
Having the same problem... I've tried the basic stuff 

Please help totally stuck..  and want to try and reinstall... but need to get VirtualBox removed first.

---

### Post by _asc_ on 2007-01-23
This really sucks! My whole package management is screwed!

When I open Synaptic, I get
```

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

and I cannot install any other software packages anymore. Is there a "force" option or something to get rid of this package. I hope I don't have to reinstall Edgy to solve this problem.

---

### Post by ipguru99 on 2007-01-23
don't remember where I posted it, but this whole scenario happened to me as well.. there are really good instructions on how to remove it at the virtualbox.org web site...
[HTML]http://www.virtualbox.org/wiki/User_FAQ[/HTML]

it took about three totally separate steps, but after getting them all, this thing rocks!  I could never get my vmware to use my wireless (on my host), but virtualbox picked it up automatically...

---

### Post by _asc_ on 2007-01-23
Thank's ipguru99, you are a life-saver!

---

### Post by palmerthegeek on 2007-01-24
Thanks a million I spent forever (okay an hour or two)  looking for exactly these instructions!
Feeling much better now, knowing my Edgy will be okay!

---

