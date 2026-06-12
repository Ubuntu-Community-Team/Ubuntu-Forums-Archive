---
title: "How can I see all the packages I have installed via apt-get? Edgy server"
date: 2007-04-11
forum: General Help
---

### Post by SnowPunk98 on 2007-04-11
I have an Edgy Server and am going to redo it but I wanna see what programs I have installed via apt-get so I don't forget anything. Is there anyway to check that and make a list for the reinstall process?

---

### Post by cstudent on 2007-04-11
This thread seems to be the closes to come to what you want.

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by Arador on 2007-04-11
*dpkg --get-selections | grep -v deinstall* should do the trick

---

### Post by SnowPunk98 on 2007-04-12
Nice that was perfect, thanks.

---

