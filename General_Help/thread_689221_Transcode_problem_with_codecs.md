---
title: "Transcode problem with codecs"
date: 2008-02-06
forum: General Help
---

### Post by jkbowle on 2008-02-06
I'm running mythtv and one of the plugins is using transcode to compress my Dvd's.  Problem is when I use xvid as my export module.. I get segmentation faults every time.

I tried switching and using divx instead, but transcode says that it can't find library "libdivxencore.so.0".

I used the find command and didn't find that library anywhere in my filesystem.

What packages/apps do I need to install to get that library.  I already installed avifile-divx-plugin.. but that didn't install the libdivx libraries.

So now I'm stuck.. I have to import my DVD's at full size until this is fixed.

anyone have suggestions or similar problems?

---

### Post by wesley_of_course on 2008-02-06
Have you installed ubuntu -restricted-extras ?  
     Code:
   >   [SIZE=-1]sudo apt-get install ubuntu-restricted-extras[/SIZE]                                               Hope this helps .

---

