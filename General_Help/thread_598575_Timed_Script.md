---
title: "Timed Script?"
date: 2007-10-31
forum: General Help
---

### Post by _simon_ on 2007-10-31
How would I write a simple script to be executed at startup that would load one thing and then when that's finished load another?

I want to load fusion-icon and then when it's finished have cairo-clock load. (the new version of cairo-clock won't run unless compositing is already running)

---

### Post by kast on 2007-10-31
[B]Well simple way would be to 

#!/bin/sh

 run fusion-icon command   *# Not sure what that would be*

 sleep 30   *# how ever long you think it would take for the fusion-icon to load*

 run cairo-clock
       exit 1

# end script[/B]

save the script 

then make it executable

** chmod 755 yourscript**

then add it to startup, there are a few different ways here is one.

move your script to the **/etc/init.d/** directory

then run 

**% update-rc.d yourscript  defaults**

---

### Post by _simon_ on 2007-10-31
I tested it from termial but it says it can't find the command run "run not found" ?

EDIT: ok, seems you don't need the run bit.
However, it's only loading fusion-icon, not the clock.

Here's what I have:

```

#!/bin/sh

/usr/bin/fusion-icon 

sleep 30

/usr/bin/cairo-clock

exit 1

# end script

```

Is the time in seconds? I tried 5 but no change.

---

### Post by _simon_ on 2007-10-31
Found the problem, cairo-clock won't load until fusion-icon is quit

---

### Post by _simon_ on 2007-10-31
Well not sure it's the right way to do things but this works lol

fusion-icon is running via the sessions manager as usual and then this script runs:

```

#!/bin/sh
sleep 5

cairo-clock

exit 1

# end script

```

Seems to work!

---

### Post by sisco311 on 2007-10-31
try out this:
```
#!/bin/sh

/usr/bin/fusion-icon &

sleep 30

/usr/bin/cairo-clock

exit 1
```

---

