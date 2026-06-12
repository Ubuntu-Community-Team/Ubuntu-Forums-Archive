---
title: "Cursor rendering issue"
date: 2013-05-26
forum: General Help
---

### Post by kill o matic on 2013-05-26
I've been using this cursor theme with shadow and transparency effects called ComixCursors, but when I reinstalled it in raring the shadow somehow turned into a transparent grey square around the cursor. I'd post a screenshot, but the mouse cursor doesn't seem to get captured with print screen.

Edit: I checked and this is happening straight from the Live USB, so it's probably not something I messed up. Can someone else confirm this?

---

### Post by kill o matic on 2013-05-28
Alright, figured out how to take screencap with cursor.

---

### Post by SantaFe on 2013-05-29
I had the same problem.  Even posted it here: [https://forum.xfce.org/viewtopic.php?id=8045](https://forum.xfce.org/viewtopic.php?id=8045)

Finally found this page: [http://xfce-look.org/content/show.php/ComixCursors?content=32627&PHPSESSID=a2fa486d4a26fc7a060d1d8d1f540084](http://xfce-look.org/content/show.php/ComixCursors?content=32627&PHPSESSID=a2fa486d4a26fc7a060d1d8d1f540084)

I used Synaptic Package Manager to remove the Comic Cursor cursors from my system, then extracted the file & put the Comic Cursor folders into usr/share/icons and now the background is gone. ;)

---

### Post by kill o matic on 2013-05-29
Well spotted =D>. It seems the art was changed in the 13.04 package, giving all the cursors backgrounds with non-zero transparency for some reason. It's obvious when you compare the thumbnails in gimp from the quantal package and the raring one. I guess nobody uses these cursors anymore if it went unnoticed til now :(. So, how do you get in touch with the package builder?

---

