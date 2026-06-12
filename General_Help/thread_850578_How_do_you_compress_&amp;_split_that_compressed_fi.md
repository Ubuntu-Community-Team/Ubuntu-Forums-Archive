---
title: "How do you compress &amp; split that compressed file into a number of parts like WinRAR?"
date: 2008-07-05
forum: General Help
---

### Post by s3a on 2008-07-05
How do you compress & split that compressed file into a number of parts like WinRAR for Windows?

I have like a ~9 GB bunch of files and I want to compress them and turn all those files/folders into 2 compressed files that I need to bring together to extract that way I can burn on two DVDs. I don't want to use the .rar extension. I want to use whatever format is 100% free as in freedom. (**.tar.gz**?)

If it is possible, is it possible to be even more specific as to set what file size u would like each part (=the division of the files so that I can fit them on DVD) to be (like WinRAR can do in Windows)? The idea is to tell it to make a 4.35 GB file to fill a whole disc and then the rest can be in the second file so I can add a couple other things on the second disc if I want to.

Thanks in advance!

---

### Post by Fass on 2008-07-05
[http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

Peazip can do what you want.

---

### Post by bodhi.zazen on 2008-07-05
You may archive the files with what ever you would like, tar, zip, bzip, etc

The split the archive with split.

bzip2 -v file

makes an archive file.bz2

Now splt the file 

split -b 4G file.bz2 split

This will make the file into splits

splitaa
splitbb

To combine them later

cat splitaa splitbb >> file.bz2

---

### Post by Fass on 2008-07-05
> **bodhi.zazen said:**
> To combine them later

cat splitaa splitbb >> file.bz2

Won't work across platforms, though, unless they have "cat".

---

### Post by casperlingus on 2008-07-05
You can also use "split" from the command line.  

```

cat the9GBfilename.iso | split -b 4G - prefixForSplitFiles

```

This will create a bunch of files 

```

prefixForSplitFiles.aa
prefixForSplitFiles.ab
prefixForSplitFiles.ac
...

```

To put them back together you use the command like:

```

cat file.aa >> file.iso; cat file.ab >> file.iso; cat file.ac >> file.iso;

```

I don't know why they make it so hard to find the solution to combining files that are split, but that's how I figured out how to do it and it works.

-Casper

---

### Post by bodhi.zazen on 2008-07-05
> **casperlingus said:**
> You can also use "split" from the command line.  

```

cat the9GBfilename.iso | split -b 4G - prefixForSplitFiles

```This will create a bunch of files 

```

prefixForSplitFiles.aa
prefixForSplitFiles.ab
prefixForSplitFiles.ac
...

```To put them back together you use the command like:

```

cat file.aa >> file.iso; cat file.ab >> file.iso; cat file.ac >> file.iso;

```I don't know why they make it so hard to find the solution to combining files that are split, but that's how I figured out how to do it and it works.

-Casper

you are doing it the hard way :twisted:

split -b 4G the9GBfilename.iso prefixForSplitFiles

cat prefixForSplit.Files.* >> file.iso

#You could put the * earlier to save typing

cat prefix*.* >> file.iso

---

### Post by bodhi.zazen on 2008-07-05
> **Fass said:**
> Won't work across platforms, though, unless they have "cat".

peazip looks nice ;)

---

### Post by s3a on 2008-07-05
Can't I just use 7-Zip 4.57 for Windows in Wine? I like to support open source software and although that is Windows software; it is easy to use and, more importantly, is open source software. :)

*If Wine doesn't work for me, I'll try the solutions above. However, I had read somewhere on a similar question in these forums and 7z got brought up so I googled it and read about it and liked it. So, I'll try it soon and will report wether my attempt is a success or not.*

---

### Post by bodhi.zazen on 2008-07-05
7Zip is in the Ubuntu repositories ....

I believe 7Zip is command line only on linux, but it will break the archive into smaller segments.

[http://linux.die.net/man/1/7za](http://linux.die.net/man/1/7za)

---

