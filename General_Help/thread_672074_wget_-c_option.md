---
title: "wget -c option"
date: 2008-01-19
forum: General Help
---

### Post by Choxo on 2008-01-19
Hi all,

I would like to know if it is possible for wget to skip files that are already downloaded?

I use wget -c -i text.txt where  text.txt is a file with urls thaat need to be downloaded...
However, when I abort the download, en I would like to continue, files that already have been download are getting downloaded again...

Is it possible that wget -c only continues downloading, but when a file is downloaded for 100%, it downloads it again?

Thanks!

---

### Post by geraldm on 2008-01-19
-c option is used with a single file partially downloaded.
If there is a filelist, purge the filenames that are already  completely downloaded from the list.

Gerald

---

### Post by skulda on 2008-01-19
I think -nc is the option you are looking for

---

### Post by Choxo on 2008-01-20
The problam is that if I use 

wget -c -N -i textfile.txt

unfinished downloads will not be finished.

If i use wget -c -nc, finished downloads will be downloaded again...

---

### Post by tbroderick on 2008-01-22
> **Choxo said:**
> Hi all,

I would like to know if it is possible for wget to skip files that are already downloaded?


I use the wget-queue script. Works great.

[http://decafbad.net/projects/scripts](http://decafbad.net/projects/scripts)

---

