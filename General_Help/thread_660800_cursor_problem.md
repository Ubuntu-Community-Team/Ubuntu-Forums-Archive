---
title: "cursor problem"
date: 2008-01-07
forum: General Help
---

### Post by ricnar456 on 2008-01-07
When a icon is double click for start a program, a little clock for wait the program start is showed, this is showed in certain programs to me firefox, pidgin, but other programs don't show nothing when you double click in the icon (opera, kdetv and more)

This is configurable? 
Is very bad don't know if the double clicking was made in right form, maybe one try again and two operas or kdetv start at the same time, is very annoying.

If anybody have the solution i appreciate very much and sorry for my bad english

ricnar

---

### Post by Nonno Bassotto on 2008-01-07
Each program has file named program.desktop somwhere (I'm not sure where they are located). This describes how a launcher should look, and it should execute when clicked. I think the difference is that some program have the line
```

startupnotify=true

```
while others don't.

---

### Post by ricnar456 on 2008-01-07
Yes, thats the problem, is solved now, thanks for all, now Opera start perfect and the others too.

ricnar

---

