---
title: "TAR for backup file ?"
date: 2006-10-22
forum: General Help
---

### Post by rfruth on 2006-10-22
I backup my /home once a month the easy way, copy all files uncompressed.  At first everything fit on one CDRW, then it took two then three now its time to use TAR (or gzip) anyone have a script to automate this ?

---

### Post by lloyd_b on 2006-10-22
Actually, you can create a compressed archive of the entire directory with a single command:

```
**tar -zcvf home.tgz ***

```
Then burn that onto a CD.

If you need to restore it, copy from the CD into your home directory, and:

```
**tar -zxvf home.tgz**
```

Lloyd B.

---

### Post by rfruth on 2006-10-22
Thats what i'm looking for, thanks !

---

### Post by rfruth on 2006-10-23
Its me again, my backup file is too big to fit on a single CDRW, anyway to have TAR make multiple small files or write directly to the CDRWs & prompt for a blank when needed ?

---

### Post by lloyd_b on 2006-10-23
> Its me again, my backup file is too big to fit on a single CDRW, anyway to have TAR make multiple small files or write directly to the CDRWs & prompt for a blank when needed ?

You've got a compressed archive that's over 650Mb?:confused: :confused: 

Dare I ask exactly what you have in that directory?:-)

Tar can't automatically split file - it's not quite that sophisticated.  However, it has a cousin, named "split".  Give you three guesses what that does....

```
tar -zxvf home.tgz *
split -d -b 600M home.tgz home
```

will create a single archive, then split it into pieces, with each piece a maximum of 600Mb.  The "piece" files will be named "home01", "home02", etc.

To glue them back together:

```
cat home01 > home.tgz
cat home02 >> home.tgz
cat home03 >> home.tgz
```

Note that there is a single ">" (Greater than) before the first "cat", but a double ">" after each following "cat".

Note: If you ever need further info on commands like "cat" "tar" "split", etc, in a terminal window type "man {command}".  This will display a reasonably good explanation of the the command and it's options.

Lloyd B.

---

### Post by rfruth on 2006-10-23
Yep my compressed archive file is 1.5 GB (lots of audio files) am sure I can trim it down some but will still need to split it, am off and running now, thanks again :)

---

### Post by skymt on 2006-10-23
You only need one cat command:```
cat home{01..03} > home.tgz
```

---

### Post by lloyd_b on 2006-10-23
```
cat home{01..03} > home.tgz
```

Doesn't work.  The "{01..03}" syntax strips leading zeroes when it's processed, so that's equivalent to:

```
cat home1 > home.tgz
cat home2 >> home.tgz
cat home3 >> home.tgz

```
not

```
cat home01 > home.tgz
cat home02 >> home.tgz
cat home03 >> home.tgz
```


Lloyd B.

---

### Post by skymt on 2006-10-24
Oops, sorry. ZSH is smart enough to include the zeros, I guess Bash isn't.

---

