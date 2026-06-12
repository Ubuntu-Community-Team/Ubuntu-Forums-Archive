---
title: "Shutter NAS problems"
date: 2016-01-04
forum: General Help
---

### Post by viktor9 on 2016-01-04
Hello! So as of Christmas I now have a NAS for backup storage. The problems have been rather few and most of the things I wanted backed up I have figured out. What I can't seem to understand however is why Shutter will not save my screenshots onto the NAS. I've properly mounted the NAS and I have full read/write permissions on all folders. Whenever i try to save the file I get a permission denied error. Is this a common problem with Shutter in general or is there anything I can try in order to make this work. I imagine some of you may suggest I use FTP, but besides forcing me to perform another action it would also require that I could save 2 FTP setups (which as far as I'm concerned is not possible) as I upload some screenshots to my dedicated server.

Any help is appreciated.

---

### Post by viktor9 on 2016-01-04
Fixed the issue. Apparently it was a invalid filename. I remembered that the NAS has NTFS or something so I couldn't use the ":" produced by the %T wildcard.

---

