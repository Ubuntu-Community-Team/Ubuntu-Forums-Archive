---
title: "can't access Add Remove Programs"
date: 2005-09-15
forum: General Help
---

### Post by 68Firebird on 2005-09-15
When I try and load "add remove programs" it asks for password then when I enter password it just sits there loading, it never fully loads and lists my programs???? What could the problem be??

---

### Post by agm642 on 2005-09-15
Try running it in a terminal and see its output.

---

### Post by 68Firebird on 2005-09-15
What would be the command for doing that?

---

### Post by 68Firebird on 2005-09-15
bump

Still have not figured this problem out??????? I don't know what the command is?????

---

### Post by varunus on 2005-09-15
This is a bug in gnome-app-install.  There's a fix on the wiki or the forums somewhere...

---

### Post by agm642 on 2005-09-16
[QUOTE=68Firebird]What would be the command for doing that?[/QUOTE]
 Can't you see it through a Gnome menu editor or something like that? I usually use KDE, so I don't know exactly what you have to do.

---

### Post by Ubunted on 2005-09-17
[Bugzilla](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

[Fix](https://bugzilla.ubuntu.com/attachment.cgi?id=2836)

Just extract, open a terminal, navigate to the extracted files and do:

```
sudo make install
```

---

### Post by MButterman on 2005-09-27
Thanks for patch and install info, problem corrected.

All My Best,
MButterman

---

