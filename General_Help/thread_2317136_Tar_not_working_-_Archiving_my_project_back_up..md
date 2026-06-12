---
title: "Tar not working - Archiving my project back up."
date: 2016-03-13
forum: General Help
---

### Post by zuto2 on 2016-03-13
Hello,

It seems tar is not archiving all my files in my back up folder. It is giving me a error saying there was a problem adding files and the archive is missing data. Is there a way to force tar to do it or another solution? The file names are meant only for Linux, so archive formats that hate sloppy names are out of the question. This is the first time this happened to me. I tried three times and got the same result each time.

My only solution would be dropping my files in a ext4 filesystem Veracrypt container.

-Zuto

---

### Post by ian-weisser on 2016-03-13
Veracrypt? Are you using encryption?
If so, is this backup occurring while you are logged in and your files are decrypted?

---

### Post by zuto2 on 2016-03-13
> **ian-weisser said:**
> Veracrypt? Are you using encryption?
If so, is this backup occurring while you are logged in and your files are decrypted?

No. The files were not encrypted and were in plain form in normal folders. I could not tar them all, so I just tossed them in a Veracrypt encrypted volume. Now they are encrypted. 

There were no logs telling me what went wrong and I went with the quickest solution. This is just a super weird thing that has never happened to me. I can think of 3 ways why it did not work, but it will take too much time to test.

Solved.

---

