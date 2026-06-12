---
title: "unity problem"
date: 2013-12-07
forum: General Help
---

### Post by balogh-marcu on 2013-12-07
I'm a new user to Linux, i'm running Ubuntu 13.10 and my unity desktop won't show the left side panel . I was doing something in compiz manager when it got into that state, all i can do from my unity now is to open the terminal and the file manager. is there a program or a command to restore unity desktop to its defaults from the terminal?  

Thanks in advance :)

---

### Post by balogh-marcu on 2013-12-07
Right now i'm using gnome dosktop

---

### Post by MG&amp;TL on 2013-12-07
Open a terminal (from any desktop) and run

```
dconf -f reset /org/compiz/
```

Then log back into unity and things should be fine. :-)

---

### Post by balogh-marcu on 2013-12-07
Usage:
  dconf COMMAND [ARGS...]


Commands:
  help              Show this information
  read              Read the value of a key
  list              List the contents of a dir
  write             Change the value of a key
  reset             Reset the value of a key or dir
  update            Update the system databases
  watch             Watch a path for changes
  dump              Dump an entire subpath to stdout
  load              Populate a subpath from stdin


Use 'dconf help COMMAND' to get detailed help.

---

### Post by balogh-marcu on 2013-12-07
so i'm getting that error

---

### Post by balogh-marcu on 2013-12-07
i got it running with [COLOR=#000000][FONT=Ubuntu Mono]dconf reset -f /org/compiz/ 

[/FONT][/COLOR]

---

### Post by Resistent on 2013-12-07
If you don't need a very beautiful with effects loaded ubuntu, try a lightweight desktop. 
(like lubuntu, xubuntu, kubuntu, ) For example I use Lubuntu desktop. You have a menu like in older Windows like Xp, Vista or 7. And it's nice looking, very fast.

---

### Post by heir4c on 2013-12-07
Maybe this link will help:
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by MG&amp;TL on 2013-12-07
Sorry that doesn't work. I half-remembered that command, and looked it up here: [http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration).

Odd that it doesn't work, mind - it's corroborated in quite a few places.

---

