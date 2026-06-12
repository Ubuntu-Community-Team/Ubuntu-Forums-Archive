---
title: "Can't find driver file."
date: 2007-04-25
forum: General Help
---

### Post by krelverehan on 2007-04-25
Hello everyone,

I am currently trying to install my lexmark z816 printer and I can't seem to find the driver package.

All leads currently point to [cerqueira.org]("http://cerqueira.org")  but the site seems to be down. Are there any mirrors to file I am looking for, or does anybody know when the site might come back? I gave quite a bit of time trying to find a mirror with no luck what so ever.

Thanks,
-KV

---

### Post by BoneKracker on 2007-04-25
You might try this site:

[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

---

### Post by krelverehan on 2007-04-25
Unfortunately it just links to [http://cerqueira.org/software/z810/]("http://cerqueira.org/software/z810/")

---

### Post by BoneKracker on 2007-04-25
Ah, I see.

Lexmark has somewhat spotty support for Linux.  I'm not familiar with that printer.  About the only thing I can suggest is trying:

a) one of the somewhat generic drivers that come with cups (in /usr/share/cups/model/, I think)
b) a driver for a similar printer, preferably in the same series and slightly older

---

### Post by BoneKracker on 2007-04-25
I assume you checked and it's not in the foomatic database.  (If installed, foomatic will generate a ppd file -- i.e. driver -- for any printer that's in it's database).

---

### Post by krelverehan on 2007-04-25
Checking foomatic was the first thing I did. I actually spent a deal of time last night trying every other lexmark driver to see if one would work, but none would. And I tried all the generic printers and none seemed to work either. The best I got was some of them would just feed the paper through, but wouldn't print.

---

