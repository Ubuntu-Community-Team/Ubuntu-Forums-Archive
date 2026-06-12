---
title: "Making Ubuntu Terminal behave like FreeBSD"
date: 2008-03-17
forum: General Help
---

### Post by abuthemagician on 2008-03-17
I know I probably just need to use a different shell, but when I am in FreeBSD I can type a partial word and hit the up arrow and it will list previous commands that used those letters to start with. Anyone know how to duplicate that in Ubuntu?

---

### Post by Joeb454 on 2008-03-17
You have to edit /etc/inputrc it's commented out :)

```
gksudo gedit /etc/inputrc
```

that's assuming you're running a standard Ubuntu install :)

---

### Post by abuthemagician on 2008-03-17
thank you very much :) this always bugged me

---

### Post by Joeb454 on 2008-03-19
I only found out how to enable it a few days ago :)

---

