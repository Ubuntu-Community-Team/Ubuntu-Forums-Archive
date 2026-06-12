---
title: "Problem Printing from Acrobat"
date: 2014-11-04
forum: General Help
---

### Post by wjbmd48 on 2014-11-04
Hi:

I have a peculiar problem printing from pdf documents to my HP Laserjet 2012 (HPLIP driver), which is that the default size is 3x5.  It has to be manually changed to "US letter" every time; annoying, but not a killer.

To reiterate, this doesn't happen out of any other app, only with both pdf apps (PDF reader and Foxit), and it's present on all 4 systems (really!) I have running Lubuntu 14.04/14.04.1.

Others have reported this, I've seen no solutions:

[http://gotoanswer.stanford.edu/problem_with_printing_pdfs-6115813/](http://gotoanswer.stanford.edu/problem_with_printing_pdfs-6115813/)

Any ideas/fixes?

Bill

---

### Post by whitesmith on 2014-11-04
See [http://askubuntu.com/questions/186779/why-did-adobe-stop-flash-player-for-linux](http://askubuntu.com/questions/186779/why-did-adobe-stop-flash-player-for-linux), which explains why Adobe stopped development of Flash for Linux (in March 2014, I believe). Eventually the company plans to drop Flash entirely in favor of features and facilities in HTML5. In the meantime you may try Lightspark. Lightsprk is  a tool like the original Acrobat, not the bloatware that Acrobat turned became. I had severe printing problems until I made the switch. Everything is fine now. Regards.

---

### Post by wjbmd48 on 2014-11-04
Thanks for the reply, but I'm not sure what lightspark/flash has to do with printing out of pdf format from an acrobat reading program?

Thanks again,

Bill

---

### Post by tgalati4 on 2014-11-05
Look at the printer's default settings in CUPS:  [http://localhost:631](http://localhost:631).  You should be able to set Letter or A4 as the default page size, then save the preferences.  It's possible that there is a bug in that particular printer.

---

### Post by wjbmd48 on 2014-11-11
Thanks for that, but, no, the CUPS administrator shows 8.5x11 as the default size.

Oh, well, maybe I'll try swapping out the printer with my wife's Mac-attached HP, see what happens.

Again, thanks for taking the time.

Bill

---

### Post by tgalati4 on 2014-11-11
Try deleting the printer in CUPS then reinstall using the* hplip*.

Open a terminal:

```
hp-toolbox
```

---

### Post by wjbmd48 on 2014-11-19
Nope, no joy. I was hopeful that the recommended gui-hplip would help, but no.  Both in CUPS and in the HPLIP utility, it shows 8.5x11 as the default size, which indeed is how it prints out of everything *except* pdf reader and Foxit.

Oh, well, first world problem, no biggie.

Thanks, everyone.

Bill

---

