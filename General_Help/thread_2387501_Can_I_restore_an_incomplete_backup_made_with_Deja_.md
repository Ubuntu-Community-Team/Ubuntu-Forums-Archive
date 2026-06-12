---
title: "Can I restore an incomplete backup made with Deja Dup (Backup default program)?"
date: 2018-03-19
forum: General Help
---

### Post by elMagnate on 2018-03-19
So this is my issue, made this backup in ubuntu of my windows 8 system (of mostly everything but Windows and program files) but the backup was incomplete... 

Now I tried with the same porgram that I made them in a Xubuntu fresh install, in Windows 10 with 7zip and with the Xubuntu own default file compressor and uncompressor, all of them either show me difftar files or difftar folders. I only uncompressed 3 or 4 difftar.gz files for test purposes, don't want to leave my computer working uncompressing for 5 or 6 hours if I'm not sure it would end in a different result. 

I suppose the ideal thing would be to make Deja Dup recognise the backup, but if that's not possible i'd be happy enough just having the files as before I backed up them. 

Maybe changing the filetype to tar.gz instead of difftar.gz? How can I do that massivele?

---

### Post by elMagnate on 2018-03-20
I think i solved it myself with this, will update if it ends up being successful

open backup file in terminal with your file manager and type this

```
for t in duplicity-full.name of your backup.*.difftar.gz; do tar xf $t; done
```

---

