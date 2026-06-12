---
title: "Group Permission Changed"
date: 2007-03-13
forum: General Help
---

### Post by louisd11 on 2007-03-13
After installing AIM (which still dosen't work) somehow my permission ownership changed to root. My login name is louis, but I made a folder on my desktop and when I moved stuff around and what not to install AIM I see a lock next to it. So I right clicked the folder  and saw that it was owned by "root". How ca nI change it back so its owned by "louis". Incae you need ti know the path to the folder is /home/louis/Desktop/Downloads . I have tried to use chgrp and chmod but I think I messed up the command. Please help!

---

### Post by Mr. C. on 2007-03-13
Terminal windows, enter the commands:

```
chown -R louis:louis /home/louis
```

MrC

---

### Post by louisd11 on 2007-03-13
GREAT worked thanx all u did was have to add sudo . Thankyou Mr C.

---

### Post by Duggeek on 2007-03-13
> **Mr. C. said:**
> Terminal windows, enter the commands:

```
chown -R louis:louis /home/louis
```

MrC

Don't forget the "sudo" -- can't take ownership from root without being root!

---

