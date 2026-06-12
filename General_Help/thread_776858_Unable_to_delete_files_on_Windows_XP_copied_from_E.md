---
title: "Unable to delete files on Windows XP copied from Evolution mail application"
date: 2008-05-01
forum: General Help
---

### Post by pwalter on 2008-05-01
I recently installed Ubuntu 8.04 as a dual-boat with WindowsXP.
Easy installation..everything went great. except...
After mounting WindowsXP drive I copied attachments from an email to the drive with WindowsXP.  Everything copied nicely..except that in addition to the pdf files and dwg files there are files that I cannot remove.

These files are named:
file:_C:Docume~1_Paul~1.DPI_Locals~Temp)nsmail-1
file:_C:Docume~1_Paul~1.DPI_Locals~Temp)nsmail-2
file:_C:Docume~1_Paul~1.DPI_Locals~Temp)nsmail-3
file:_C:Docume~1_Paul~1.DPI_Locals~Temp)nsmail-4
file:_C:Docume~1_Paul~1.DPI_Locals~Temp)nsmail-5

I'm guessing these file names are somehow refering the directory of my hardrive at my office as they include ".DPI_Locals" where DPI is the abbreviation of my office.

I've tried everything I know including third party software and Windows simply cannot find the files to delete yet they are big as day on my monitor. 

Anyone have any suggestions how to approach removing these "ghost" file names from my computer? 

Is there a method of safely copying attachements to one's NTFS drive without getting these "ghost" file names appearing?

---

### Post by ryanhaigh on 2008-05-01
I would try rebooting back into ubuntu and renaming the files to something very simple like file1 etc. My guess is that windows doesn't recognise some character eg. ) in the name or the 'extension', remember that windows would see everthing after the period as the extension and i don't know if you can have non alpha numeric characters in the extension. After renaming you should be able to get rid of them. I don't use evolution so I cant say what is causing the issue or how to get around it.

---

