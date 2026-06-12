---
title: "Remove Unused Dependencies"
date: 2006-12-24
forum: General Help
---

### Post by Afoot on 2006-12-24
Hello,
What I'm looking for is a command to remove all of the unused dependencies of a meta package. Running "apt-get autoremove" works to some extent, but if I for instance want to remove "ubuntu-desktop" and all its dependencies, how would I go by doing so? 

Please, don't compile a list of the packages to remove if you were planning to do so... :p

---

### Post by bodhi.zazen on 2006-12-24
Edgy: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Dapper: [http://www.psychocats.net/ubuntu/purekdedapper](http://www.psychocats.net/ubuntu/purekdedapper)

---

### Post by Afoot on 2006-12-24
> **bodhi.zazen said:**
> Edgy: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Dapper: [http://www.psychocats.net/ubuntu/purekdedapper](http://www.psychocats.net/ubuntu/purekdedapper)
Thanks, but that was exactly what I *didn't* want. I want a tool that I can use for any meta package I remove with apt-get...

---

### Post by Afoot on 2006-12-24
> **bodhi.zazen said:**
> Edgy: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Dapper: [http://www.psychocats.net/ubuntu/purekdedapper](http://www.psychocats.net/ubuntu/purekdedapper)
Thanks, but that was exactly what I *didn't* want. I want a tool that I can use for any meta package I remove with apt-get... I just used "ubuntu-desktop" as an example.

---

### Post by bodhi.zazen on 2006-12-24
As far as I know you can not remove a meta-package with apt-get.

Use aptitude. If you install a meta package with aptitude you can remove a meta package with aptitude as well.

[http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

FYI Synaptic is a front end for apt-get.

---

### Post by brownkenny on 2006-12-24
Umm, try deborphan.  `sudo deborphan` returns a list of packages that are unnecessary, allowing you to remove them with your package manager of choice.

---

### Post by Afoot on 2006-12-25
> **bodhi.zazen said:**
> As far as I know you can not remove a meta-package with apt-get.

Use aptitude. If you install a meta package with aptitude you can remove a meta package with aptitude as well.

[http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)
Thanks, that's exactly what I wanted. :)

> **bodhi.zazen said:**
> 
FYI Synaptic is a front end for apt-get.
Yep. :p

[QUOTE=brownkenny]Umm, try deborphan. `sudo deborphan` returns a list of packages that are unnecessary, allowing you to remove them with your package manager of choice.[/QUOTE]
Seems nice, thanks. But it tries to remove w32codecs, which I surely want to have on my system.

---

### Post by rudiz on 2006-12-25
Here is a  GUI for deborphan:

sudo apt-get install gtkorphan

---

