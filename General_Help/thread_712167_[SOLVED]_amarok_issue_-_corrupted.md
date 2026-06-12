---
title: "[SOLVED] amarok issue - corrupted?"
date: 2008-03-01
forum: General Help
---

### Post by Tyke91 on 2008-03-01
I was stupid and left my laptop on all night with amarok running. It ran out of power and now something is corrupted. I don't have any icons for amarok or any buttons to start it. typing amarok in a terminal will just do nothing and I can't install or uninstall it. here is the error I get with apt-get install amarok:

```

Unpacking replacement amarok ...
dpkg: error processing /var/cache/apt/archives/amarok_2%3a1.4.7-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/kde', which is also in package kdelibs-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/amarok_2%3a1.4.7-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

how can I fix this?

---

### Post by Tyke91 on 2008-03-01
sudo apt-get install -f gives me this output

```

dpkg: error processing amarok (--remove):
 cannot remove file `/usr/share/applications/kde/amarok.desktop': Not a directory
Removing amarok-xine ...
Errors were encountered while processing:
 amarok
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by sumguy231 on 2008-03-01
See if maybe 'sudo apt-get --purge remove amarok' resolves it. Barring that, maybe you could try removing the file yourself to appease the removal script?
```
sudo mv /usr/share/applications/kde/amarok.desktop /usr/share/applications/kde/amarok.desktop.broken
```

---

### Post by Tyke91 on 2008-03-01
/usr/share/applications/kde is not a directory... it's a binary. so now I'm confused about why the script would want to remove a non existant directory... and that's probably what the computer is confused about too.

---

### Post by Tyke91 on 2008-03-01
your move command wouldn't work... so I did

sudo rm -f /usr/share/applications/kde/amarok.desktop 

and that seemed to fix the problem

reinstall worked

---

