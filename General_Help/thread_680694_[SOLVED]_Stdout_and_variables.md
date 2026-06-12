---
title: "[SOLVED] Stdout and variables"
date: 2008-01-28
forum: General Help
---

### Post by PinkFloyd102489 on 2008-01-28
Im making a script that will capture the /tmp Flash file when I load a youtube video. Here's what I have so far, albeit it's wrong:

```

#!/bin/bash

#Naming the file
NAME="zenity --title "Enter file name" --text "Enter what you wish to name the file""

sleep 3

#Moving and encoding

sleep 3

cd /tmp
mv Flash* ~
cd ~
ffmpeg -i Flash* $NAME | zenity --progress --pulsate --title "Encoding..." --text "Encoding file..." --auto-close --auto-kill

sleep 3

mv $NAME ~/Desktop

zenity --info --title "Finished" --text "Done encoding $NAME"

```


As you can see, Im trying to use the stdout (standard output) of the zenity entry command to set as a variable to use later in the script. It's not working like this, even though I tried using a > in there also. Help?

---

### Post by PinkFloyd102489 on 2008-01-28
bump

---

### Post by heindsight on 2008-01-28
try
```
NAME=$(zenity --title "Enter file name" --text "Enter what you wish to name the file")

```

---

### Post by PinkFloyd102489 on 2008-01-28
I was just about to try parenthesis but didnt know if that would work. Testing now.

---

### Post by PinkFloyd102489 on 2008-01-28
Alright that fixed it, aside from a few sytax errors that I overlooked when testing out Zenity. Thanks for your help!

---

### Post by nick_h on 2008-01-28
or you could use:
```
NAME=`zenity --entry --title "Enter file name" --text "Enter what you wish to name the file"`
```

---

