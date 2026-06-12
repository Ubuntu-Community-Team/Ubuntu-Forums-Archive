---
title: "Spaces in paths?"
date: 2007-10-31
forum: General Help
---

### Post by ownaginatious on 2007-10-31
Both my drives happen to have spaces in the naming (i.e. /Server Drive/Server Core Folder), does anyone know how I enter these in the terminal when wanting to change things? I tried replacing the spaces with underscores, but it didn't seem to work very well...
what is the syntax equivalent to a space?

Sorry if this is a noob question (which it probably is) but I can't seem to find any information on this :p

---

### Post by dcstar on 2007-10-31
> **ownaginatious said:**
> Both my drives happen to have spaces in the naming (i.e. /Server Drive/Server Core Folder), does anyone know how I enter these in the terminal when wanting to change things? I tried replacing the spaces with underscores, but it didn't seem to work very well...
what is the syntax equivalent to a space?

Sorry if this is a noob question (which it probably is) but I can't seem to find any information on this :p

Put the string within quotes: "/usr/local/a path with a space in it/this file"

---

### Post by BlueSkyNIS on 2007-10-31
A more complicated way:

```
My Computer Files/Users music
```

in terminal would be:

```
My\ Computer\ Files/Users\ music
```

So, put every \ before a space character ;-)

---

