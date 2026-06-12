---
title: "&quot;/home/user/&quot; files disappeared"
date: 2020-03-28
forum: General Help
---

### Post by dt04 on 2020-03-28
I'm using Ubuntu 18.04.4. Suddenly all the content inside /home/user/ has disappeared, except those starting with a ".", any idea how to recover the files and why this has happened?

---

### Post by u666sa on 2020-03-28
You using English language?

try

sudo updatedb
locate Documents

Provided that you're using English, otherwise replace Documents with whatever it is on your language.

See, maybe you moved it somewhere. 

Post outputs here, and post output of l, command lower case l inside your home folder.

---

### Post by dt04 on 2020-03-28
I am using English. After doing "sudo updatedb", "locate Documents" shows me the following:

/usr/share/dbus-1/services/org.freedesktop.portal.Documents.service
/var/lib/app-info/icons/ubuntu-bionic-universe/48x48/gnome-documents_org.gnome.Documents.png
/var/lib/app-info/icons/ubuntu-bionic-universe/64x64/gnome-documents_org.gnome.Documents.png

and "l" shows me only 
snap/

---

### Post by ajgreeny on 2020-03-28
If you can remember exactly the name of a recent file you used or saved you can search for it with command ```
find -name filename.suffix
```

Also have a look at the file ***~/.config/user-dirs.dirs*** in case that can give us any clues; not likely but "any port in a storm".

---

### Post by u666sa on 2020-03-28
You deleted your files.

---

### Post by oldfred on 2020-03-28
Do you have separate /home partition?
Post this:
cat /etc/fstab

If for some reason, it cannot mount a separate /home partition, it will default to a new /home with default (mostly hidden) configuration files.

---

### Post by Impavidus on 2020-03-28
Maybe accidental deletion? When you use shell globbing to act on all files, it will skip the hidden files, which may explain why everything is gone except those starting with ..

Have you got backups?

---

### Post by Frogs Hair on 2020-03-28
Closed per OP request.

---

