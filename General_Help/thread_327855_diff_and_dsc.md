---
title: "diff and dsc"
date: 2006-12-29
forum: General Help
---

### Post by Buck2348 on 2006-12-29
What are .diff and .dsc files for when they accompany a source package?

Thanks,
Buck

---

### Post by dothedorky on 2006-12-29
I did some googling, 

a .dff file extension in a source package is also known as a "duplicate file finder" which a is utility that searches for duplicate files on your local computer and/or network drives.

a .dsc extension is a database description file.It's used in creating a database.

I could be completely off, seeing as how i dont know too much about databases in general.

---

### Post by johnnymac on 2006-12-29
.dsc is a debian source control file

and more than likely .diff is a file containing a "diff" (difference) from the last revision to the version being installed.

So usually a source package (which we find in the debian hooie) is a collection containing all the files you need to build or modify that specific piece of software.  Along with that comes the source control file (like the date it was built and such) and the diff file.

Hope this helps in assisting your understanding...

---

### Post by Buck2348 on 2006-12-29
Yes, thank you both--that helps.  Would I use either or both the .diff and .dsc files when compiling and installing the package?

Thanks,
Buck

---

### Post by johnnymac on 2006-12-29
Not unless your interested in checking out the major differences between the older version and the version you want to install....they are purely informational files.

---

### Post by Buck2348 on 2006-12-29
> **johnnymac said:**
> Not unless your interested in checking out the major differences between the older version and the version you want to install....they are purely informational files.OK, great.  That is what I thought but didn't know.  Thank you very much.

Buck

---

