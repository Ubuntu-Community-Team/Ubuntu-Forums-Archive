---
title: "du - different results when comparing macOS and Linux directories"
date: 2020-08-02
forum: General Help
---

### Post by gebseng on 2020-08-02
Hi everyone,

I have two supposedly identical directories on macOS (HFS+) and Ubuntu Server 20.04 (EXT4). I copied the directory from the Mac to the Linux machine using ```
[COLOR=#000000][FONT=&amp]rsync -auv [directory1] user@192.168.0.20:[directory2] [/FONT][/COLOR]
``` without problems. Now I have some problems with differing sizes of those two directories. Lets start with this:

On the Linux machine, when my path is inside [directory2], I do 
```
ls | wc -l
```, I get ```
[COLOR=#000000][FONT=Menlo]147296[/FONT][/COLOR]
``` as a result for the number of files in the directory
```
du -shk
```, I get ```
[COLOR=#000000][FONT=Menlo]146460120[/FONT][/COLOR]
``` as a result in kB

On the Mac, inside [directory1], I do the same
```
ls | wc -l
```, I get ```
[COLOR=#000000][FONT=Menlo]147296[/FONT][/COLOR]
``` as a result for the number of files in the directory
```
du -shk
```, I get ```
[COLOR=#000000][FONT=Menlo]149033768[/FONT][/COLOR]
``` as a result in kB

To explain the size difference, on the Linux machine I tried
```
[COLOR=#000000][FONT=Menlo]du -shk --exclude './.*'[/FONT][/COLOR]
``` to exclude hidden files and resource files, I get ```
[COLOR=#000000][FONT=Menlo]146445092[/FONT][/COLOR]
``` as a result in kB

same on the Mac:
```
[COLOR=#000000][FONT=Menlo]du -shk -I './.*'[/FONT][/COLOR]
``` to exclude hidden files and resource files, I get ```
[COLOR=#000000][FONT=Menlo]149033768[/FONT][/COLOR]
``` as a result in kB, same as before

When I do a ```
[COLOR=#000000][FONT=Menlo]diff -x '.*' -rq [dir1] [dir2][/FONT][/COLOR]
``` it ends without output, so seemingly the same.

What could explain the size differences? Or is there a better way to compare file sizes?

---

### Post by dinkidonk on 2020-08-02
The difference may be related to a difference in size of file system entries and extra space allocated for sparse files. Try command "du -sb" to get the apparent byte size instead of a block size.

---

### Post by gebseng on 2020-08-02
Thanks! on the Ubuntu machine, ```
du -sb
``` gives an output of [COLOR=#000000][FONT=Menlo]149672510341.

On the Mac, I get a [/FONT][/COLOR]```
[COLOR=#000000][FONT=Menlo]du: illegal option -- b[/FONT][/COLOR]
```[COLOR=#000000][FONT=Menlo] error. The macOS -du manpage states [/FONT][/COLOR]> **-h**[COLOR=#000000][FONT=Menlo]      "Human-readable" output.  Use unit suffixes: Byte, Kilobyte,[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]             Megabyte, Gigabyte, Terabyte and Petabyte.[/FONT][/COLOR][COLOR=#000000][FONT=Menlo], but I'm not sure how to use this.[/FONT][/COLOR]

---

### Post by The Cog on 2020-08-03
Try this instead of -b then:
```
du -s --apparent-size
```

---

### Post by kneutron on 2020-08-03
--Mac HFS+ does not support sparse files.  As long as the number of files are the same, and they pass a basic md5sum / sha1sum check, it could be the difference between 512 sector size and 4096 on the different drives.  And HFS+ just stores files a little differently.

REF: 
[https://en.wikipedia.org/wiki/HFS_Plus](https://en.wikipedia.org/wiki/HFS_Plus)

---

