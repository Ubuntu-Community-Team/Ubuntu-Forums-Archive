---
title: "Can not print from Firefox"
date: 2005-05-09
forum: General Help
---

### Post by rmmcgr on 2005-05-09
Hi,

For some reason when I print from Firefox I get no output from the printer.  When I select File -> Print, I get the print dialog box and can click OK, but nothing comes out.

All other programs, such as Open Office, print with no problems.

I am using the default 'Human' theme (have seen some comments about themes affecting firefox??).

Any suggestions?  Is this a known bug? (Work around?).  

Printer is a Samsung SCX-4100 (which came with Linux drivers).

Thanks,
Richard

---

### Post by Toddy on 2005-05-09
See this thread for using gtklp to print from apps like firefox:

[http://www.ubuntuforums.org/showthread.php?t=24850&highlight=gtklp](http://www.ubuntuforums.org/showthread.php?t=24850&highlight=gtklp)

---

### Post by rmmcgr on 2005-05-10
Yes, thank you.

Installing gtklp solved the problem.  I installed the package, then in Firefox selected File->Print.  In the print dialog box I clicked properties, then changed lpr <options> to gtklp <options>.  

It is a shame that with this solution users get two dialog boxes to negotiate when printing from firefox (the firefox one and the gtklp one) but at least I can now print.

(There is probably a setting somewhere for gtklp to just use the defaults and not put up its own print dialog box, but short of a quick and obvious GUI control panel for it, I will have to search around more).

Thanks again for the pointer to the thread....Richard

---

