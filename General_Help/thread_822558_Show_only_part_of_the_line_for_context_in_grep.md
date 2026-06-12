---
title: "Show only part of the line for context in grep?"
date: 2008-06-08
forum: General Help
---

### Post by Endolith on 2008-06-08
I'm grepping through a file, but each line is really long, and wraps.  I'd like to make it output just part of the line for context, like put the match in the middle of the screen and then show 20 characters in each direction around it, instead of the entire line.  Is there a way to do this?

---

### Post by geirha on 2008-06-08
Yes, using the -o option for grep, which only shows the part that actually matches:
```
$ grep -o 'monitor' /var/log/Xorg.0.log
monitor
monitor
monitor
# Then we just extend the regexp to match extra characters to each side. 
# I'll just use 6 for this example:
$ grep -o '.\{0,6\}monitor.\{0,6\}' /var/log/Xorg.0.log
using monitor secti
as no monitor secti
as no monitor secti
# Or if you prefer extended:
$ egrep -o '.{0,6}monitor.{0,6}' /var/log/Xorg.0.log

```

---

### Post by Endolith on 2008-06-08
> **geirha said:**
> Yes, using the -o option for grep, which only shows the part that actually matches:


Oh!  Good idea.  I have colored highlighting turned on.  Is there a way to highlight only the part I actually want to match?  Like .{0,6}(monitor).{0,6}

---

### Post by geirha on 2008-06-08
Would be nice, though looking through the man-page it does not seem possible. The only way I can think of to achieve this is with two greps. Perhaps make a script like this?

```

#!/bin/bash
regex="$1"
shift
egrep -o ".{0,6}$regex.{0,6}" "$@" | egrep "$regex"

```

---

### Post by Endolith on 2008-06-08
> **geirha said:**
> Would be nice, though looking through the man-page it does not seem possible. The only way I can think of to achieve this is with two greps.

Also a good idea.  :)

---

