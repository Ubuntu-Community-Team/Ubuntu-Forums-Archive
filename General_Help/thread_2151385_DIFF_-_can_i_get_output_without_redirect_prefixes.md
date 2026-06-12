---
title: "DIFF - can i get output without redirect prefixes?"
date: 2013-06-04
forum: General Help
---

### Post by cbillson on 2013-06-04
quite a useful feature, the output <> appears before lines to show if the changes are in the from / to file. 

Can i stop it from doing this, i just want the raw data that is different.

Had a look through the MAN page, but cannot see anything that looks like i want to do.

Also, is '--suppress-common-lines' a default?

Cheers
Chris

---

### Post by Vaphell on 2013-06-04
you can easily strip these 'redirects' with sed 's/^[<>]//' but how are you going to recognize which part belongs to which file?

---

### Post by cbillson on 2013-06-05
File 1 is always an older copy of the file

File 2 is the only copy that could have additions

i'm only outputting differences, and they could only be in file 2

diff file1 file2 > changes

I'm then outputting the whole file changes to logger to send to another server via Syslog, it causes me problems at the remote end.

I'd added the sed command as a workaround, looks like i did it the right way for once :)

---

