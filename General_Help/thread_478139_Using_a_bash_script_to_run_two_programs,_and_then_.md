---
title: "Using a bash script to run two programs, and then terminate them cleanly"
date: 2007-06-19
forum: General Help
---

### Post by soro2005 on 2007-06-19
So here's the situation: I have python script A and python script B. Script B presupposes A. Script B is the one the user interacts with, and which user terminates once he or she is done.

I want to start both scripts with a bash script, then have the bash script wait for Script B to be terminated. Then, the bash script should cleanly terminate script A, so there're no residues which don't belong. This must be really easy, but I freely admit that I don't have a clue.

I have so far something like this here:
```
#!/bin/bash
python ScriptA.py &
python ScriptB.py
exit
```

Thanks for your help!

---

### Post by stylishpants on 2007-06-19
OK, how about this:
```
#!/bin/bash

# Run A, remember it's PID
python ScriptA.py &
pid=$!

# Run B
python ScriptB.py

# Clean up
kill $pid


```

---

### Post by soro2005 on 2007-06-19
I knew it was easy. Thanks so much!

---

