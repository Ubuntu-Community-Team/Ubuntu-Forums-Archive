---
title: "Question about scripts."
date: 2006-09-06
forum: General Help
---

### Post by Roasted on 2006-09-06
Say I'm downloading a lot of stuff and my automatic scheduled time of the day comes up where my script runs. My script automatically mounts my spare drive, sync's everything in my home folder from Drive A to Drive B (spare), then unmounts it.

But, while I'm downloading, my files are downloading to a specific folder within my home folder, and since Drive B copies my home folder + everything in it, would that cause any harm? Because realistically, while B is copying the home folder, there's still files being added as I download... or would it just skip over that, copy what's available at that very milisecond, and just keep moving?

---

### Post by mssever on 2006-09-07
That shouldn't be a problem, but it would depend on how the script's written. You should probably read the script docs or check with the author.

You might also consider installing unison (and unison-gtk) from the universe repository. It might make your life easier. Docs are available by typing ```
unison -doc topics | less
``` after you install.

---

### Post by Roasted on 2006-09-07
The script is simply mount drive, rsync home from A to home on B, unmount. The end.

---

### Post by Tomosaur on 2006-09-07
You can make rsync skip a file/directory by using the
--exclude-from=FILE

option on it.

---

