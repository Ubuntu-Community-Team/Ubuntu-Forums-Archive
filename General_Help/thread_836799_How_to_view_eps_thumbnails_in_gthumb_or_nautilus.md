---
title: "How to view eps thumbnails in gthumb or nautilus?"
date: 2008-06-21
forum: General Help
---

### Post by stevieP on 2008-06-21
I have a very simple question that I couldn't find the answer to on the forums:

How do I get gthumb or nautilus to view .eps thumbnails? 

I have installed gs-gpl, and have ghostscript installed, but I still can't see any thumbnails for .eps and .ps files. 

stevieP

---

### Post by cariboo on 2008-06-21
Have you tried gimp? it is located in Application-->Graphics--> Gimp. Gimp will save as eps so I sure it can open eps files.

Jim

---

### Post by stevieP on 2008-06-22
> **cariboo907 said:**
> Have you tried gimp? it is located in Application-->Graphics--> Gimp. Gimp will save as eps so I sure it can open eps files.
Thanks Jim. However I am actually looking to display thumbnails for a large number of eps files, not necessarily open or edit individual files with gimp or Imagemagick, etc. 

gthumb (or nautilus) does an excellent job of displaying thumbnails for jpg and gif files, but it seems that apparently some extra software needs to be downloaded for it to work with eps and ps files....

---

### Post by stevieP on 2008-06-22
> **stevieP said:**
> ...but it seems that apparently some extra software needs to be downloaded for it to work with eps and ps files....
Actually nautilus is able to display thumbnails for .ps files on my computer, but not .eps files, while gthumb can not display either .ps or .eps (I'm more interested in fixing gthumb).

---

### Post by stevieP on 2008-06-25
awww cmon, doesn't anybody know about this? b-b-b-ump...

---

### Post by stevieP on 2008-06-25
I've found out there used to be a viewer that could do this, i.e. that could view PNG, JPEG, TIFF, GIF, NetPBM, and if ImageMagick is installed,  PSD, TGA, EPS, PICT, DCX, PCX, MIF, BMP, VIFF, and PNM. 
That was **PikView**:
[http://pikview.sourceforge.net/](http://pikview.sourceforge.net/)

Unfortunately its unavailable on synaptic, so you can try and download the sources and install it manually. The software hasn't been updated since 2001 as far as I can tell, and even the executable "pv" has been taken by another package on synaptic, Pipe viewer.

Unfortunately my attempt at a manual install failed, and I am not proficient enough at deciphering error messages in configure logs to figure out what to do. 

Here are the error messages anyway:


First error msg:

```
configure:2924: error: '__CYGWIN32__' undeclared (first use in this function)
configure:2924: error: (Each undeclared identifier is reported only once
configure:2924: error: for each function it appears in.)
```


2nd error msg:

```
configure:2953: error: '__MINGW32__' undeclared (first use in this function)
configure:2953: error: (Each undeclared identifier is reported only once
configure:2953: error: for each function it appears in.)
```


Later on there were a bunch of errors involving the inclusion of headers, I think:

```
conftest.C:2:21: error: qglobal.h: No such file or directory
conftest.C:3:26: error: qapplication.h: No such file or directory
conftest.C:4:18: error: qapp.h: No such file or directory
conftest.C:5:22: error: qobjcoll.h: No such file or directory
conftest.C:6:20: error: qevent.h: No such file or directory
conftest.C:7:21: error: qstring.h: No such file or directory
conftest.C:8:20: error: qstyle.h: No such file or directory
conftest.C:9:23: error: qiconview.h: No such file or directory
conftest.C:11:2: error: #error 1
conftest.C: In function 'int main()':
conftest.C:15: error: 'QStringList' was not declared in this scope
conftest.C:15: error: 't' was not declared in this scope
conftest.C:15: error: expected type-specifier before 'QStringList'
conftest.C:15: error: expected `;' before 'QStringList'
conftest.C:16: error: 'QIconView' was not declared in this scope
conftest.C:16: error: expected `;' before 'iv'
conftest.C:17: error: 'iv' was not declared in this scope
conftest.C:18: error: 'QString' was not declared in this scope
conftest.C:18: error: expected `;' before 's'
conftest.C:19: error: 's' was not declared in this scope
conftest.C:20: error: 'QEvent' has not been declared
conftest.C:20: warning: unused variable 'magnolia'
configure: failed program was:
#include "confdefs.h"
#include <qglobal.h>
#include <qapplication.h>
#include <qapp.h>
#include <qobjcoll.h>
#include <qevent.h>
#include <qstring.h>
#include <qstyle.h>
#include <qiconview.h>
#if ! (QT_VERSION >= 222)
#error 1
#endif
```


Would there be any interest in making PikView available to Ubuntu users via Synaptic???

stevieP

---

### Post by stevieP on 2008-06-27
I'm still hoping someone who knows how to solve this problem notices my troubles. This problem is listed as "solved" on the launchpad ubuntu forums,
[https://answers.launchpad.net/ubuntu/+source/gthumb/+question/15504](https://answers.launchpad.net/ubuntu/+source/gthumb/+question/15504)
where someone (mike-g2) found that by installing gs-gpl they were able to view pdf and eps files in gthumb. 

I went ahead and did that- now gs-gpl is listed on Synaptic as a "transitional package"  and is replaced by ghostscript. Installing gs-gpl does not solve the problem now, unfortunately...

---

