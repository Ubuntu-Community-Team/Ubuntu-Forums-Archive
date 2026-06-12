---
title: "Multimedia keys"
date: 2008-06-10
forum: General Help
---

### Post by O-pos on 2008-06-10
Hello,

I have HP Pavilion and it comes with dedicated multimedia keys which I can't bring to life uner Ubuntu. Only right, left, up & down, as well as OK works, but nothing else (play/pause, forward, backward, stop, and some other buttons). Under xev these nonresponsive keys give this kind of output:

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

I can't use xbindkeys or Keyboard Shortcuts because they don't read these keys.

Any ideas how can I deal with it?

---

### Post by geraldm on 2008-06-10
The problem was encountered before.  Look for help on the community forums and HOWTOs.  I found this article:
[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

perhaps that is a start.  If you cannot find an answer already by searching the
forums, then perhaps the community needs to put the information in an obvious place for users to find.

Gerald

---

### Post by O-pos on 2008-06-10
Thanks, but I went through this couple of times, I also googled everywhere but found no solution.

---

### Post by avtolle on 2008-06-10
I do not know if this will be of any help to you, but have you looked under System>>Preferences>>Keyboard, then click on the Layout tab; there will be a two windowed panel which opens. There will be something listed in the keyboard model. Click on that, and another two window panel will come up. Under Vendors, scroll to Hewlett Packard. The bottom window will list a variety of keyboards. Perhaps one of those selections will assist you.

EDIT: I understand the computer is a laptop, but given various vendors' affinity for using the same codes for specialized keys on keyboards, just thought this might give you a chance to try some of the options out and see whether any of them work for you.

---

### Post by O-pos on 2008-06-10
I played with that too, no results.

---

