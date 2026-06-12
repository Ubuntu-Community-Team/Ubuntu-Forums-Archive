---
title: "error in etc/apt/sources.list"
date: 2006-11-25
forum: General Help
---

### Post by admiralthrawn999 on 2006-11-25
Ok, I was trying to install wine to run a virtuilization of windows on my i386 machine.  However,while installing, something either got typed wrong, or corrupted, so now my /apt/sources.list has an extra line (33) that does not work

normally, it wouldnt be a problem, I can find and open the file using a text editor, except it will not let me re-write (it is read only)

within the terminal, if I type apt-get uninstall wine, it says "type eb-sc  is not known on line 33 in source list /etc/apt/sources.list"

can someone please tell me how to manually get rid of it so I can make a clean install?

---

### Post by koenn on 2006-11-25
you need to be root to edit sources.list, so run your editor with sudo, 
eg in a terminal:
```
sudo gedit /etc/apt/sources.list
```

The mistake in question is obviously 'eb-sc' - should propably be deb-src

---

### Post by meng on 2006-11-25
And the error will be on line 33!!!!

---

