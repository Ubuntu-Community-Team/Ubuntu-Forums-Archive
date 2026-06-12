---
title: "Bzip2 interesting scenario, what do you think will happen?"
date: 2008-06-20
forum: General Help
---

### Post by cody50 on 2008-06-20
I need to compress a 16 gb tar file with bzip2. I have approximately 4 gb free on my drive. Will it work? I know that bzip2 will delete the source file after the compression, but does it do it as it goes? otherwise I am thinking it will run out of space. Does anyone have any idea?

---

### Post by sdennie on 2008-06-20
It almost certainly won't work.

---

### Post by iaculallad on 2008-06-20
Bzip2 would still need a temporary space to compress your data. Won't work.

---

### Post by cody50 on 2008-06-20
thats what I am thinking, I stopped it for the time being and will have to work out some temporary space for it to do the work.

---

### Post by sdennie on 2008-06-20
If you can get rid of the original tar and rebuild it in stages (a few files/directories at a time), you may be able to make a series of .tar.bz2 files and that would work.

---

