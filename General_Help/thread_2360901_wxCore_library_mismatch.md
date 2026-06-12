---
title: "wxCore library mismatch"
date: 2017-05-09
forum: General Help
---

### Post by alissa-schmidt90 on 2017-05-09
Hello, all.

I'm having an IDE issue which originated post upgrade from 16.10 to 17.04.  The IDE I was using -- CodeLite -- stopped running with the following error message in console:
Fatal Error: Mismatch between the program and library build versions detected.
The library used 3.0 (wchar_t,compiler with C++ ABI 1009,wx containers,compatible with 2.8),
and wxCore used 3.0 (wchar_t,compiler with C++ ABI 1010,wx containers,compatible with 2.8).
Aborted

This same error message crops up when I try to use wxCrafter and Code::Blocks.
Clearly there's a problem with compiler mismatch between those tools and wx.  I've removed and re-installed Codelite, wxCrafter, and Code::Blocks, as well as all of my wx libraries, however this error persists.  Installation is being done from repositories on all accounts, and I've reached the limit of my ability to find a solution to this particular problem.  Is this a situation where I'm going to just have to suck it up and build everything from source?  Or is there an easier way?

Thanks!

---

### Post by mc4man on 2017-05-09
Maybe just rebuild wxwidgets3.0? It would seem the GXX_ABI_VERSION mismatch should only be a warning, not fatal.
Older bug in Fedora - [https://bugzilla.redhat.com/show_bug.cgi?id=1200611](https://bugzilla.redhat.com/show_bug.cgi?id=1200611)
Of file an Ubuntu bug on wxwidgets3.0

---

