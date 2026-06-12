---
title: "Right click option 'Open as root' opens a new instance of Nautilus/&quot;File Browser&quot;"
date: 2006-11-13
forum: General Help
---

### Post by Ullner on 2006-11-13
I'm using the right click script 'Open as root' which have been posted on this forum.
```
if [ -n "$1" ]; then
# Open selected folder/files as root
        for url in $NAUTILUS_SCRIPT_SELECTED_URIS; do
                gksudo "gnome-open $url" &
        done
else
# Open directory I'm in as root
        gksudo "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI" &
fi

```
Unfortunately, when either block is executed for a directory, a new instance of Nautilus/"File Browser" is opened. This means I have now two instances open. The first that doesn't have access and the second which have root access. I want to (1) close the first automatically or (2) elevate my rights in the first (and only) window.

How would I go about doing either (1) or (2)? I don't particularly care which, as long as I don't have to have two instances open. 

I tried with eg "nautilus -q $NAUTILUS_SCRIPT_CURRENT_URI" to accomplish option (1), but windows gets closed 'randomly'.

---

### Post by hikaricore on 2006-11-13
Try adding something to your script to get nautilus' current pid:"

```
pidof nautilus
```

_Before_ opening a new session of nautilus as root.  Then you can kill that pid instead of doing "nautilus -q"

---

### Post by Ullner on 2006-11-13
Thanks. kill `pidof nautilus` seem to do that.
```
if [ -n "$1" ]; then
# Open selected folder/files as root
        for url in $NAUTILUS_SCRIPT_SELECTED_URIS; do
                kill `pidof nautilus`
                gksudo "nautilus --no-desktop $url" &
        done
else
# Open directory I'm in as root
        kill `pidof nautilus`
        gksudo "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI" &
fi
```
This is the current code. 

However, this code will kill ALL other windows as well. All windows seem to run on the same process... Is there some way to get single windows?

---

