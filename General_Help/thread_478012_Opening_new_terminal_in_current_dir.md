---
title: "Opening new terminal in current dir"
date: 2007-06-18
forum: General Help
---

### Post by malfist on 2007-06-18
I'm trying to write a script so I can launch a terminal for the current directory in nautilus using nautilus's scripts. I can't get it to work right, I 've tried ```
gnome-terminal --working-directory=.
``` but that just launches it at $HOME.

---

### Post by Brucevdk on 2007-06-19
After I initially posted this message I thought I found out what the heck was going on. But I'm still not sure why the current working directory (pwd) isn't changed properly. For some reason though, just using gnome-terminal seems to work. Don't ask me why....

```

gnome-terminal

```

There's also *nautilus-open-terminal*, which is an actual Nautilus extension you can get it from the repository. Anyways, the following nautilus-script I found a while ago works for everything from opening a terminal in the current directory to opening a terminal in the selected directory. I added a couple of comments to make it clear what it does.

```

#!/bin/sh
# From Chris Picton
# Replaces a Script by Martin Enlund
# Modified to work with spaces in path by Christophe Combelles

# This script either opens in the current directory, 
# or in the selected directory

# uses cut and sed to clean up the variable
base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"

# if nothing has been selected then it doesn't do anything
if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else 
     # but if there is something selected it'll find the first directory selected
     # -z checks for an empty string, -d tests if something is a directory
     # -a means AND or &&, see man test for more options
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     # either it finds a directory and appends it or it appends an empty variable
     dir="$base/$1"
fi

# done!
gnome-terminal --working-directory="$dir"

```

---

