---
title: "[SOLVED] checkgmail"
date: 2008-03-22
forum: General Help
---

### Post by dlstrife on 2008-03-22
I installed checkgmail in gusty and installed all dependencies it asked for. It gives me the following when I try to run it through terminal (if I run it through the applications menu it just doesn't run):

Specification mandate value for attribute COS
attributes construct error
error parsing attribute name
attributes construct error
xmlParseStartTag: problem parsing attributes
Couldn't find end of Start Tag label_delay line 15 at /usr/lib/perl5/XML/LibXML/SAX.pm line 64
 at /usr/share/perl5/XML/Simple.pm line 299
A thread exited while 2 threads were running.

I've tried reinstalling several times, reboots to make sure the new packaged were fully recognized, and I also followed this guide [http://colorfulcuriosities.blogspot.com/2008/02/checkgmail-alternative-gmail-notifier.html]("http://colorfulcuriosities.blogspot.com/2008/02/checkgmail-alternative-gmail-notifier.html") for adding the dependencies manually. No change. Still receive this error message. The funny thing is it worked the very first time I installed it, then my system froze due to a mounted drive losing its connection and when I did a hard reboot, checkgmail stopped working. Any ideas?

---

### Post by dlstrife on 2008-03-22
bump

---

### Post by dlstrife on 2008-03-24
bump

---

### Post by dlstrife on 2008-03-25
bump. anyone?

---

### Post by dlstrife on 2008-03-26
Figured this out. If you have labels with whitespace in them checkgmail can't parse them correctly. I just renamed my labels without whitespace, but you could try putting in quotes in the gmail prefs. I don't know if that will work though. If you're getting this error, just delete the prefs file in the ~/.checkgmail directory and you can load gmail again.

---

