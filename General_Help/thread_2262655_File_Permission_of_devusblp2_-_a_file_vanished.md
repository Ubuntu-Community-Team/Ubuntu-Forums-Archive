---
title: "File Permission of /dev/usb/lp2 - a file vanished?"
date: 2015-01-26
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-01-26
I tried to find a way to see ink levels of my ink-jet printer and noodling around the 'net saw a Linux command line app: "ink" I installed it and tried the command line to see the levels of ink remaining. FAIL.

But the weblog from which I got this info, had the file permissions of /dev/usb/lp2 (lp2 is my Brother MFC-240C printer) changed to 666.

What are the default file permission for USB printer-scanner-fax devices? Are they by the device's ROM or by the OS?

And when I used "gksudo nautilus" to look at that file, it doesn't exist. Nautilus shows only hiddev0 and hiddev1. Using CTRL-h does not show more files. From the command line, using "locate" and searching for "lp2" shows no such named file.

The Brother's ability to scan and print are unaffected. I don't want to leave files vulnerable to malware or other intrusion.

On my own, I found some more info. This is added on 27-Jan-15. 

```
mark@Lexington:~$ ls -l /dev/usb/lp* /dev/bus/usb/*/*

crw-rw----+ 1 root lp   180,   2 Jan 27 10:40 /dev/usb**/lp2**
```

Which I found at: [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) and that page says that the permission should be "crw-rw-r--" so mine is missing an -r. How do I change that one? Is it necessary?

---

