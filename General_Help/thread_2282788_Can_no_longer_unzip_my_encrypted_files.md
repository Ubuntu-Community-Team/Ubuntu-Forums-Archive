---
title: "Can no longer unzip my encrypted files"
date: 2015-06-16
forum: General Help
---

### Post by Sleepy-zz-John on 2015-06-16
Hi,  I have been successfully zipping, adding entries and unzipping my own encrypted zipfiles using terminal and nautillus in 12.04 LTS and previous distros for a long time.   However since I upgraded to 14.04.2 a few days ago I can no longer open my encrypted zipfiles in "Files" which has apparently replaced nautillus.  Nor can I open them with "unzip" in terminal which skips some files and says " need PK compat. v5.1 (can do v4.6)".   I've looked at "funzip" and "unzipfx" and "file-roller" without success so far.    Basically I would simply like to find an easy way of continuing to open my encrypted zipfiles in "Files" like I did with nautillus,  but meanwhile what is this "PK compat v5" and where would I find it?

---

### Post by spjackson on 2015-06-20
Perhaps use 7zip, see [http://ubuntuforums.org/showthread.php?t=1416364](http://ubuntuforums.org/showthread.php?t=1416364)

---

### Post by Sleepy-zz-John on 2015-06-21
Thanks.  That was helpful.  I found that only some of my encrypted zipfiles were subject to this problem,  not all,  and by unzipping and re-zipping those with 7zip, I could then open them OK in "Files" or "unzip".  Still don't quite understand why upgrading to 14.04.2 has uncovered an incompatibility that wasn't apparent in 12.04, but the main thing is that I'm back in business with my encrypted zipfiles.

---

