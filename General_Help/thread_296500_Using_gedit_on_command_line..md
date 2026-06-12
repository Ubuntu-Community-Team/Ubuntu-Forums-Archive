---
title: "Using gedit on command line."
date: 2006-11-09
forum: General Help
---

### Post by napoelon on 2006-11-09
So I installed Ubuntu 6.10 LAME server, and I am running into problems. I am trying to edit a file for mysqls "my.cnf" and i type in the following, and command line, shoots back follows:

I type..
```
gksudo gedit /etc/mysql/my.cnf
```

The response..
```
(gksudo:3540): Gtk-WARNING **: cannot open display:
```

I am promptly following instructions according to the Ubuntu Guide wiki.

([http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_MYSQL_Database_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_MYSQL_Database_Server))

Please, any help is appreciated.

Thanks

---

### Post by bigken on 2006-11-09
try nano instead of gedit ;)

---

### Post by bsussman on 2006-11-09
> **napoelon said:**
> So I installed Ubuntu 6.10 LAME

Did you install desktop or server ubuntu?

If server, you do not have a gui in the server 'edition'.  So you cannot use gksudo or gedit.  You will need to use nano or vi or another terminal editor:
```

sudo vi <filename>
```

---

### Post by taurus on 2006-11-09
> **bsussman said:**
> Did you install desktop or server ubuntu?

If server, you do not have a gui in the server 'edition'.  So you cannot use gksudo or gedit.  You will need to use nano or vi or another terminal editor:
```

sudo vi <filename>
```
I believe he said "I installed Ubuntu 6.10 LAME server..."

---

### Post by napoelon on 2006-11-09
> **bsussman said:**
> Did you install desktop or server ubuntu?

If server, you do not have a gui in the server 'edition'.  So you cannot use gksudo or gedit.  You will need to use nano or vi or another terminal editor:
```

sudo vi <filename>
```

awesome, great help. well now that i know i dont need gksudo.. i installed the package, now how would i go for uninstalling (big n00b, i know)

---

### Post by Engnome on 2006-11-09
> **napoelon said:**
> awesome, great help. well now that i know i dont need gksudo.. i installed the package, now how would i go for uninstalling (big n00b, i know)

sudo apt-get remove <package name> will remove that package.

man <command> will give you the manual for that program.

---

### Post by dcstar on 2006-11-09
> **bigken said:**
> try nano instead of gedit ;)

nano instead of vi (actually, just about anything instead of vi.......)

---

