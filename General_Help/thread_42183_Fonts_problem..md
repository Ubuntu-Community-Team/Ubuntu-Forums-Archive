---
title: "Fonts problem."
date: 2005-06-16
forum: General Help
---

### Post by arunsub on 2005-06-16
I have problem with fonts on some applications like XMMS, Yahoo Messenger, Skype etc. Not all are affected. The fonts are fine in Firefox etc. I don't know if that happened after i installed msttcorefonts or before that. I have given the link to the screen shot. Can anyone tell me how to correct this?
[http://tech.arun-prabha.com/screenshot.htm](http://tech.arun-prabha.com/screenshot.htm)

Thanks.

---

### Post by GTvulse on 2005-06-16
Go to System->Preferences->Font->Details and Check Smothing-> none, Hinting->full. Also look at the font HOW-TO threads:

1. "Rocking fonts in Gnome" [http://ubuntuforums.org/showthread.php?t=23426](http://ubuntuforums.org/showthread.php?t=23426)
2. "Cleartype-like fonts" [http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

---

### Post by arunsub on 2005-06-16
Thanks. I'll try that.

---

### Post by angkor on 2005-06-16
To make Skype look a little better:

```
apt-cache search qtconfig
qt3-qtconfig - The Qt3 Configuration Application
``` 

With this tool you are able to adjust the font(size) in skype and other qt applications.

---

### Post by arunsub on 2005-06-16
I'll try that. You're signature is pretty good.

---

### Post by angkor on 2005-06-16
*grins*

Thought so too, stole it from a LinuxQuestions-user. :)

---

### Post by arunsub on 2005-06-16
[QUOTE=dradul]Go to System->Preferences->Font->Details and Check Smothing-> none, Hinting->full. Also look at the font HOW-TO threads:

1. "Rocking fonts in Gnome" [http://ubuntuforums.org/showthread.php?t=23426](http://ubuntuforums.org/showthread.php?t=23426)
2. "Cleartype-like fonts" [http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)[/QUOTE]
I tried the options you specified and the thread you posted here. I think AMsn looks better now, but all other applications that were affected earlier like Yahoo, XMMS etc are still the same as i showed in the screen shot. Skype is ok. no problem. Any idea how to change those?

---

### Post by GTvulse on 2005-06-16
Because those are GTK+ 1.x applications and follow different rules. I think this thread [http://ubuntuforums.org/showthread.php?t=39446](http://ubuntuforums.org/showthread.php?t=39446) explains it better than I could. :-)

---

### Post by arunsub on 2005-06-16
Thanks for the link.

---

