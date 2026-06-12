---
title: "Help with Bash Command - startdir"
date: 2007-07-05
forum: General Help
---

### Post by Darko Beta on 2007-07-05
I am a Bash newb and this is a simple question.

I am trying to run a script and I can't seem to get the syntax right on the first command, startdir.

Here is what I have:
```
startdir='/media/My Book_/Media/Music'
```

I have tried every combination of quotes, I swear, but I might have missed one.  Anyway, when a subsequent part of the script comes up, cd $startdir, then it kicks out an error: 

```
cd: 25: can't cd to /media/'My
```

What is the syntax I need to use to make it CD to that directory?

---

### Post by bodhi.zazen on 2007-07-05
The problem is the single quotes and the space.

Try no quotes or "

startdir=/media/My\ Book_/Media/Music

or 

startdir="/media/My Book_/Media/Music"

---

### Post by stylishpants on 2007-07-05
I don't think you can do it with shell trickery.  That space just screws you up every time.

Maybe you should consider installing the cdargs package and using that instead.


This is how you would do it with cdargs:

1. Install the cdargs package (sudo apt-get install cdargs)
2. Add this shell function to ~/.bashrc
```
       function cv () {
           cdargs "$1" && cd "‘cat "$HOME/.cdargsresult"‘" ;
       }

```
3. restart your shell ("exec bash")
4. create a file in your home dir named  ".cdargs", defining a 'shortcut' to your dir.  Add this to the file:
```

startdir /media/My Book_/Media/Music

```
5. cd to your dir with this command (note that it is 'cv' not 'cd'):
```

cv startdir

```

You can define as many of these shortcuts as you like in the ~/.cdargs file.

---

