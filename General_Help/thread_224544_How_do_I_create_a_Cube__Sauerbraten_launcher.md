---
title: "How do I create a Cube / Sauerbraten launcher?"
date: 2006-07-28
forum: General Help
---

### Post by gingermark on 2006-07-28
Hi,

I like Cube and Sauerbraten, but I can't figure out how to create a launcher for them.

To run cube for example I have to navigate into the cube directory before running ```
./cube_unix
``` to start the game.

I don't seem to be able to do this from a launcher. Is it possible? Running Kubuntu Dapper here.

Thanks in advance,
gingermark.

---

### Post by hw-tph on 2006-07-28
Try providing the full path to the executable in the launcher, something along the lines of */home/gingermark/games/cube_unix* or wherever it is installed.


Håkan

---

### Post by gingermark on 2006-07-28
> **hw-tph said:**
> Try providing the full path to the executable in the launcher, something along the lines of */home/gingermark/games/cube_unix* or wherever it is installed.


Håkan

Thanks for the suggestion. I probably should have said that I have already tried that with no success. I've also tried playing around with the working directory and terminal options, but to no avail.

---

### Post by gingermark on 2006-07-28
For anyone else who cares, I just ended up creating my own shell script to launch the games, and that worked from the menu.

No idea why the provided shell scripts didn't work from the menu, but anyways, I'm happy with the solution.

---

### Post by petersjm on 2006-08-11
I've been wondering about this, myself. How did you solve it, gingermark?

---

### Post by Perfect Storm on 2006-08-11
make a
RunGame.sh

open it

fill in 
```

#!/bin/bash

cd /to/the/game/folder

./<the launcher>

```

chmod + x it.

Now point the launcher to the script instead with
sh /to/the/folder/Rungame.sh

---

### Post by thedarkdonut on 2007-11-07
As for me I edited the sauerbraten_unix shell file.  All I did was comment out the the SAUER_DIR=. line, uncommented #SAUER_DIR=/usr/local/sauerbraten, and edited it to point it to the actual folder that I have the sauerbraten folder place at.  So the top of my sauerbraten_unix shell file now looks like the following:

```

#!/bin/sh
# SAUER_DIR should refer to the directory in which Sauerbraten is placed.
#SAUER_DIR=~/sauerbraten
SAUER_DIR=/usr/local/games/sauerbraten
#SAUER_DIR=.

```

As for the launcher the command line I'm using is:
```

/usr/local/games/sauerbraten/sauerbraten_unix

```

Executed the launcher and it works fine for me.

---

