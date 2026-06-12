---
title: "locating files on the hard drive"
date: 2007-07-09
forum: General Help
---

### Post by jeff0149 on 2007-07-09
I have installed Gnuaccounting.  That went well.  To configure the program, I need to identify the path for openoffice.org.  I have read some documtntation and looked tin the "Places" and can't find the needed file.  This file system is a little different than windows and I don't know what to do next.  Please help.
Jeff

---

### Post by confused57 on 2007-07-09
> **jeff0149 said:**
> I have installed Gnuaccounting.  That went well.  To configure the program, I need to identify the path for openoffice.org.  I have read some documtntation and looked tin the "Places" and can't find the needed file.  This file system is a little different than windows and I don't know what to do next.  Please help.
Jeff
Maybe this will work:
```
which gnucash
```
or if you installed a different program, substitute that for gnucash

---

### Post by meatpan on 2007-07-09
> **jeff0149 said:**
> To configure the program, I need to identify the path for openoffice.org. 

Consider running the command 'which ooffice' to get the location of the ooffice executable (f it is installed).  If you need to see all of the files that are associated with the openoffice.org, run 'dpkg -L OpenOffice.org'.  A handy trick for finding a specific file is the 'locate' command.  Run 'locate <file-name>' to get a list of all files that match whatever you supplied in <file-name>.  Note:  the locate command is essentially a database search program.  To update the database, run 'sudo updatedb'.  I think ubuntu does this for you occasionally, but I'm not sure.

---

### Post by jeff0149 on 2007-07-09
Those were great suggestions.  I tried them and found the executable file.  My problem is that the software I am trying to configure is not accepting the location of the exe file.  I guess I will have to find some support for gnuaccounting.

Thanks for your help.
Jeff0149

---

