---
title: "&quot;extract here&quot; on iso image appends &quot;;1&quot; to filenames"
date: 2008-05-25
forum: General Help
---

### Post by cogitordi on 2008-05-25
I have an ISO file for an MS Windows application. In Ubuntu (Gibbon), I right-click and select "extract here". The result is that the files are indeed extracted, but they all (including subdirectories) have ";1" appended to the filename. For example, "setup.exe" is extracted as "setup.exe;1".  

Anyone ever seen anything like this before?

---

### Post by cogitordi on 2008-05-29
I suspect that the problem was caused by the utility nrg2iso. The ISO image was created from an NRG.

I wrote a small Perl program to rename all the files extracted from the ISO image.

---

