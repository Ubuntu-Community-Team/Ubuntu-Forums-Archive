---
title: "Make perl script start on linux startup?"
date: 2008-04-05
forum: General Help
---

### Post by Petrock6 on 2008-04-05
Hello guys.
I'm running a Perl linux script for a friend on my server.
I keep forgetting to run it EVERY TIME i reboot.
How can i make a PERL [YES PERL!] script start on startup? Thank you.

---

### Post by jpeddicord on 2008-04-05
The easy way? Add it to crontab, as long as it is marked +x (executable):

```
crontab -e
```
And in the editor:
```
@reboot /full/path/to/script
```

Press Ctrl-X, hit Y to save. @reboot isn't the normal crontab syntax you see out there; it's one of those special keywords.

---

### Post by Petrock6 on 2008-04-05
Thanks a ton.

---

