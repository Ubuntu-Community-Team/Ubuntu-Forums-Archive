---
title: "Lenmarck 3500-4500 series"
date: 2008-01-07
forum: General Help
---

### Post by hackarre on 2008-01-07
Hello to everyone,

For this xmas i was given a new pc and a Lexmarck printer. So the first thing i did was to delete vista :) and i installed Ubuntu 7.10 in my hard drive.

Everything works like a charm, but i haven't been able to install my new printer, it's a wifi printer, and the problem is that when i click on the printing icon, in which i am supposed to install new printers, since it isn't connected to the pc, and ubuntu doesn't recognize it automtuaclly, nothing appears.

So my question is: There is any other way of installing a wifi printer? 

I also tried reinstalling system-config-printer. But i still get this error:

hackarre@hackarre-desktop:~$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 4090, in <module>
    main(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 4064, in main
    mainwindow = GUI(start_printer, change_ppd)
  File "/usr/share/system-config-printer/system-config-printer.py", line 204, in __init__
    self.language = locale.getlocale(locale.LC_MESSAGES)
  File "/usr/lib/python2.5/locale.py", line 462, in getlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ca_AD


Thank you for your answers,

Greetings.

---

### Post by phidia on 2008-01-07
If you go [here]("http://openprinting.org/printer_list.cgi") and enter the exact model you can find the status of your printer in the open source driver world.
Most Lexmark printers are not supported-Lexmark does not make their source code available for linux devs. You can try a non-free program like turboprint. I don't use turboprint so I can't say how well Lexmark works through that.

---

