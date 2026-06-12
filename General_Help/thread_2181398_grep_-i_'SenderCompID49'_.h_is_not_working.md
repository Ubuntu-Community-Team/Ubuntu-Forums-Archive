---
title: "grep -i 'SenderCompID*49' *.h is not working"
date: 2013-10-17
forum: General Help
---

### Post by vincegata on 2013-10-17
Hi,

I run this grep line: 
 grep -i 'SenderCompID*49' *.h

but it's not finding anything. However I know there is a header file containing SenderCompID = 49.

Any help with grep,
THX

---

### Post by steeldriver on 2013-10-17
grep expects matches to be in regular expression (regex) format - which is not quite the same as shell wildcards i.e. for 'any number of any characters' you need .* instead of plain *

```
grep -i 'SenderCompID**.***49' *.h
```

---

### Post by vincegata on 2013-10-17
I see, big thanks.

---

### Post by Lars Noodén on 2013-10-18
[globbing](http://manpages.ubuntu.com/manpages/raring/en/man7/glob.7.html) is what you see with paths and filenames.  It uses some of the same symbols as regex, but with different meanings, so it can be confusing because it is something different.

---

