---
title: "extraction of files issue"
date: 2013-05-17
forum: General Help
---

### Post by Hex9 on 2013-05-17
I'm unsure why im even having trouble with this....
All i am doing is attempting to extract the files inside a tar.gz folder to a specified folder. eg, the files inside apr-1.4.6.tar.gz inside the folder srclib
as follows:
tar -zxf apr-1.4.6.tar.gz -C srclib/

I've read in the man page but i cant see anything but the -C option, this is the same on google too. The tar.gz always extracts as follows:

srclib/apr-1.4.6.tar.gz/(files)

I'm probably making a really stupid mistake..
Can anyone see it?

---

### Post by steeldriver on 2013-05-17
I don't see anything that you're doing wrong - it may just be that the archive was created like that (i.e. the directory structure was xxx/apr-1.4.6.tar.gz/files when the archive was created) - try opening it in the GUI filemanager using 'Archive Manager', you should be able to see the directory hierarchy inside

---

### Post by scbingham on 2013-05-17
It might be something to do with explicit path names when the archive was created. Try:

tar xvf apr-1.4.6.tar.gz -C /srclib or -C ../srclib (probably the latter actually)
(the 'z' is redundant & 'v' means verbose, so you can see the files extracting)

Failing that, Archive Manager is a friendly GUI. Hope this helps.

---

