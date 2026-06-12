---
title: "Comparing Identical Files within Separate Folders"
date: 2007-01-14
forum: General Help
---

### Post by puppy on 2007-01-14
Hi everyone, is there any way that I can run a comparison between the contents of one folder and another?

To explain, I have copied my mp3 music folder over to another drive and I want to do a file by file comparison and output any differences (to check if individual files have not copied over)

Is there any CLI command or GUI tool I can use to achieve this please?

Many thanks ;)

---

### Post by Jussi Kukkonen on 2007-01-14
diff has a recursive mode (see *man diff*), maybe it does what you want.

---

### Post by majoridiot on 2007-01-14
```
ls -a -R path/to/source/directory > source.list
ls -a -R path/to/destination/directory > dest.list
comm -3 source.list dest.list > missing.list
```

the first line lists (ls) recursively(-R)  all files (-a), including hidden files, in the source dir and 
redirects the output to the file source.list

the second line does the same to the destination directory and outputs to file dest.list

the third line compares (comm) the two files and outputs only files not found in both dirs (-3)
and outputs to missing.list... note that it will report files that are present in the dest and not
the source as well, so it checks both ways.

there are other options available, i suggest

```
man ls
man comm
```

---

### Post by puppy on 2007-01-14
Thanks for the advice - now I know what we're talking about I've managed to find Kdiff3 in the repositories which does exactly what I want - and in fact offers the ability to simply compare each file by it's size and output the results. I can see how it would be very useful for more complex tasks however, but the basic functionality is exactly what I needed :) 

Many thanks

Pups

---

### Post by rabid9797 on 2007-01-14
here's another option if you want to do it with gui(and have more options)

i did a howto thread a couple months back on comparing md5 hashes of files for duplicates in batches, check out the programs here to see if any of them can help you out:

[http://ubuntuforums.org/showthread.php?t=272292&highlight=duplicate+files](http://ubuntuforums.org/showthread.php?t=272292&highlight=duplicate+files)

---

