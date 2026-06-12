---
title: "How does rsync -H (hard links) actualy work"
date: 2023-06-03
forum: General Help
---

### Post by funkytwig4 on 2023-06-03
Ime asumeing and hoping it does as I am mirroring a large backup volume that uses them.  Ime curious exacly how it works.  It strikes me it would need to do the actual first then add the hard links, otherwise how would it work if interupted, but does not seem to work like this.  Whats the secret source?

---

### Post by TheFu on 2023-06-03
You'll need to look at the code for rsync to actually know how it works.  [https://github.com/WayneD/rsync/blob/master/hlink.c](https://github.com/WayneD/rsync/blob/master/hlink.c) 
I haven't, but I would expect that tracking the inode for every file would be involved. 

From the code:
```
/* Analyze the hard-links in the file-list by creating a list of all the
 * items that have hlink data, sorting them, and matching up identical
 * values into clusters.  These will be a single linked list from last
 * to first when we're done. */
void match_hard_links(struct file_list *flist)
```

Looking at the code, there are some coding style issues which make for poor maintainability of the code and can hide some errors, IMHO.  OTOH, who am I to complain?

---

### Post by HermanAB on 2023-06-04
A hard link is just another name for a file.  Rsync works across different file systems, so normally it would treat one file with two names, as two separate files, to ensure that it will always work. 

The -H option only works if the destination file system supports hard links and one file with two names will remain one file with two names.

However, the man page has a long explanation of caveats…

---

### Post by inamullah123 on 2023-06-04
[COLOR=#1F1F1F][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]The -H option to rsync tells rsync to create hard links instead of copying files when the source and destination files have the same content. Hard links are a type of file that points to the same data as another file. This means that if you have two files that are hard linked to each other, they will take up the same amount of space on disk.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]When rsync uses the -H option, it will first check to see if the source and destination files have the same content. If they do, rsync will create a hard link to the source file in the destination directory. This means that the destination file will not take up any additional space on disk.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]The -H option can be used to speed up rsync transfers by avoiding the need to copy files that have the same content. It can also be used to reduce the amount of disk space used by rsync backups.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]Here is an example of how to use the -H option to rsync:[/FONT][/COLOR]
[COLOR=var(--bard-color-on-surface-variant)]Code snippet[/COLOR]
rsync -a -H /source/directory /destination/directory
[COLOR=var(--bard-color-on-surface-variant)]Use code with caution. [Learn more]("https://bard.google.com/faq#coding")
content_copy[/COLOR]

[COLOR=#1F1F1F][FONT=&quot]This command will recursively copy the contents of the /source/directory directory to the /destination/directory directory. If any of the files in the source directory have the same content as files in the destination directory, rsync will create hard links instead of copying the files.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]The -a option tells rsync to preserve all of the file attributes, including permissions, ownership, and modification times. This is useful for making backups or transferring files between systems.The -H option to rsync tells rsync to create hard links instead of copying files when the source and destination files have the same content. Hard links are a type of file that points to the same data as another file. This means that if you have two files that are hard linked to each other, they will take up the same amount of space on disk.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]When rsync uses the -H option, it will first check to see if the source and destination files have the same content. If they do, rsync will create a hard link to the source file in the destination directory. This means that the destination file will not take up any additional space on disk.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]The -H option can be used to speed up rsync transfers by avoiding the need to copy files that have the same content. It can also be used to reduce the amount of disk space used by rsync backups.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]Here is an example of how to use the -H option to rsync:[/FONT][/COLOR]
[COLOR=var(--bard-color-on-surface-variant)]Code snippet[/COLOR]
rsync -a -H /source/directory /destination/directory
[COLOR=var(--bard-color-on-surface-variant)]Use code with caution. [Learn more]("https://bard.google.com/faq#coding")
content_copy[/COLOR]

[COLOR=#1F1F1F][FONT=&quot]This command will recursively copy the contents of the /source/directory directory to the /destination/directory directory. If any of the files in the source directory have the same content as files in the destination directory, rsync will create hard links instead of copying the files.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]The -a option tells rsync to preserve all of the file attributes, including permissions, ownership, and modification times. This is useful for making backups or transferring files between systems.[/FONT][/COLOR]

---

### Post by TheFu on 2023-06-04
> **inamullah123 said:**
>  This command will recursively copy the contents of the /source/directory directory to the /destination/directory directory. If any of the files in the source directory have the same content as files in the destination directory, rsync will create hard links instead of copying the files.
The -a option tells rsync to preserve all of the file attributes, including permissions, ownership, and modification times. This is useful for making backups or transferring files between systems. 

This isn't correct.  rsync only maintains existing hardlinks, it doesn't look inside files and magically generate new hard links if the content matches.  This is trivial to test, but the manpage and the code comments are very clear.

If there is confusion about what a hardlink is, check out the wikipedia page for it.  You can reproduce this test.
```

$ mkdir /tmp/HL
$ cd  /tmp/HL
$ cp ~/.bash_aliases bash_aliases

# Let's create a few identical copies:
$ cp bash_aliases bash_aliases2
$ cp bash_aliases bash_aliases3
$ cp bash_aliases bash_aliases4

# And 1 hardlink
$ ln bash_aliases bash_aliases-hl

$ ll
total 59
drwxrwxr-x  2 tf   tf      7 Jun  4 08:17 ./
drwxrwxrwt 13 root root   17 Jun  4 08:16 ../
-rw-r--r--  2 tf   tf   1116 Jun  4 08:17 bash_aliases
-rw-r--r--  1 tf   tf   1116 Jun  4 08:17 bash_aliases2
-rw-r--r--  1 tf   tf   1116 Jun  4 08:17 bash_aliases3
-rw-r--r--  1 tf   tf   1116 Jun  4 08:17 bash_aliases4
-rw-r--r--  2 tf   tf   1116 Jun  4 08:17 bash_aliases-hl
```

They all appear to be the same and copies.  I'll add a comment to the end of each file with the filename
```
$  echo "# bash_aliases" >> bash_aliases
$  echo "# bash_aliases2" >> bash_aliases2
$  echo "# bash_aliases3" >> bash_aliases3
$  echo "# bash_aliases4" >> bash_aliases4
$  echo "# bash_aliases-hl" >> bash_aliases-hl

$ tail -n 2 bash_aliases*
==> bash_aliases <==
# bash_aliases
# bash_aliases-hl

==> bash_aliases2 <==
alias xterm='xterm  -sb'
# bash_aliases2

==> bash_aliases3 <==
alias xterm='xterm  -sb'
# bash_aliases3

==> bash_aliases4 <==
alias xterm='xterm  -sb'
# bash_aliases4

==> bash_aliases-hl <==
# bash_aliases
# bash_aliases-hl
```
 
So the hardlink points to the exact same place on disk, just has 2 names.  The copies are separate files.  Reset the files back to be identical again. (remove the added comments).

Now, let's use rsync -H to clone /tmp/HL to /tmp/HL-mirror
```
$ mkdir /tmp/HL-mirror
$ cd ..
$ rsync -avH     /tmp/HL/    /tmp/HL-mirror/
sending incremental file list
./
bash_aliases-hl
bash_aliases2
bash_aliases3
bash_aliases4
[B]bash_aliases => bash_aliases-hl
[/B]
sent 4,807 bytes  received 122 bytes  9,858.00 bytes/sec
total size is 5,580  speedup is 1.13

```

Let's check which files use the same inodes.  'find' can show that data. So can 'stat'.
```
$ stat /tmp/HL/* |egrep 'File:|Device:'
  File: /tmp/HL/bash_aliases
Device: 1ch/28d Inode: **1148886**     Links: **2**
  File: /tmp/HL/bash_aliases2
Device: 1ch/28d Inode: 1149008     Links: 1
  File: /tmp/HL/bash_aliases3
Device: 1ch/28d Inode: 1149010     Links: 1
  File: /tmp/HL/bash_aliases4
Device: 1ch/28d Inode: 1149012     Links: 1
  File: /tmp/HL/bash_aliases-hl
Device: 1ch/28d Inode: **1148886**     Links: **2**
```

So there are 2 files which use the same inode, as expected.  What about inside the mirror?
```
$ stat /tmp/HL-mirror/* |egrep 'File:|Device:'
  File: /tmp/HL-mirror/bash_aliases
Device: 1ch/28d Inode: **1149086**     Links: **2**
  File: /tmp/HL-mirror/bash_aliases2
Device: 1ch/28d Inode: 1149088     Links: 1
  File: /tmp/HL-mirror/bash_aliases3
Device: 1ch/28d Inode: 1149090     Links: 1
  File: /tmp/HL-mirror/bash_aliases4
Device: 1ch/28d Inode: 1149092     Links: 1
  File: /tmp/HL-mirror/bash_aliases-hl
Device: 1ch/28d Inode: **1149086**     Links: **2**
```

So rsync mirrored the files, but retained the hardlinks as hardlinks.  Note that the mirror file "bash_aliases" in both directories do NOT point at the same inode, so they are copies between the rsync {source} and {target} locations.

See how easy it is to verify questions like this?  I spent 4x more time writing this post than running the commands.

---

