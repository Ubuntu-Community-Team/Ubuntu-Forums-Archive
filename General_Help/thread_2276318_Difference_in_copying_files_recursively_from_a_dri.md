---
title: "Difference in copying files recursively from a drive using rsync"
date: 2015-05-01
forum: General Help
---

### Post by user155478 on 2015-05-01
I've used the command below to copy files from Windows drive to an external HDD, using the command:    
```
rsync -azv --progress --exclude "/Windows" --exclude "/Program Files" --exclude "Program Files (x86)" ./* /media/ubuntu/external_hdd/c_drive  
```
  What's a good way to verify that all files were copied and their  sizes are correct, etc? When I'm looking at the output folder on my  external HDD c_drive properties, it tells me it has 60,712  items (215,4GB), but looking at the rsync ```
command it, it tells me it  copied 61029 files. Here's the end report from rsync:[INDENT]   sent 201,309,277,955 bytes received 1,039,371 bytes 20,370,383.74   bytes/sec total size 216,054,087,051 speedup is 1.07  
 [/INDENT]

```Calculation tells me this:
201,309,277,955 bytes - 187.483875039034 gigabytes
216,054,087,051 bytes - 201.216048608534 gigabytes.
  So here's what it looks like:
rsync input has 61029 files, output folder has 60712 files
rsync shows it copied 187GB (or 201GB?), output folder has 215,4GB  
  So I've got less files, but the folder size has grown some 15-20GB?  
  I tried using diff command to compare both folders.  
  ```
diff --exclude="Program Files" --exclude="Program Files (x86)" --exclude="Windows" -r /media/ubuntu/OS media/ubuntu/external_hdd/c_drive
```
  And it gave me a few files that have been made afterwards - hidden  files starting with a dot (.hiberfil.sys.[idnumber] and  .pagefile.sys.[idnumber]), but this gave me 9,4GB of indifference, but  there's still the remaining 6GB (or 11?).

---

### Post by TheFu on 2015-05-01
Yeah - comparing directories on different types of file systems doesn't work.
The only way I know is to re-run the command and see if rsync sees any differences the 2nd, 3rd, 20th times that you don't expect.  If you add a new file between 2 and 3rd tries - is only that file copied?  What happens if you remove a file from the source side?  Any --delete option?

If you have enough room - rsync back to the source file system, just a different top level directory and use  a local comparison tool.

---

### Post by papibe on 2015-05-01
Hi user155478.

A few thoughts:

You used the compress option (-z) so the data was compress, then transferred, and then uncompress in the destination. This way the 'sent' data reported would differ from the actual amount sent.

Make sure you that you are comparing the same thing. A file has associated 2 sizes, and often are confused. One is the file size, and the other is the disk usage. Here's an example:

Creating a file with 1 character (a newline):
```
$ echo > file.txt

$ od -a file.txt 
0000000  nl
0000001

```
File size would be 1:
```
$ ls -l file.txt 
-rw-rw-r-- 1 user user 1 May  **[COLOR="#B22222"]1[/COLOR]** 15:17 file.txt
```
But its disk usage, i.e., the actual size it occupies on the disk is:
```
$ ls -sh file.txt 
**[COLOR="#B22222"]4.0K[/COLOR]** file.txt

$ du -h file.txt 
[COLOR="#B22222"]**4.0K**[/COLOR]	file.txt
```
Which is the size of a disk block.

Does that help? Let us know if you have more questions.
Regards.

---

