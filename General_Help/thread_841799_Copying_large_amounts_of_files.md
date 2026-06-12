---
title: "Copying large amounts of files"
date: 2008-06-26
forum: General Help
---

### Post by jackyyll on 2008-06-26
What's the best, safest, way to copy 200GB+ of files to another hard drive? Preferably an option that is resumable incase of bad things happening. By safest, i mean not losing bytes in the transfer and files not getting corrupted for what ever reason. 


Thanks

---

### Post by Zero Prime on 2008-06-26
Can you connect the hard drive up as a slave on your computer?  If you can you could simply copy and paste.  I don't know if that's the best way, but it may be the safest.  That's also the way I back up most of my files.

---

### Post by jackyyll on 2008-06-26
Yeah, the hard drive is in the same computer. But i'm looking for something i will be able to resume where it left off incase i need to stop it or the computer crashes for what ever reason.

---

### Post by jackyyll on 2008-06-26
Anyone? :S

---

### Post by grizzu on 2008-06-26
man rsync

```
rsync -aP source destination
```

---

