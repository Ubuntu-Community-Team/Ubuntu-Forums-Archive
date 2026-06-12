---
title: "Need the help of someone clever to get aMSN working fully"
date: 2006-12-18
forum: General Help
---

### Post by happy-and-lost on 2006-12-18
After much Googling, I've found out how to fix the aMSN file sending problems I've encountered by means of pressing Ctrl-S at the main screen and entering:

```
set ::abook::demographics(listening) true
```

Which, I assume, edits the /usr/share/amsn/utils/abook.tcl file (I may be very wrong!) to set listening to true (Otherwise aMSN just reports that I'm behind a firewall). This is, however, only a temporary fix, and it's reset when aMSN is closed. I think the key to fixing this lies in the above file, but as my programming knowledge is incredibly limited, I don't know where or what!

I've enclosed the suspect file for your delectation. It'll be obvious to anyone smarter than me!

---

