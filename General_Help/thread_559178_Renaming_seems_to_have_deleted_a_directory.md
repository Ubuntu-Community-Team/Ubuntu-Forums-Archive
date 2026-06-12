---
title: "Renaming seems to have deleted a directory"
date: 2007-09-24
forum: General Help
---

### Post by Sweet Spot on 2007-09-24
I don't understand how this could have happened, but it did. I was attempting to put the location of a directory into the terminal in order to join some video files, but every time I put the location in, I was told the directory did not exist. 

Eventually I tried renaming the directory which WAS: 1- Vids" to simply "Vids"

Afterwards, I could not even find the vids directory anymore ! ? I closed and opened Nautilus again, but that was futile. And now, after doing god knows what, the original directory is back, but it has only 3 of the sub folders which were in it originally. 

How the hell can something like this happen, and are the other sub folders recoverable ?  I looked in the trash, nothing is there. And I most certainly did not give any delete command. This is really puzzling.

---

### Post by lisati on 2007-09-24
Does ```
dir
``` tell you anything useful from the terminal?

---

### Post by Adramelech on 2007-09-24
How did you renamed the directory? 
Im pretty sure the problem is with the '-' character, that character is used to pass options to commands, when you use it, the command parser get confused and misbehave, do not use '-' on file names, if you already have files with that character, enclose the filename on "" when using commands.

---

### Post by Sweet Spot on 2007-09-24
> **lisati said:**
> Does ```
dir
``` tell you anything useful from the terminal?

Not really, no. Thanks though. 

> **Adramelech said:**
> How did you renamed the directory? 
Im pretty sure the problem is with the '-' character, that character is used to pass options to commands, when you use it, the command parser get confused and misbehave, do not use '-' on file names, if you already have files with that character, enclose the filename on "" when using commands.

Geeesh... Wish I had known this before ! I can see how this would lead to problems if one doesn't know about it. Ah well. Thanks.

---

