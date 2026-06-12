---
title: "Make unrar run from nautilus script?"
date: 2007-02-18
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-02-18
I find I have to use unrar from the command line a lot with many files, as Archive manager fails to cope with them. So I took upon the idea of writing a nautilus script so that i could simply right click on the rar file, choose the script, and have a terminal open and either be asked for a password (in the terminal) or just watch and wait for the unrar process to complete (in the terminal). I looked at a few of the nautilus scripts already available, so have figured out how to place the filename into the scripts path, and can get a terminal to open, but cannot figure out how to pass the filename and the unrar command to the terminal prompt.

I have had a good read about bash scripting, but cannot find what I need to do this.

```
#!/bin/bash

  cd $NAUTILUS_SCRIPT_CURRENT_URI
  for arg in $@
  do
      gnome-terminal -x unrar e -y $arg
  rm $arg
  done
```

This is as far as I have got, and I know this script doesn't work!:confused: 

Help please to sort what I think would be a useful feature.

Well, got it working, needed the full path to unrar (doh!):
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
  for arg
  do
      gnome-terminal -x /usr/bin/unrar e -y "$arg"
  done
```

Now need help to add more commands!

---

### Post by zvacet on 2007-02-20
Isn´t it much  easyer to right click on rar file and in dropdown menu select : unpack here ?

---

### Post by Jose Catre-Vandis on 2007-02-20
> **zvacet said:**
> Isn´t it much  easyer to right click on rar file and in dropdown menu select : unpack here ?

Yes and No....

Depends if it is password protected, or the type of rar file that the Archive manager or "Unpack here" can cope with. At least I know that unrar can cope with just about everything you throw at it. it is also less clicks, if the rar files have a password.

---

