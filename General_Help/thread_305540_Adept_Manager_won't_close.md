---
title: "Adept Manager won't close"
date: 2006-11-23
forum: General Help
---

### Post by Tilex on 2006-11-23
While I was installing a new JRE, I noticed the Adept Manager was stalled during the configuration of the packages.  When I hit "show details", I noticed it was needing my input, for I had to press 'OK' to the User Agreement form.  There was no way I could ever press 'OK' simply because I wasn't able to have control over the terminal (which is the upper half of Adept Package Manager when you click 'show details').  After trying half an hour, I decided to close Adept and reboot my system.  

Since then, every time I try to install something using either 'apt-get' and Adept Manager, it says some program is using my sources.list so I can't install anything.  I guess that's because I closed the program unexpectedly the other day.  I tried to go kill Adept Manager's processes manually that may lock the repositories or something but to no avail.

Anyone has an idea as to what to do in order to be able to use Adept Manager?
Thanks!

---

### Post by Tilex on 2006-11-23
Ok, I managed to 'close' theses processes that were locking the repositories by running 

```
dpkg --configure -a
```

which finished installing what I had previsouly closed without terminating the installation.

---

