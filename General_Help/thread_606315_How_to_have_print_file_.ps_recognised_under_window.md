---
title: "How to have print file .ps recognised under windows?"
date: 2007-11-07
forum: General Help
---

### Post by aum11 on 2007-11-07
My lappy has no printer connected to it.  I need to print something from my lappy on a friend's windows pc.  So I thought I would chose the print to file option and then transfer the file via flashdrive.  It created a .ps file.

When I transfer this to the windows machine, the ps file type is unrecognised.

How to solve this problem please?

Thanks for Your help.

---

### Post by mpierce on 2007-11-07
From the DOS prompt of the XP machine:

COPY my_file.ps LPT1 /B and press ENTER

Hope this helps...

---

### Post by cwaldbieser on 2007-11-07
> **aum11 said:**
> My lappy has no printer connected to it.  I need to print something from my lappy on a friend's windows pc.  So I thought I would chose the print to file option and then transfer the file via flashdrive.  It created a .ps file.

When I transfer this to the windows machine, the ps file type is unrecognised.

How to solve this problem please?

Thanks for Your help.

I think CUPS lets you print to PDF.  You might get more milage going that route.  You can get GSView for Windows to print a postscript file, too, I think.

---

### Post by mypapit on 2007-11-07
Try GhostScript for windows.

[https://sourceforge.net/project/showfiles.php?group_id=1897&package_id=108733&release_id=529280](https://sourceforge.net/project/showfiles.php?group_id=1897&package_id=108733&release_id=529280)

It has ps2pdf package which can convert ps to PDF file

---

### Post by aum11 on 2007-11-08
Yes ghostscript and ghostview did the job thanks

---

