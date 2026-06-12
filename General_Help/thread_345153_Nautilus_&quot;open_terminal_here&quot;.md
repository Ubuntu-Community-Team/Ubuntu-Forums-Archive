---
title: "Nautilus &quot;open terminal here&quot;?"
date: 2007-01-23
forum: General Help
---

### Post by PurplePenguin on 2007-01-23
Back when I was using kde, I used to really love the "open terminal here" that I could get via right click in konqueror.

That is, if I made my way to some obscure directory, I could just right click some empty space, select "open terminal here", and pop! a terminal window would open at exactly that spot.

My wife found it helpful, since she sticks her digital photos in weird directories (and isn't comfortable using the command line), then wants to open up a terminal at that spot to resize photos (yes, mogrify is the extent of her command line skill - not too bad!).

I haven't come across anything in nautilus that will let me do this, but I'm assuming that I'm not the only one who's found this useful.  Does anybody know if there's a bit of a hack or script that can add this functionality?  Or maybe I'm missing something blatantly obvious (I tend to do this on an alarming basis).  Thanks! :)

---

### Post by 23meg on 2007-01-23
```
sudo apt-get install nautilus-open-terminal
```

---

### Post by PurplePenguin on 2007-01-24
And it's that easy! :)  Thanks!

---

### Post by fragos on 2007-01-24
I hadn't seen that one but what I did was place the following bash script in /home/fragos/.gnome2/nautilus-scripts with file name "Terminal Here".  Be sure to set the execute permission.  In Nautilus, right click an in an open are of its window and select Scripts-> "Terminal Here".  Perhaps the installable package is a Nautilus script like this one.

#!/bin/sh
# Original by two other scripts merged together
# Modified by Eugenia Loli and Kon, Oct 2004
# This script either opens in the current directory, 
# or in the selected directory
# Doesn't work with the ~/Desktop or the ~/.Trash folders (Nautilus' limitation).

base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"

if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else 
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     dir="$base/$1"
fi

if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "x-nautilus-desktop:///" ]; then
dir="Desktop"
fi

if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "trash:" ]; then
dir="$HOME/.Trash"
fi

if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "file:///" ]; then
dir="/"
fi

FIRST_URI="`echo -n $NAUTILUS_SCRIPT_SELECTED_URIS`"

if [ "$FIRST_URI" == "x-nautilus-desktop:///home" ]; then
dir="$HOME"
fi

if [ "$FIRST_URI" != "" ]; then
dir="`echo $FIRST_URI | cut -c8-`"
fi

if [ "$FIRST_URI" == "x-nautilus-desktop:///computer" ]; then
dir="/"
fi 

# uncomment this if you want to use the Gnome Terminal instead of XTerm
gnome-terminal --working-directory="$dir"

#cd $dir
#exec xterm -bg black -fg green -cr red -sl 3000 -g 100x76+1+1 -T `pwd`

---

### Post by PurplePenguin on 2007-01-25
Great work!!  I tried your script and it works perfectly.  This is the kind of stuff I wish I could write... :)

---

### Post by jesse0 on 2008-02-13
The nautilus-open-terminal package will also open terminals on SSH servers which you are browsing via Nautilus.

---

