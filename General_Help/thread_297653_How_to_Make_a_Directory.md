---
title: "How to Make a Directory"
date: 2006-11-11
forum: General Help
---

### Post by mrbilbobaggins1 on 2006-11-11
Hello
  I am new to Linux...& am trying to install Doom3 with Iso...
  I keep getting a message saying No Directory Found when I try to install
mount -t iso9660 /path/to/doom3-CD1.iso /mnt/cdrom/ -o loop 
   Any & All help will be greatly appreceiated.
    Thank You
    [email]mrbilbobaggins1@comcast.net[/email]

---

### Post by taurus on 2006-11-11
Open a terminal, Applications -> Accessories -> Terminal, and type

```
cd /mnt/cdrom
ls -la
```

---

