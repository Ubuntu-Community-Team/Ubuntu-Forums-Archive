---
title: "A little help with Wine needed!"
date: 2007-03-29
forum: General Help
---

### Post by Fireblend on 2007-03-29
Hey! I finally managed to make one of my windows programs (Fireworks) run under Linux, but for some reason I can't make a launcher. On the launcher command I type 

> wine /home/user/.wine/drive_c/Program Files/Macromedia/Fireworks 8/Fireworks.exe

And nothing happens
If I type it on a terminal, it says "cannot find '/home/moresq/.wine/drive_c/Program'"

Most guides I used to do this told me to type it that way. I guessed that happened because the directory "Program FIles" has a space, so I typed it like Program_Files (same with FIreworks 8) and it still says it cannot find the file. How can I solve this little problem of mine?

Thanks in advance!

---

### Post by nikhilk on 2007-03-29
Try escaping the space between Program and Files. Try this command
```
wine /home/user/.wine/drive_c/Program\ Files/Macromedia/Fireworks 8/Fireworks.exe
```

---

### Post by Fireblend on 2007-03-29
> **nikhilk said:**
> Try escaping the space between Program and Files. Try this command
```
wine /home/user/.wine/drive_c/Program\ Files/Macromedia/Fireworks 8/Fireworks.exe
```


That worked! I had to add the "\" for the "Fireworks 8" directory too.

Thanks!

---

### Post by nikhilk on 2007-03-29
> **Fireblend said:**
> I had to add the "\" for the "Fireworks 8" directory too.
Oops! I missed that, but you got it working :)

---

