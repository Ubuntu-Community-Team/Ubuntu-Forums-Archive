---
title: "[SOLVED] Amarok messes up my song information"
date: 2008-05-31
forum: General Help
---

### Post by HighD on 2008-05-31
now what is this? Why does Amarok display some of my song names in chinese?? I have no chinese songs in my collection and have no problems with other files. They're well all organized using mp3tag on wine? Font perhaps? Id3 Tag? I'm clueless...

---

### Post by ajgreeny on 2008-05-31
Install tagtool from the repos and see if the id3 tags are in Chinese.  If that doesn't help, then it's really weird.

---

### Post by HighD on 2008-06-01
> **ajgreeny said:**
> Install tagtool from the repos and see if the id3 tags are in Chinese.  If that doesn't help, then it's really weird.

dude.....they were in chinese! They didn't show up like that in mp3tag but they sure did using tagtool.It had something to do with the tag coding.I changed the WRITE setting in mp3tag (through wine) from ID3v2.3 UTF-18 to ID3v2.3 ISO-8959-1, then saved the tag info and that solved the issue. Thanks!

---

