---
title: "Command to open file in terminal"
date: 2007-09-29
forum: General Help
---

### Post by cameran on 2007-09-29
hello,

i would like to be able to find a command so i can run mp3/ogg files through mplayer in terminal.  i'd like the terminal window to stay open.  i've been pouring through the forums but i can't find anything that will work right.

the specific command i'm looking to use with mplayer is:

```
mplayer -loop 0
```

when i've gotten it to run usually the console window closes instantly and no music plays.  sometimes the music plays but there is no console window!

thanks for any help!!!

cameran

---

### Post by cameran on 2007-09-29
figured it out myself.  here's the code if anyone ever wants to use it:

```
gnome-terminal -x mplayer -loop 0
```

-loop 0 sets it for an infinite song loop.  you can do something like -loop 2 to play it twice, etc.

just put that code in the open with other application > use a custom command field

i love listening to music with no gui, so much cleaner looking :D

cameran

---

### Post by cameran on 2007-09-29
ok i guess my next question is -

i want to save this command as a bash script so i can run my music using that script when i right click.

i created a simple script:```
#!/bin/bash
mplayer -loop 0
```

but i can't seem to get it to run when using a custom command.  terminal pops up and then is gone.  

how can i set it so i can run a song via script when right clicking?

thanks in advance :confused::confused:

cameran

---

