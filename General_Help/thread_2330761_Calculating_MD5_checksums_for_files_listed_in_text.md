---
title: "Calculating MD5 checksums for files listed in text file"
date: 2016-07-14
forum: General Help
---

### Post by Rooster2000 on 2016-07-14
Suppose I have a files.txt with a following content:

```

/home/user/dir1/file1
/home/user/dir2/file2
/home/user/dir3/file3
/home/user/dir4/file-to-ignore
```

I want to pass these lines as an argument for md5sum, excluding one of the files. I have started with:

```
~$ cat files.txt | grep --invert-match 'file-to-ignore'
/home/user/dir1/file1
/home/user/dir2/file2
/home/user/dir3/file3

```

But how can I pass these lines to md5sum so that it considers them as files, not as text read from standard input?
This does not do it, but just calculates checksum for the text from standard input.

```
~$ cat files.txt | grep --invert-match 'file-to-ignore' | md5sum
8f57359c5e2e79785ad88e6adf5b1223  -
```

The result I would like to have is:

```
~$ md5sum /home/user/dir1/file1 /home/user/dir2/file2 /home/user/dir3/file3
d41d8cd98f00b204e9800998ecf8427e  /home/user/dir1/file1
d41d8cd98f00b204e9800998ecf8427e  /home/user/dir2/file2
d41d8cd98f00b204e9800998ecf8427e  /home/user/dir3/file3
```

---

### Post by &amp;KyT$0P# on 2016-07-14
First off, if you have only one file to ignore why not just delete it from the text file?

Anyway, if your shell is bash or ksh, try this?
```
IFS='
'
for i in `cat files.txt | grep --invert-match 'file-to-ignore'`;do md5sum "$i";done
```

or maybe even just
```
IFS='
'
md5sum `cat files.txt | grep --invert-match 'file-to-ignore'`
```

The important thing is setting IFS to just a newline, so that filenames with whitespace in them don't get split up as if separate files.

---

### Post by btindie on 2016-07-14
```
grep -v 'file-to-ignore' files.txt | xargs -r -I{} md5sum '{}'
```

---

### Post by Rooster2000 on 2016-07-16
Thanks for the replies, I ended up in a solution like this:

```
~$ grep --invert-match 'file-to-ignore' files.txt | xargs --no-run-if-empty --replace={}  md5sum '{}'
d41d8cd98f00b204e9800998ecf8427e  /home/user/dir1/file1
d41d8cd98f00b204e9800998ecf8427e  /home/user/dir2/file2
d41d8cd98f00b204e9800998ecf8427e  /home/user/dir3/file3
```

> **halogen2 said:**
> First off, if you have only one file to ignore why not just delete it from the text file?

This is because the text file contains a list of files to be backed up, and the file to ignore is the one where these checksums are being saved.

---

