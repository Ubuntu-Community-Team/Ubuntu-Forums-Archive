---
title: "Kubuntu Edgy: Power Managment - Monitor Settings Never Saved"
date: 2006-11-26
forum: General Help
---

### Post by guyforget on 2006-11-26
Im using Kububtu Edgy w/ everything up to date.  

When I go from System Settings > Monitor & Display > Power Saving

And change the amount of time that elapses before the monitor shuts itself off, the value is never saved.  Its currently set to 5 hours.  I try to change it to 15 minutes but every time I open it back up its set to 5 hours again. Ive set it as user, Ive set it as root, Ive set it as user after clicking to Admin Mode and entering my password.  Ive installed KControl and gone in through it and changed it to 15 minutes.  But nothing works.  Its always set back to 5 hours no matter what.  

What gives?  Any tips?  I just started using Kubuntu after using Gnome for at least 3 years.  Ive pretty well got everything else worked out to my liking, but I cant seem to get this one to stick.  

Thanks in advance.

Edit:  OK, I just read this: [http://ubuntuforums.org/showthread.php?t=283364](http://ubuntuforums.org/showthread.php?t=283364) and I guess there is no fix?  Lame.

---

### Post by esaym on 2006-11-26
same problem in 6.06 kubuntu

try adding ```
Option "OffTime"	"15"	# Turn off (DPMS)
```under Section "ServerLayout" in xorg.config;)

---

### Post by jeremy on 2006-12-09
> **esaym said:**
> same problem in 6.06 kubuntu

try adding ```
Option "OffTime"	"15"	# Turn off (DPMS)
```under Section "ServerLayout" in xorg.config;)
This doesn't work in Kubuntu Edgy, there is a workaround at:
[http://ubuntuforums.org/showthread.php?p=1819397](http://ubuntuforums.org/showthread.php?p=1819397)

---

