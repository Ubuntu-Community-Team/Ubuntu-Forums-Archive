---
title: "Viewing list of files whom copies failed"
date: 2022-01-06
forum: General Help
---

### Post by yayou on 2022-01-06
Hello everyone,

Using Dolphin I got copy errors while copying directories from my old HDD to my new one. I had to choose the option to ignore all of them so that the operation could finish without having to intervene each time. Now I would like to have a listing of all the files whom copy failed except that I do not know which log file records this kind of result. Could you help me please?

Thanks for having read.

---

### Post by schragge on 2022-01-06
See the thread [Is there a way to log file move operations in Dolphin?](https://www.reddit.com/r/kde/comments/ii0u2a/is_there_a_way_to_log_file_move_operations_in) @Reddit.

---

### Post by yayou on 2022-01-06
I don't have the impression that it can solve my problem (perhaps I should try auditctl) but this page shares good informations. Thank you schragge.

---

### Post by HermanAB on 2022-01-06
Note that rsync uses checksums to ensure correct copies are made.  If you need to transfer large numbers of files with increased risk of errors, use rsync.

---

### Post by yayou on 2022-01-06
Thank you HermanAB for this great advice. I will read about this software and use it from now on. Too many people recommend it.

---

### Post by The Cog on 2022-01-06
> **HermanAB said:**
> Note that rsync uses checksums to ensure correct copies are made.  If you need to transfer large numbers of files with increased risk of errors, use rsync.
I'm not convinced that is true. According to the man page, --checksum is just more thorough checking to see if a transfer is necessary. I don't see anything about checking that the write to disk was error free. 

Running **rsync -nv --checksum <src> <dst>** will list the files that don't match (-n means dry-run, no actual writing), but may end up just reading checksums from disk cache rather than actual disk.

---

