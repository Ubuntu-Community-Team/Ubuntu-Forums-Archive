---
title: "rsync not working with --include-from option."
date: 2014-02-11
forum: General Help
---

### Post by c2tarun on 2014-02-11
I am trying to add folder locations to a simple txt file so that rsync can create my backup. But when I am running --dry-run its not showing any file transfer.

```
$ rsync -avrh --dry-run --progress --include-from=/home/tarun/.backup_scripts/include_files.txt /home/tarun/b_test/destination/
sending incremental file list
drwxrwxr-x        4096 2014/02/11 22:26:47 .


sent 41 bytes  received 12 bytes  106.00 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)


```

include.txt file:
```
$ cat include_files.txt 
+ /home/tarun/b_test/source
```

source and destination folder contents.
```
$ ls *
destination:


source:
abs-guide.pdf  C++ By its Creator.pdf  file.txt  testDir  videoplayback_002

```

---

### Post by sudodus on 2014-02-12
I'm using ***rsync*** too, but I have not used **--include-from=...**

Have you tried without the plus sign at the beginning of the line in the file?

Maybe you have better luck with **--files-from=...**

See ```
man rsync
```

---

### Post by Habitual on 2014-02-12
In my experience, both include-from and exclude-from files are just straight textual listings of absolute paths.

---

### Post by Dennis N on 2014-02-12
I experimented with this in the past, but don't use it. I recall that the files in the list must have paths relative to the source folder and be no higher than the source folder. 

```
rsync -ti --files-from=filelist source destination
```

---

### Post by Dennis N on 2014-02-12
Just ran a little test. Works as advertised.

```
folder and file structure
-------------------------
rsync-testing
folder1
--folder3
----file5
--file1
--file2
folder2
file3
file4
filelist

dn@Sydney:~/work/rsync-testing$ rsync -nti --files-from=filelist /home/dn/work/rsync-testing/ /home/dn/work/rsync-testing/folder2/
>f+++++++++ file3
>f+++++++++ file4
cd+++++++++ folder1/
>f+++++++++ folder1/file1
cd+++++++++ folder1/folder3/
>f+++++++++ folder1/folder3/file5

```

filelist lists all files except file2

---

### Post by papibe on 2014-02-12
Hi  c2tarun.

The '--include-from' option is used to list rsync's 'filter rules'. In order to include only one subdirectory (e.g. /home/tarun/b_test/source/), all its contents (all recursive tree), and nothing else, you need several rules. Something like this:
```
+ /home/
+ /home/tarun/
+ /home/tarun/b_test/
+ /home/tarun/b_test/source/
+ /home/tarun/b_test/source/**
- *
```
However note that this rules must be relative to the path being read by rsync. If you run your rsync command from your home, you may simplify the rules to something like this:
```
+ b_test/
+ b_test/source/
+ b_test/source/**
- *
```
In any case, you need both source and destination in your command:
```
rsync -avrh --dry-run --progress --include-from=.backup_scripts/include_files.txt  **b_test/** **destination/**
```
Hope it helps. Let us know how it goes.
Regards.

---

