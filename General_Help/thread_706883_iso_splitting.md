---
title: "iso splitting"
date: 2008-02-24
forum: General Help
---

### Post by banditxkr on 2008-02-24
hi everyone thanks in advance

i have some isos i would like to split so they fit on my flash drive to put them on a different computer

could someone please tell me how to do this in ubuntu

---

### Post by hugmenot on 2008-02-24
split and cat on the shell, e.g.

---

### Post by banditxkr on 2008-02-25
sorry for being so noobish, but how is this done

---

### Post by taurus on 2008-02-25
Applications -> Accessories -> Terminal
```
man split
man cat
```
Hit the space bar for the next 24 lines.

---

### Post by stevejesus on 2008-02-25
What sort of computer are you taking it to?  If you are taking it to a windows computer, your best bet is to create a multi-file .rar archive.

---

### Post by banditxkr on 2008-02-28
> **stevejesus said:**
> What sort of computer are you taking it to?  If you are taking it to a windows computer, your best bet is to create a multi-file .rar archive.

glad you said this, would have been a big problem, can this be done with a program like 7zip.

---

### Post by hugmenot on 2008-02-28
Ah, yes. 

Read "man 7z".

example:

```
7z -v50m a archive.7z bigfile.iso
```

for 50MB volumes.

Can be extracted aywhere with 7zip, too.

---

