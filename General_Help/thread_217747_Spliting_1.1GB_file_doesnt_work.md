---
title: "Spliting 1.1GB file doesnt work"
date: 2006-07-17
forum: General Help
---

### Post by Bossieman on 2006-07-17
I have a file backup.tar.bz2 (1.1 GB) that I want to split into 2 files so I can burn them to CDs.
I used this command 
```

sudo tar -cvz backup.tar.bz2 | split -b 650m

```

This generates 2 files, xaa and xab. The problem is that xab is unrecognized and cant be opened, xaa cant be opened either but is recognized as gzip-arcive but when I try to open the file i get this errormessage "This arcive-type is not supported."

What am I doing wrong?

---

### Post by scxtt on 2006-07-17
i'm assuming that the files won't be usable again until they're joined back together ...

---

### Post by Bossieman on 2006-07-17
After I used
```

sudo cat xa* >  backup.tar.bz2

```
I had the file backup.tar.bz2 again. Thanks for the info :p

---

### Post by Bossieman on 2006-07-17
Damn, I cant open upp the created file backup.tar.bz2. I get error message this is not a bz2 archive.
Suggestions?

---

### Post by HAARP on 2006-07-17
You only tar'ed the archive. It's not actually bzip2-compressed.

---

### Post by Bossieman on 2006-07-17
> **HAARP said:**
> You only tar'ed the archive. It's not actually bzip2-compressed.

Ok, so the backupfile is actually not a bzip2 file. I used the command
```

tar cvpjf backup.tar.bz2

```
to create the backupfile, what should the right code be if I want a bzip2 file?

---

### Post by DoktorSeven on 2006-07-17
tar cfv backup.tar && bzip2 backup.tar

---

### Post by jordilin on 2006-07-17
> **Bossieman said:**
> 
I used this command 
```

sudo tar -cvz backup.tar.bz2 | split -b 650m

```

This procedure is wrong. The command tar with the pipe following does nothing. First of all you have several folders or one folder and you want to tar it and bzip it so:
```
tar -cjvf nameoffolder.tar.bz2 folder1...foldern
``` (the j option does a bzip2)
You get a file whose name is nameoffolder.tar.bz2
Now, we are going to split it by running:
```
split -b 650m nameoffolder.tar.bz2 prefixname 
```
where prefixname is what you'll get, in this case two files with names:
prefixnameaa and prefixnameab
In order to get back, you proceed like follows:
```
cat prefixname* > nameoffolder.tar.bz2
```

---

### Post by Bossieman on 2006-07-17
> **jordilin said:**
> This procedure is wrong. The command tar with the pipe following does nothing. First of all you have several folders or one folder and you want to tar it and bzip it so:
```
tar -cjvf nameoffolder.tar.bz2 folder1...foldern
``` (the j option does a bzip2)
You get a file whose name is nameoffolder.tar.bz2
Now, we are going to split it by running:
```
split -b 650m nameoffolder.tar.bz2 prefixname 
```
where prefixname is what you'll get, in this case two files with names:
prefixnameaa and prefixnameab
In order to get back, you proceed like follows:
```
cat prefixname* > nameoffolder.tar.bz2
```

Thanks, im going to try this now.

---

