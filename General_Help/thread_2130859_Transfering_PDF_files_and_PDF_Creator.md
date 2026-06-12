---
title: "Transfering PDF files and PDF Creator"
date: 2013-03-30
forum: General Help
---

### Post by Seeker84 on 2013-03-30
I've been consolidating old backup files and took some PDFs I create through Open office and placed them on my Windows XP machine through Samba.  The issue is that the PDFs can't be read on the Windows XP machine.  I was about to delete them when I tried to moved them back on the Ubuntu Machine.  The Ubuntu Machine reads the files just fine.  This leads me to believe that the program that created the PDF, didn't doo a good job.  Since I can still read them on the Ubuntu system, I was wondering if anyone has a good PDF creator, one that I can use to print the files to another format.

---

### Post by sudodus on 2013-03-30
What software did you use when you tried to read the files in the Windows machine? And what errors did you get?

I have created pdf files successfully with ***Open Office***, both in Ubuntu and Windows. Now I run ***Libre Office*** and can do the same. I think that the pdf files are readable by ***Adobe Acrobat Reader***, at least if the original format was not too complicated.

You can use ***ImageMagick convert*** to convert pdf files, and you can test if they would be easier to read.

---

### Post by Seeker84 on 2013-03-30
I was using Abode Reader X, the error is:
"Adobe Reader could not open'<File Name>.pdf' because it is either not a supported file type or because the file has been damaged ( for example, it was sent as an email attachment and wasn't correctly decoded)."

I think that that isn't right because when I bring the files back to the Ubuntu machine it opens and reads the files just fine in Evince Document Viewer 2.22.2.

I'll try the recommended ideas and get back, about 30 minutes.

---

### Post by Seeker84 on 2013-03-30
The convert option seems to solve my issue with not opening the PDF.  

My problem with creating the documents is that I wanted to have a printer to create the PDFs.  That doesn't look like a good idea based on my issue.  But Open Office has an export function which seems to work for what I want to do.

---

### Post by Seeker84 on 2013-03-30
Cuz I can't figure out how to mark this thread as solved.

---

### Post by sudodus on 2013-03-30
> **Seeker84 said:**
> The convert option seems to solve my issue with not opening the PDF.  

My problem with creating the documents is that I wanted to have a printer to create the PDFs.  That doesn't look like a good idea based on my issue.  But Open Office has an export function which seems to work for what I want to do.

I thought that you were using the export function all the time, so I didn't tell you about it. I'm glad you found out, so that your new pdf files will be good :-)

And you can use convert to fix the quality of the old pdf files.

See this link to mark the thread as SOLVED [[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730")

---

### Post by Seeker84 on 2013-03-30
For those of you who need a script(like me) to convert multiple file in the same directory using the covert function mentioned above, here's a bash file that I successfully used.  Be aware, ImageMagick had to be installed first and I manually created the convert Directory within the working one.

```

#!/bin/bash
for f in *.pdf;
do
  echo "Processing $f file..."
  # take action on each file. $f store current file name
  convert "$f" convert/"$f"
done

```

---

