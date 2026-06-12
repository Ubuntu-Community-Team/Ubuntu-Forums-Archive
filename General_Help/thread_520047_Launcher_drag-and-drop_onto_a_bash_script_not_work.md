---
title: "Launcher drag-and-drop onto a bash script not working"
date: 2007-08-07
forum: General Help
---

### Post by imbjr on 2007-08-07
Try as I might, a perfectly functioning bash will not run if its run from a launcher from a panel or the desktop. I've tried %u and %f with and without quotes and .desktop, but it's not having it.

Clues?

---

### Post by imbjr on 2007-08-08
Well, I've discovered that it was the script at fault. Running the script from the launcher confused it because of tryig to access the dropped file from the wrong directory.

Trouble is, I now cannot get basename and dirname to work in a script:

base = 'basename $1'

just does not work!

base does not get to the basename of $1, it gets set to the string "basename <whatever $1 was>"

Any ideas?

---

### Post by apetresc on 2007-08-08
You are using the wrong kind of quotes (this is a common bash problem). You want the ` quote, but you're using the ' quote. (The ` quote is the one below the "Esc" key on most keyboards).

So the line ```
base = `basename $1`
``` should work :)

---

### Post by imbjr on 2007-08-08
Thanks. I just discovered that by directly copying something and came here to post about it.

---

