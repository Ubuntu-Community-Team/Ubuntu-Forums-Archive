---
title: "Input / output errors due to disk corruption, how to copy files?"
date: 2020-02-17
forum: General Help
---

### Post by blackbird34 on 2020-02-17
Hi all ,

My SSD has been dying for a while (currently 1522 bad sectors) so i bought a new one, and installed my preferred KDE Neon on it and everything is fine on that front. However I'm having issues copying some of my files from the old drive: 

They refuse to copy and I only get a message saying ```
Error splicing file: Input/output error
```

Sometimes it also says "error 5". I have tried this with Dolphin (I run KDE), Thunar and even Nemo file manager, and with the command line. None work. 
I looked all this up and all the forum posts i found confirmed it was due to disk corruption. 

HOWEVER I have managed to get the videos out in one piece by transcoding them (with Handbrake) onto the other disk. It takes forever.

Is there any faster way of doing this?

---

### Post by SeijiSensei on 2020-02-17
Photorec, which comes with TestDisk, is often recommended in situations like this.  You can install testdisk from the Ubuntu repositories.

[https://www.cgsecurity.org/wiki/PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec)

---

