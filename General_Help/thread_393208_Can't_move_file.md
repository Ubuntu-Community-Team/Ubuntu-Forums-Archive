---
title: "Can't move file"
date: 2007-03-25
forum: General Help
---

### Post by ComputerGuy56 on 2007-03-25
I'm trying to move a file to install Java, but when I try to move the file, I don't have enough permissions. I created the folder using mkdir /usr/java. I downloaded the file from the Java website. I'm also wondering, how can I delete files/folders using terminal?

---

### Post by ArieT on 2007-03-25
Remove files:
```

rm filenaam

```
Remove dirs:
```

rm -R dirnaam

```
move files
```

mv old new

```
change owner file
```

chown username file

```
change owner dir
```

chown -R username dir

```

---

### Post by ComputerGuy56 on 2007-03-25
Wow, just what I needed. Thanks

---

