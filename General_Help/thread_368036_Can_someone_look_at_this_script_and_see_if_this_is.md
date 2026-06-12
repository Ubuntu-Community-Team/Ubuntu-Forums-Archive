---
title: "Can someone look at this script and see if this is right?"
date: 2007-02-22
forum: General Help
---

### Post by billdotson on 2007-02-22
I am making a script to automatically rip and convert the .vob file to mpeg format

I started off doing this

mkdir ~/bin # in case it doesn't exist
nano ~/bin/vob

then put this text in the terminal: 

#!/bin/bash

vobcopy -t movie
tcextract -i SONY_DVD_RECORDER_VOLUME.vob.partial -t vob -x mpeg2 > movie.m2v
tcextract -i SONY_DVD_RECORDER_VOLUME.vob.partial -t vob -x ac3 -a 0 > movie.ac3
mplex -f 8 -o "movie%d.mpg" movie.m2v movie.ac3

Then I put this in the terminal: chmod +x ~/bin/vob

Then I typed vob in the terminal but it said it wasn't a command.  

I typed echo $PATH and I got this: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

How do I get it so this command is usable?

---

### Post by stickmangumby on 2007-02-22
Did you just type:
```
vob
```

Or did you type:
```
./vob
```
?

---

### Post by scoon on 2007-02-22
> **billdotson said:**
> I am making a script to automatically rip and convert the .vob file to mpeg format

I started off doing this

mkdir ~/bin # in case it doesn't exist
nano ~/bin/vob

then put this text in the terminal: 

#!/bin/bash

vobcopy -t movie
tcextract -i SONY_DVD_RECORDER_VOLUME.vob.partial -t vob -x mpeg2 > movie.m2v
tcextract -i SONY_DVD_RECORDER_VOLUME.vob.partial -t vob -x ac3 -a 0 > movie.ac3
mplex -f 8 -o "movie%d.mpg" movie.m2v movie.ac3

Then I put this in the terminal: chmod +x ~/bin/vob

Then I typed vob in the terminal but it said it wasn't a command.  

I typed echo $PATH and I got this: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

How do I get it so this command is usable?

Hey there, 

~/bin ($HOME/bin) is not in your path.  You need to add it.  Assuming you are using bash, you can add this to .bashrc: PATH=$PATH:$HOME/bin  Then, when you open up a terminal, $HOME/bin will be in your path and you'll be able to use your script.

-scoon

---

### Post by billdotson on 2007-02-22
I don't know how to add that to the path.  How do I do that

"~/bin ($HOME/bin) is not in your path. You need to add it. Assuming you are using bash, you can add this to .bashrc: PATH=$PATH:$HOME/bin Then, when you open up a terminal, $HOME/bin will be in your path and you'll be able to use your script."

---

### Post by scoon on 2007-02-22
Use a text editor and open ~/.bashrc to edit.

-scoon

---

