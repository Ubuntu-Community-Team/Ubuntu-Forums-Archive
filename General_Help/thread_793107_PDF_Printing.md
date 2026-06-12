---
title: "PDF Printing"
date: 2008-05-13
forum: General Help
---

### Post by omrsafetyo on 2008-05-13
Hey guys 

I have 2 or 3 PDF viewers installed on my Ubuntu Edgy EFT box - and none of them have an option to print.

For me, its just as easy (if not easier) to simply go to the CLI and "lp myfile.doc", but for my wife, thats just simply not an option.

In order to get around this, I created a "Magic Folder" on the desktop called "TO PRINT".  I then have a script run at start-up with a while 1 = 1 loop, which sleeps, and then periodically runs an ls on the folder, and if it has anything in it, it prints it.  This ends up making printing anything much easier, and certainly isn't a big deal.

Still, I can't help but think that there must be a PDF viewer for Ubuntu that has a print option.

??

---

### Post by minaev on 2008-05-13
Most of them have. I don't even remember a PDF viewer that doesn't print... What about kpdf?

---

### Post by omrsafetyo on 2008-05-13
I think I have kpdf and envice - though I'm not at home right now.

Neither my wife or myself could find it...  and I know I have seen posts on printing from envice...  hmmm...

---

### Post by minaev on 2008-05-13
Perhaps, you don't have CUPS installed and the PDF viewers see no printers?

---

