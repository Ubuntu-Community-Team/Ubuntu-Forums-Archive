---
title: "Remove duplicate files"
date: 2014-11-15
forum: General Help
---

### Post by Nishad_Hasan on 2014-11-15
Hello guys, i am in serious problem. My hard disk space is just running low. I find the problem. There hugh amount of duplicate data. So, can anyone suggest me how i [remove duplicate files]("http://www.duplicatefilter.com"). Please friend suggest me. It emergency for me.

---

### Post by dragin-mm on 2014-11-15
> **Nishad_Hasan said:**
> Hello guys, i am in serious problem. My hard disk space is just running low. I find the problem. There hugh amount of duplicate data. So, can anyone suggest me how i [remove duplicate files]("http://www.duplicatefilter.com"). Please friend suggest me. It emergency for me.

Try this using fdupes - ```
sudo apt-get install fdupes
``` and then ```
fdupes -rsd
``` run that on the directory you want to find the duplicated files on for instance ```
fdupes -rsd /media/driveNAME
``` That should work.

---

