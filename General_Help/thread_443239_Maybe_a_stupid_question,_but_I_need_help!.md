---
title: "Maybe a stupid question, but I need help!"
date: 2007-05-14
forum: General Help
---

### Post by chunchengch on 2007-05-14
I am a Linux newbie, I am trying to modify **Makefile** in order to successfully install **acpi4asus**, however I lack enough knowledge to use the shell commands, I know **mkdir** is used to make a new directory, while what command is to make a new file?

---

### Post by RedSquirrel on 2007-05-14
You could use:

```
touch filename
```

to create the file OR you could use a command line editor to create the file and open it for editing all at the same time (nano and vim are two such editors):

```
nano -w filename
```

or 

```
vim filename
```

---

### Post by chunchengch on 2007-05-14
RedSquirrel,

Thanks a lot!:)

---

