---
title: "help with compression a big file in many small ones"
date: 2005-04-18
forum: General Help
---

### Post by kosmic on 2005-04-18
Ok, my problem is, I have a one big File 1,5 GB, but in my box I only have in this moment a cd recorder.

Is possible to compress that file to small ones of 650Mb ?

if yes how ?

---

### Post by Stormy Eyes on 2005-04-18
If you use tar, you should be able to split the file. Refer to tar's manual at [gnu.org](http://www.gnu.org/software/tar/manual/html_chapter/tar_toc.html).

---

### Post by andvaranaut on 2005-04-18
[QUOTE=kosmic]Ok, my problem is, I have a one big File 1,5 GB, but in my box I only have in this moment a cd recorder.

Is possible to compress that file to small ones of 650Mb ?

if yes how ?[/QUOTE]
 I think tar has multivolume capability, but don't really know the exact way to do it. Check the manual.

If, however, all you need is to divide the file in chunks that will fit on your CD recorder, you may use split:

```
split --bytes=650m my_very_large_file pieces
```

That would write the files piecesaa, piecesab, piecesac... each containing a part of my_very_large_file and 650 M in size. You'd then burn each piece to CD.

To recover my_very_large_file in another computer, copy all of the pieces to a directory on the hard drive and issue the command:

```
cat pieces* > my_very_large_file
```

That would recreate my_very_large_file by gluing together all of the pieces.

The process is admittedly a little clunky, but it will work ;)

Good luck, andvaranaut

---

### Post by shakin on 2005-04-18
The easiest way is to use tar-split.

[http://www.informatik-vollmer.de/software/split-tar.html](http://www.informatik-vollmer.de/software/split-tar.html)

---

### Post by maqi on 2005-04-18
[QUOTE=kosmic]Ok, my problem is, I have a one big File 1,5 GB, but in my box I only have in this moment a cd recorder.

Is possible to compress that file to small ones of 650Mb ?

if yes how ?[/QUOTE]
 Take a look [HERE](http://dsl.org/cookbook/cookbook_11.html#SEC157) for a description of the **split** command. Also have a look at ```
$ info coreutils split
```
But the "linux Cookbook" link gives an easier to understand description of usage of the command.

Basically, for your situation:
```
$ split -b650m <input-filename> <output-filename>
```

Hope this helps
maqi :)

---

### Post by andvaranaut on 2005-04-18
[QUOTE=shakin]The easiest way is to use tar-split.

[http://www.informatik-vollmer.de/software/split-tar.html](http://www.informatik-vollmer.de/software/split-tar.html)[/QUOTE]
 From the web site, I understand tar-split will only work on tar files with several files - that is, it reorders the files and redistributes them among different .tar.(gz)'s, so that each of them is a full .tar.gz on his own right. 

So if you only have a single 1.5Gb file, it will not work, would it?

cheers

---

### Post by brickbat on 2005-04-18
Hi,

Rar is the best program for this.  You can use it with the -v 650000k switch to give you 650mb files

ciao
bb

---

### Post by kosmic on 2005-04-22
Thank you very much

---

