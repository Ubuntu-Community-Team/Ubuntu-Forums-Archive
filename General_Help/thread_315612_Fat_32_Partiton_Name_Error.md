---
title: "Fat 32 Partiton Name Error"
date: 2006-12-09
forum: General Help
---

### Post by Xiunix on 2006-12-09
For some Unknown reason my fat-32 partition's name became illegible. I was wondering if any one knows the reason and how to fix it without losing the data I have on there.
 I have a screenshot of the partition mounted on the desktop which I have attached.

---

### Post by taurus on 2006-12-09
Did you mount it through /etc/fstab?  If yes, then paste it here then...

Applications -> Accesories -> Terminal
```
cat /etc/fstab
```

---

### Post by budgie9 on 2006-12-09
As to the cause I don't know. What I did find is that in XP my disk that had that same character with the name was in need of a defrag. Strangely enough when done, it cleared  and the name came back as it should.
I also found I had one partition named as F: under Windows suddenly became 'Local Disk'. I renamed the disk in XP and it was then fine.
I think there is a bug somewhere.

---

