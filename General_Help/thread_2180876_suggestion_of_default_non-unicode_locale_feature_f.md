---
title: "suggestion of default non-unicode locale feature for many applications"
date: 2013-10-15
forum: General Help
---

### Post by xuancong on 2013-10-15
Dear Ubuntu Programmer,

I am now proposing a new and very useful feature for Ubuntu, called "default non-unicode locale" (such as those in Windows).

The problem is that when Ubuntu is accessing some DOS/windows file-systems, or some media files like mp3/mp4/etc, some  contains a combination of unicode and non-unicode filenames, folders and texts. Multimedia applications like Rhythmbox/VLC-player/KMPlayer never displays artists and album names perfectly for mp3/mp4/etc... This is because some text are in UTF8, some are in GBK (I'm from China). There're many other cases where the text cannot be displayed properly and garbage codes are shown.
In general, regardless of any application, the OS shall NOT assume that all non-ascii characters are in UTF-8. This is because the user may choose a particular code page for efficient encoding of text in his/her own language (e.g. gbk/gb18030 for Chinese, tis-620 for Thai, etc). Therefore, I strongly suggest that we should introduce "default non-unicode locale" into Ubuntu's system setting, like those in Windows, so that if a string cannot be displayed in unicode, then the default non-unicode locale is chosen.

It's going to be very useful as you will see.

Wang Xuancong

---

