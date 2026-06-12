---
title: "Using Phatch or an alternative to batch convert TIF images"
date: 2013-02-20
forum: General Help
---

### Post by hundred1906 on 2013-02-20
I have many tif images inside my Pictures directory and want to get them all converted to jpg type. Is Phatch really the best tool for this because after spending a reasonable amount of time looking I cannot figure out how to use it, even after looking at the tutorials.

Is there anything out there that is more intuitive and has a GUI?

Or has anyone a simple description of how to set Phatch up to do this?

---

### Post by lmarmisa on 2013-02-20
I recommend ImageMagick:

[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

This is an example:

```

convert image.tif image.jpg

```

---

### Post by MrsUser on 2013-02-20
You can try XnConvert which makes it a breeze:
[http://www.xnconvert.com/downloads](http://www.xnconvert.com/downloads)

---

### Post by hundred1906 on 2013-02-20
Thanks but the problem with Convert is that it is not easily operated as a batch tool.

---

### Post by hundred1906 on 2013-02-20
> **MrsUser said:**
> You can try XnConvert which makes it a breeze:
[http://www.xnconvert.com/downloads](http://www.xnconvert.com/downloads)

I might try this but the download site looks as though it is going to  install adware. I can see that it is also available on the Software Centre via Launchpad - just need to remember my password - it is too late for this sleepyhead.

---

### Post by stani on 2013-03-28
Hi,
I am the author of Phatch. Converting them to jpeg is very simple. Just add a save action and set file type to jpg. Then drag and drop your Pictures folder on Phatch.
Kind regards,
Stani

---

### Post by stani on 2013-03-28
Hi,
I am the author of Phatch. Converting them to jpeg is very simple. Just add a save action and set file type to jpg. Then drag and drop your Pictures folder on Phatch.
Kind regards,
Stani

---

### Post by hundred1906 on 2013-04-01
Stani. Thanks for coming back on this but that advice did not work completely.

I added an Action and set type to jpg. Dragged the folder in and checked tif type, also do not overwrite (or similar). After pressing "Batch" it found the tif files and commenced processing - however there was no discernable output except a message advising of errors in the log. 

I looked at the log file but closed the error message before noting it's contents and now cannot find it, at least it is not where I expect it to be. As I recall it looked pretty much like a copy of the Action item.

---

### Post by hundred1906 on 2013-04-01
OK. I found all the new files, on a directory called Phatch on my desktop.

---

### Post by apos on 2013-09-10
Hi hundred 1906,

you can use nautilus-scripts to do this task.

The following nautilus-script will run the phatch-script **in the current folder "."** 
You can also use it as bash script ;-)

Pay attention, that you add the "save"-Action to your phatch-script! I prefer to user "<folder>/name_of_script" for the place to save. This will put everything into a subfolder of the current folder.

1. put it simply into $HOME/.gnome2/nautilus-scripts
2. chmod 755 scriptname

Now you can use it with your left mouse button and the scripts-menu.

[FONT=Courier New][COLOR=#000000]#!/bin/bash

# Phatch
myPhatchScript="YOUR_PHATCH_FILE.phatch"
myPhatchDir="/PATH/TO/PHATCH_SCRIPTS/"
myPhatch="${myPhatchDir}/${myPhatchScript}"

myNotifyIcon="/PATH/TO/YOUR_ICON.png"


## Change this for toggling beeing a bash-script or a nautilus-script
[ "$DEBUGMODE" = "--debug" ] && DEBUG=1
[ $DEBUG ] && zenity --info --title "DEBUG-MODE" --text "Running in debugging mode."

[ $DEBUG ] || cd "$NAUTILUS_SCRIPT_CURRENT_URI"
[ $DEBUG ] && cd "$(pwd)"

notify-send  "Start conversion..." \
     -i ${myNotifyIcon} \
     "Phatch Script: ${myPhatchScript}."

if phatch "${myPhatch}" .
then
notify-send  "Conversion successfully ended ..." \
     -i  ${myNotifyIcon} \
     "Phatch Script: ${myPhatchScript}."
fi

sync[/COLOR][/FONT]

Greets
Axel

---

