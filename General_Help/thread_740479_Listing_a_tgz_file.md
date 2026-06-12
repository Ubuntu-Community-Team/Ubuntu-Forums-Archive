---
title: "Listing a tgz file"
date: 2008-03-30
forum: General Help
---

### Post by lsutiger on 2008-03-30
I did a backup today and would like to verify the content of the tgz file. What I did before was list the contents and dump it into a text file, but I forgot the command.

I tried tar -t files.tgz >> list.txt but it just sits there and the file is 0 bytes.

Any advice?

---

### Post by Fixman on 2008-03-30
> **lsutiger said:**
> I did a backup today and would like to verify the content of the tgz file. What I did before was list the contents and dump it into a text file, but I forgot the command.

I tried tar -t files.tgz >> list.txt but it just sits there and the file is 0 bytes.

Any advice?

```

tar -xvvzf files.tgz

```

---

### Post by lsutiger on 2008-03-30
Thanx for the reply, but wouldn't that extract the files?

---

### Post by lsutiger on 2008-03-30
Got it 
```
 tar -ztvf file.tar.gz
```

---

