---
title: "Opening a program in a terminal"
date: 2007-04-01
forum: General Help
---

### Post by abuntoyoutoo on 2007-04-01
I'm trying to write a command that will open a terminal, then the opened terminal opens vim. When I quit vim, the terminal vim was opened in remains open. How can you do this?

What I came up with so far was:
```

konsole -e vim afile.txt

```
However, when vim is closed, the opened terminal window also closes.
Note that I am using this for a program script, so the actual script will be something like ```
konsole -e vim %F
```

---

### Post by tribble222 on 2007-04-01
So you want the terminal to stay open even after vim is closed?  Can you just add a & to the end of the command?

---

### Post by abuntoyoutoo on 2007-04-01
> **tribble222 said:**
> So you want the terminal to stay open even after vim is closed?  Can you just add a & to the end of the command?

Not quite. Putting the & at the end of the command, like
```

konsole -e vim afile.txt &

```
means that the terminal that started the command doesn't wait for it to finish. The konsole terminal created by the command quits like before when vim is closed. Is that what you meant?

---

### Post by tribble222 on 2007-04-03
Oh, I see what you mean.  It seems that when you use -e then no matter what you tell the terminal to execute, it exits that terminal when the process ends.  Maybe what you need to do is find a way to open a terminal normally and then, after it's open, make it execute the vim command.  I'm not sure how this could be accomplished or if it is even possible, but it would probably involve finding (or creating) a unique ID for the terminal you launched and then passing the command to it somehow.  Sorry I can't be of more help!

---

