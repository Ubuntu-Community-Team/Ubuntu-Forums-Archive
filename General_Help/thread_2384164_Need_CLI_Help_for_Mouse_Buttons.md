---
title: "Need CLI Help for Mouse Buttons"
date: 2018-02-03
forum: General Help
---

### Post by th1bill on 2018-02-03
I researched and found the top code below as the normal and below it is what I need my four button Kensington Expert Mouse Track Ball to read at, swapping only the right and left clicks.  Will the command work work on Ubuntu 16.04 that has been updated to that was made Studio through the ppa.  I read that xmodmap will not work on 16.04 will not work on 16.04 but  installed it and it read my mouse switches but I'm an old and disabled Vietnam Veteran and don't want to kill this machine but everything on my right side only works some and I've had to become left handed.  If you can give a high sign that this is the way to go on the Terminal or correct me, I will really appreciate it.




xmodmap -e "pointer = 1 8 3 4 5 6 7 9 2"

xmodmap -e “pointer = 3  8 1 4 5 6 7 9 2”

My puter is an HP 400-224 with 12 gig of RAM and is ran by an AMD A-4000 processor.

---

### Post by again? on 2018-02-03
The xmod changes will only last for the session.
So if somethings not right , just log out and back in.
When it's what you want add the xmod command to ~/.Xmodmap
You only need to add the line of code that alters the mapping, not the default mapping as well.
eg all need in the file is something like
```
pointer = 3 8 1 4 5 6 7 9 2
```

eg I disable buttons 8 and 9

---

