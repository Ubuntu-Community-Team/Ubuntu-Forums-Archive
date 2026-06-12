---
title: "Permissions on shared Folder"
date: 2005-10-17
forum: General Help
---

### Post by viuks on 2005-10-17
Can anybody help me? I'm totally stuck with this. It is simple to change permisions on folder, but how to change them on all files and subfolders in it. I have one HDD, I would like to share with ather users, bur by default it sts only read permissions on group users.:confused:

---

### Post by cytoplasm on 2005-10-17
Folder named "foo":

chmod -R a+x ./foo

This enables execute permissions on folder foo and everything within folder foo.

---

### Post by wylfing on 2005-10-17
Open a terminal and type [FONT="Courier New"][COLOR="DimGray"]man chmod[/COLOR][/FONT] for more information about how to use that command. It's a very handy one to know.

---

### Post by seldenthuis on 2005-10-17
[QUOTE=cytoplasm]Folder named "foo":

chmod -R a+x ./foo

This enables execute permissions on folder foo and everything within folder foo.[/QUOTE]

I would use chmod -R a+**X** ./foo if I were you. a+x gives all files execute permission, even the ones that shouldn't have it, like text files.

---

### Post by cytoplasm on 2005-10-17
viuks,

seldenthuis is correct.  The command I provided was merely an example of how it works.  Please read the man page or do some google reading of chmod to get your head around it. ;)

---

### Post by viuks on 2005-10-22
Thank You guys for help!

---

