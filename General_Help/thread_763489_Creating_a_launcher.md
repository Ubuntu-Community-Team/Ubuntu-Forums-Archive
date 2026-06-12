---
title: "Creating a launcher"
date: 2008-04-23
forum: General Help
---

### Post by funguy on 2008-04-23
Ok this should be easier than I am making it. I am trying to create a Launcher for a game, Enemy Territory - Quake Wars. I can't seem to run the game just by dbl clicking etqw but if in the terminal I type   ./etqw it loads. I tried to do the launcher graphically thru the menus but it doesn't work. It appears to me that the association of that file isn't pointed to terminal. Any help?

---

### Post by justleen on 2008-04-23
try poiting the launcher to the full path.

in the directory where you type issue a ```
 pwd 
```.
copy and paste that path in the launcher, at the "command" line

---

### Post by funguy on 2008-04-23
here is my path

/home/erik/.wine/drive_c/Program Files/id Software/etqw

It is in the wine directory cause the demo also has the Windows version too.

in that directory I type

./etqw


how would I put that into the launcher?

---

### Post by justleen on 2008-04-23
/home/erik/.wine/drive_c/Program Files/id Software/etqw/etqw

---

### Post by forrestcupp on 2008-04-23
It runs with Wine, so you have to put wine in the command.  Here is what your launcher command should be.
```
wine /home/erik/.wine/drive_c/Program\ Files/id\ Software/etqw/etqw
```always remember to put a **\** before any space in a path.

If it still doesn't work, you'll need to make a script that changes to that directory then runs the program.  Then make your launcher run that script.  But try the command above.  There's a good chance it will just work like that.

---

### Post by funguy on 2008-04-23
Like I said it doesn't run with wine, cause it is native to linux (ie  ./etqw) It is only in the WINE directory.

JUSTLEEN
>  /home/erik/.wine/drive_c/Program Files/id Software/etqw/etqw

comes up saying
```

dirname: extra operand `Files/id'
Try `dirname --help' for more information.
exec: 4: ./etqw.x86: not found

```

Thanks guys, for the help by the way.

---

### Post by funguy on 2008-04-23
I think the etqw is a script... let me see.

```

#!/bin/sh
cd `dirname $0`
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:."
exec ./etqw.x86 "$@"

```

This is what is in the file. Maybe after the exec it needs the full address.

---

### Post by funguy on 2008-04-23
Thanks... I got it. You all are my muse  :guitar:

I had to change the original script to include the rest of the directory.

```

#!/bin/sh
cd `dirname $0`
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:."
exec /home/erik/.wine/drive_c/Program\ Files/id\ Software/etqw/etqw.x86 "$@"

```

This works great!

---

