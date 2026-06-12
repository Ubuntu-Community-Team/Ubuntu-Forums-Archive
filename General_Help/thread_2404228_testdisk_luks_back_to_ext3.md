---
title: "testdisk luks back to ext3"
date: 2018-10-21
forum: General Help
---

### Post by aantoon on 2018-10-21
Hi all.
I have a 1.5TB external hdd that was partitioned as one ext3 partition.
I accidentally formated it to luks. Doing so I lost all data from the ext3 partiton.

Did hours and hours of googeling but can not find a solution all I find is &#8220;recovering a luks partition&#8221;

Testdisk gives:

partiton: >* Linux 
start:  0  0  1
end: 0 254 63
size in sectors: 16002

I did photorec on the hdd and it found some really big 30Gb and 40Gb files with messed up file-extensions. Files could not be opened and were never present on the drive of that I&#8217;m sure.

Is it possible to restore the ext3 partition and use photorec to recover the files?

---

