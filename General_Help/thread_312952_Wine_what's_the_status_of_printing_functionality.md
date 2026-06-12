---
title: "Wine: what's the status of printing functionality?"
date: 2006-12-05
forum: General Help
---

### Post by cogitordi on 2006-12-05
Using Drake. 

I have found trying to configure printing in Wine to be the sort of miserable time-wasting experience that I had come to expect from Windows. But I am assuming that Wine doesn't seek to emulate the ~misery~ of Windows as well. ;^)

The documentation on the Web is mostly out of date. Config files here, config files there, yes you have to edit the registry, no you don't have to edit the registry. And then, consider the documentation statement:
"If you are using CUPS, you do not need to configure .ini or registry entries, everything is autodetected." 

I have CUPS running. I can print from Linux applications. I can print a test page from CUPS. But I can't get printing in Wine to work, either to the printer or to a PS file. All printing options are disabled in my Wine applications. 

IS this supposed to work at all? ](*,)

---

### Post by schnucki on 2006-12-08
Hi! 
Have you installed cupsys-bsd? (Attention: I'm a Debian user - don't know if this package is part of Ubuntu basic installation...) Tried for hours to print with wine, finally discovered that just "lpr" does not work.... ;)
Maybe I could help you - your posting really made me laugh. Just experienced the same: config - no more config, now it's regedit e.g.
And: After half a day of googling for "cups wine" I know really a lot about wine and wine-cups.....

---

### Post by cogitordi on 2006-12-11
> **schnucki said:**
> Hi! 
Have you installed cupsys-bsd? (Attention: I'm a Debian user - don't know if this package is part of Ubuntu basic installation...) Tried for hours to print with wine, finally discovered that just "lpr" does not work.... ;)
Maybe I could help you - your posting really made me laugh. Just experienced the same: config - no more config, now it's regedit e.g.
Yes, cupsys-bsd is installed. The executable lpr exists but the command lpr <filename> does nothing.
> **schnucki said:**
> 
And: After half a day of googling for "cups wine" I know really a lot about wine and wine-cups.....
Then you are a better man than I, Sir. After two days of searching for "cups wine" I just gave up and drank several cups of wine.

---

### Post by cogitordi on 2006-12-13
Wine has been updated to wine-0.9.27 and printing to the "default" printer is now enabled. I can't change the print settings from within a Windows application, but I can live with that.

---

