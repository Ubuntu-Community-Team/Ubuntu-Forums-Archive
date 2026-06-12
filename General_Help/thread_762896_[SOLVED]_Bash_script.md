---
title: "[SOLVED] Bash script"
date: 2008-04-22
forum: General Help
---

### Post by alberto ferreira on 2008-04-22
Hi, I wanted to open a .mp3 file in nautilus with a mouse right click > open with > and then run cmus, however cmus can only run inside a terminal so i created a script with two parts:
 - part 1 : launch cmus inside a terminal
     $ exec cmus

 - part 2 : tells cmus to play the desired file
     $ cmus-remote -q '$music to be played'
     $ cmus-remote --play


However, the 2nd part needs cmus running and when I use '&' after the command, cmus doesn't work, so I need to run the first part in one terminal and the second in a new terminal.

How do I run the second part inside a new terminal?????????????????????????

Thanks

---

### Post by -Zeus- on 2008-04-22
Please go to a terminal and run this:

```
cmus&
```

and tell me what happens

---

### Post by bingoUV on 2008-04-22
If cmus does not like being backgrounded, run it in a terminal and background the terminal. Your post suggests that you do not mind opening an extra terminal window.
```

xterm -e "cmus" &
cmus-remote -q '$music to be played'
cmus-remote --play

```

---

### Post by alberto ferreira on 2008-04-28
I think that by using xterm to run cmus, the rest of the code running in gnome-terminal can't access it, as no music gets played.

---

### Post by bingoUV on 2008-04-28
I have never used cmus, but I think you are not quite using it correctly. Even without this script that you are trying to write, have you ever succeeded in playing music on cmus? 

Because it does not like being backgrounded and expects remote command from the same terminal where it was started it is impossible to run it at all. Does it have any documentation? Any mention of this there?

---

### Post by alberto ferreira on 2008-04-29
Oh, thanks for the reply, I've been trying things and here it is working:

###############################
#! /bin/bash

xterm -e cmus &
sleep 1
cmus-remote -q "/path/to/music"
sleep 1
cmus-remote -p
###############################

The cmus-remote commands executed before cmus was ready, so I put a sleep command, however if my pc is running too much stuff they will still be executed before cmus is ready, so, how do I know if a process is running? In this case, cmus in xterm ?

Thanks :D

---

### Post by bingoUV on 2008-04-29
Script is attached. The while loop runs as long as isRunning is an empty string. isRunning will remain an empty string as long as cmus is not running. It is checked every second whether cmus is running or not.    

PS : This forum is going to the dogs. Cannot even format code blocks properly anymore.

---

