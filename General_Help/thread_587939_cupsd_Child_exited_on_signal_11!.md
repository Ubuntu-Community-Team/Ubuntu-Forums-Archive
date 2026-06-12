---
title: "cupsd: Child exited on signal 11!"
date: 2007-10-23
forum: General Help
---

### Post by trymbill on 2007-10-23
I am trying to set up a print server @ home with Ubuntu but I keep getting this error when I try to start cupsys.

Does any one know what could be wrong?

---

### Post by Jorn.jambers on 2007-10-23
First of all, signal 11 is a segmentation fault.

I think this will help you:
[http://ubuntuforums.org/showthread.php?t=366507](http://ubuntuforums.org/showthread.php?t=366507)

---

### Post by mregan on 2008-02-05
I had the same problem after trying to configure a new printer.

I finally tracked it down to the /etc/cups/cupsd.conf file. 

The file had been updated without the ServerName being set. I edited the file to show:

ServerName localhost

and everything started OK.

Hope that helps

---

