---
title: "scrot/firefox arguments"
date: 2008-05-17
forum: General Help
---

### Post by thevjm on 2008-05-17
I am working on a command that will take a screenshot (with scrot), open up firefox, and upload it to imageshack, photobucket, ect...

So far all I have is this:

```
scrot Screenshot.png && firefox "www.imageshack.us"
```

I am kind of an amateur at this command line stuff, so please help me out.:(

Even just a command to copy the screenshot's directory onto the clipboard would suffice.

It would be cool to automate the entire process, though.

---

### Post by ibuclaw on 2008-05-17
xclip can copy commandline output to the X Clipboard.
```
sudo apt-get install xclip
```

Then try out this script:
```

#!/bin/bash                                                                     
if [ $1 ]
then scrot "$HOME/$1.png"
echo "$HOME/$1.png" | xclip -selection c
firefox "imageshack.us"
fi

```
It isn't brilliant, but it will do.

It makes a screenshot and copies the link to that screenshot in your "Ctrl+V" command.

Usage is "**./screen filename**"
The script will add ".png" onto the filename itself, so you don't have to.
You may also want to consider adding a timer before the screenshot too.

Regards
Iain

---

