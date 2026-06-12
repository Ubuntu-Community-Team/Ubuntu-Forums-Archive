---
title: "Filesnames in gvfs gets &quot;illegal encoding&quot;"
date: 2008-05-09
forum: General Help
---

### Post by pmdoc on 2008-05-09
Hi all!

I have a problem in Ubunty Hardy Heron:

"Mounting" a remote share in nautilus, utilizing gvfs, by ssh/sftp or ftp, results in multiple filesnames having weird filenames. At the end of the filename a postfix "illegal encoding" is added. When looking the .gvfs directory, the "illegal encoding" postfix is not present, and the øæå are replaced by "\233" or something similar.

The only files which do have this problem are files with the special scandinavian letters "æ ø å". But i suspect other special letters in other languages have the same problem.

Example:
Actual filename: "Søknader"
Nautilus filename: "S&#65533;knader (invalid encoding)"
Terminal filename: "S\233knader" (found in .gvfs)

How can i fix this? 

pmdoc

---

