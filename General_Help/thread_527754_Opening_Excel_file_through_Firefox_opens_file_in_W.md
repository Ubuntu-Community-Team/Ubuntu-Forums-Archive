---
title: "Opening Excel file through Firefox opens file in Writer instead"
date: 2007-08-17
forum: General Help
---

### Post by timzak on 2007-08-17
On my fantasy football website, you can choose to open stats in Excel from Firefox.  However, each time I try this in Feisty, it opens the file in Writer instead.  I found an old thread on this topic and there was never a solution found, but I thought I'd re-ask to see if anyone knew of a solution.

Here's the old thread, which describes my problem exactly:
[http://ubuntuforums.org/showthread.php?t=148457](http://ubuntuforums.org/showthread.php?t=148457)

Just like the OP in the link above, this works correctly in Windows--the file opens in Excel.  But in Linux, when I download, it opens in Writer instead of Calc.

Any ideas?

---

### Post by PaulFr on 2007-08-17
Two ideas:

1. Can you save or create a sample .xls file on your system, and then follow the steps in **[http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/](http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/)**, then see if that helps in letting Firefox know what application to open ?

2. If that does not work, try the Edit -> Preferences -> Content entry in Firefox. Click the **Manage...** button in the **File Types** section to see the list of application actions defined. Check to see if there is any entry for .xls files - if so, I would suggest you remove it so hopefully Firefox will attempt to open it with the OS default.

Hope one of these helps.

---

