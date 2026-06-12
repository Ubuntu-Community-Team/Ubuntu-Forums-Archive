---
title: "Need guidance about file  compression"
date: 2021-11-29
forum: General Help
---

### Post by gardenair on 2021-11-29
hi,
       I need guidance about file compression.
There are some files with like ending 

 foo.cpio.gz 
 foo.tar.gz  
 foo.zip[URL="https://cdimage.debian.org/cdimage/unofficial/non-free/firmware/stable/current/firmware.zip"]

[/URL]What is the difference in-between these three files ? Are the same ? What is the technical difference ?

Thanks in advance.

---

### Post by HermanAB on 2021-11-29
Some people hate this kind of answer:
$ man gzip

That would actually tell you everything.

You could also type man gzip in a web browser. :)

---

### Post by The Cog on 2021-11-29
foo.tar.gz would be a tar archive that has been compressed by gzip.
foo.cpio.gz - some other file type compressed by gzip. 
Using gunzip on the above files would create foo.tar or foo.cpio. You could rename the gzip files, but the convention is to retain the original filename and append ".gz". gzip is a file compressor,and only compresses individual files - it doesn't do archiving. 
On the other hand, tar is an archiving program that originally couldn't do compression, but has at some point gained the -z flag that says to compress the archive it writes by passing it through gzip.

I guess foo.zip would be an archive created by zip (a different compression utility). zip does both archiving (it is a file container) and compression.

---

### Post by rsteinmetz70112 on 2021-11-30
You could just try to gunzip or unzip the files and see what your get.

---

### Post by SeijiSensei on 2021-11-30
Usually files with a .zip extension are compressed using the ZIP method that's common on Windows machines. In early days the ZIP algorithm was patented or otherwise encumbered so a free and open alternative called GNU Zip was created. By convention these files have gz extensions. The utilities gzip/gunzip handle files in that format; the utilities zip/unzip handle .zip files.

---

### Post by Holger_Gehrke on 2021-11-30
The first two files originate with programs that follow the Unix philosophy: one program for one job. Putting multiple files into one file in such a way that it is possible to pull the single files back out is one job, storing a file in such a way that it takes less space is another job. cpio and tar are Unix archiving tools. You can read all about them in their respective manuals which should be available on your Ubuntu system ('man cpio' and 'man tar' in a terminal; or if you've got the graphical manual reader 'xman' installed you can find them in that, too). The extension '.gz' is commonly found on files that have been run through gzip. gzip uses a compression method that is similar to **one** of the methods used by zip, but the file format is different. gzip and the decompressor gunzip also have their own manual pages. Just like there are multiple tools for creating archives, there are other tools for compressing data: compress, gzip, bzip, xzip, ...

The third file probably was created using zip (by the Info-zip group), Winzip or pkzip. This format originated with pkzip on MS-DOS and the program does both tasks in one program. There's many programs and file formats for compressed archives like that: arc, zip, lharc, zoo, rar, ace, 7zip, ... As you can imagine, most of these tools are not compatible with one another. Newer programs might be able to read (or even write - 7zip can create .zip files that are fully compatible with pkzip, Info-zip and Winzip but take some percentage less space than files produced by these would) the formats of older programs but there never was any attempt at creating something like a common format for compressed archives.

One thing to keep in mind with all these archivers is that formats created for DOS or Windows have trouble storing all the things that can be in a Linux file system; trying to use one of these to store Linux files will probably loose the permission bits, ACLs, and extended attributes associated with a file and I don't think they would handle links (hard or soft/symbolic), sparse files or device files gracefully.

Holger

---

