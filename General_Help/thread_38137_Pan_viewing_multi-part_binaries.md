---
title: "Pan: viewing multi-part binaries"
date: 2005-05-30
forum: General Help
---

### Post by hanzj on 2005-05-30
How can we download multi-part binaries using Pan? And not just download, of course, but "stitch up" the several parts into one whole complete file for viewing...

Please take a look at the attached images below of screenshots of Pan. I'd like to know how to access the binary called "Basic Japanese".

I went to Pan's website, but there is no instruction manual (yet). If you know of an online guide to Pan, please let us know!

Thank you.

---

### Post by tahuya_rat on 2005-06-19
I'm sure this post may be a day (or 20) late and a dollar short, but a red icon to the left of the header means that the post is incomplete on your server.

Pan will combine and decode all the parts of a multi-part binary post automatically if they are all there.

As far as reconstituting the RAR files when you have them all downloaded, Ubuntu has support for that pre-loaded (at least in the distro I installed), but if they are RAR 3.0 files, I think you may have to use WinRAR (in wine) to extract them.

There may be a better way to do it native, and if so, I'd really like to know about it!

hth
tahuya_rat

---

### Post by darkaudit on 2005-06-19
This is a file that has been split into multiple .rar files. You'll need to download all of the files to be able to extract.

To extract, you need the unrar-nonfree package. No need to muck about with WINE or WinRAR. Unrar-nonfree will work with both ark and file-roller. Open the first .rar file and extract. As long as all the .rar files are present, everything will extract automagically.

I would also suggest the par2 package to verify and repair these multi-file posts. Posters use .par and .par2 files to help users make sure they have all the parts without having to go begging for reposts. Usage is par2 v foo.par2 for verify, or par2 r foo.par2 for repair. I just go ahead and do the repair by default. That way I don't have to scan the set twice If it's complete, nothing is needed. If damaged, it'll go ahead with the repairs.

---

### Post by Buchinho on 2007-07-12
I know this thread is quite old but maybe somebody can help me...

I need to know how to select all multipart files to completely download them all and not to miss any file.

Can somebody help me??

---

### Post by Cappy on 2007-07-12
Can you shift click and select them all?
I use hellanzb (only works with nzb) and it does EVERYTHING automatically so I'm not quite sure.

---

### Post by Buchinho99 on 2007-07-13
No, it doesn't. Where do you get the NZB Files from?

---

### Post by h2gofast on 2007-10-04
[www.binsearch.info](www.binsearch.info)

---

### Post by peter_k on 2007-12-16
A little different question, but how about files with a .00x extension (i.e. .001 .002 .003 etc...)

I know the Windows folks do this with hjsplit; I have not been able to successfully install their Linux version however; I have also tried join, but to no avail.  Are there any other programs to handle this?

---

### Post by peter_k on 2007-12-16
Turns out there are 2 ways to handle this:

1. cat -- I couldn't get join to work, but cat is OK:

syntax is cat file.* > newfilename.extension


2. A program developed by one of our forum users (Spano) called lxsplit; it also has a gtk front end associated with it.  Very nice, and as it's from one of our own, the choice I'll go with.

---

