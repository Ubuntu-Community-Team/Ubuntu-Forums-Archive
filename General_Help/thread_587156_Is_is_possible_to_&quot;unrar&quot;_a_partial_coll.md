---
title: "Is is possible to &quot;unrar&quot; a partial collection of volumes?"
date: 2007-10-22
forum: General Help
---

### Post by morrin on 2007-10-22
Hi

Apologies if this question is in the wrong section or not suitable for this forum. Basically I have a large "rar" file which has been split into volumes i.e. I have file.part1.rar, .... file.part10.rar . However I do not have the full collection of files , which is a dvdrip. I was just wondering if it possible to "unrar" say only the first section. Does the first section contain only file.part1.avi? Can I simply unravel only this part of the file? If I try to unrar it at the minute it looks for file.part2.rar which I don't have, and then exits.  The file.part1.rar cannot seem to be uncompressed on it's own.

Can anyone confirm if this is actually the case , or can I tell unrar only to look for the first volume?

Thanks in advance

---

### Post by kast on 2007-10-22
Usually you would unrar the first of how many files you have and that would produce the hole file. 

Not sure how it exactly works, but it links up with the other rar's to produce the one  file.

---

### Post by morrin on 2007-10-22
> **kast said:**
> Usually you would unrar the first of how many files you have and that would produce the hole file. 

Not sure how it exactly works, but it links up with the other rar's to produce the one  file.

Yeah, that's my problem. I usually do that. However in this case I only have the first volume of the file so when it looks for the second one, it can't find it and exits. I presume that it is probably unlikely that I can extract only the first part to "preview" a partial bit of the avi.

---

### Post by kast on 2007-10-22
I can take a guess and say your probably correct, you will need the other parts to view this file, but I have to admit I'm not an expert on the subject hopefully someone else might have some insight on this.

---

### Post by seventyeights on 2007-10-22
Try the "keep broken" switch: -kb

```
unrar e -kb "file.part01.rar"
```

---

