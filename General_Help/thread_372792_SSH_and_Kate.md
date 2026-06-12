---
title: "SSH and Kate"
date: 2007-02-28
forum: General Help
---

### Post by carrie.peary on 2007-02-28
I currently SSH into our linux servers on our school's campus to work on all my programming projects/etc. I recently installed Ubuntu 6.10 and want to edit those files easier, and I heard Kate is the best for it. Well, I downloaded and installed Kate but have no idea how to edit my files that I have to SSH into and get them to open for editing with Kate.....what do I do? or is there another way and I'm doing this wrong? Thanks!

---

### Post by Iarwain ben-adar on 2007-03-01
Hi there,

why don't you try
```
ssh -X ip.of.campus
```

This brings up a nice graphical screen (provided you have installed kate on the campus)


Iarwain

---

