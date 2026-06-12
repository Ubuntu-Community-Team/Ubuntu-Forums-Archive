---
title: "Wine error - could not load psapi.dll"
date: 2007-11-08
forum: General Help
---

### Post by rainwalker on 2007-11-08
I'm trying to run the Sony Ericsson PC Suite software on my Gutsy install with Wine (from the repos),  but about halfway through it tells me
> ERROR: Could not load c:\windows\system32\psapi.dll

What does this mean? And what can I do about it?

---

### Post by hikaricore on 2007-11-08
I'm not quite sure how well mobile phone software will work under WINE in the first place.  O.o

Is there any way you can do what you are attempting with BitPim ([http://www.bitpim.org/](http://www.bitpim.org/))?
BitPim is also in the Universe repos (you'll need them enabled):

```
sudo apt-get install bitpim
```

Not sure if this helps at all but just offering alternatives.

Worse comes to worse find and download that file and put it in:

~/.wine/drive_c/windows/system32

---

