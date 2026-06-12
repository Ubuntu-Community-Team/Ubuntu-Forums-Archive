---
title: "wierd folder"
date: 2007-01-18
forum: General Help
---

### Post by odin942zx on 2007-01-18
hi, i'm new to Linux, so i am not very familiar with anything when it comes to using it

i opened up my home folder, and for some reason, a file labeled "core.7457" showed up

i have never seen that folder before, but i dont want to delete it, in case it's a system file or something important

i tried opening it, but it came up with an error that said that gedit could not detect the character coding

could someone tell me what that file is, and what i should do with it?

---

### Post by taurus on 2007-01-18
It's probably a core dump when a program crashed!  If it's in your $HOME directory, it will not screw up your system if you delete it.  The only thing it would screw up is your own $HOME account but not likely with that file.  See what's the size and when it was created it?

```
ls -la core.7457
```

---

### Post by odin942zx on 2007-01-18
yea, it says that it is from a program that crashed, and it's 144.7 MB...

i'm not sure when it was created, but it wasn't there yesterday

---

### Post by JamieC on 2007-01-18
It's safe to delete. As Taurus said, it's a core dump from a crash.

---

