---
title: "unable to copy some files"
date: 2015-03-23
forum: General Help
---

### Post by kebeat on 2015-03-23
Hello. I am trying to transfer my files from external HDD to a pendrive (in Files, Ubuntu 14.04), but many file names (not all of them!!) loose their accented or special characters (they are automatically substituted with _. Then I tried Krusader. I had no problem with special characters but some files still remained problematic. I had the error message stating unsuccessful copying, without further information.
Can you help me, please?

---

### Post by bardo2 on 2015-03-23
from looong time ago (after coming from Windoze), i recall i had such a problem using different filesystems (like NTFS + ext4) from different operating systems. It took some time to realize, that it boiled down to a character set issue (UTF-8 vs ISO-something or cp-???). But i found mount options did not solve that really. Instead, there was a tool (looking it up...)

There are plenty of options, tools dealing with character sets include recode, iconv,...
Many people used some combination of find with other commands.
But i was happy, when i found convmv.

But you may(?) have another problem (permission, corruption), the lack of useful exploration/error messages makes me guessing wildly...

---

