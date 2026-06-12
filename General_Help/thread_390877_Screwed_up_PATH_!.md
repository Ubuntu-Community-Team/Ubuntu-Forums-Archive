---
title: "Screwed up PATH !"
date: 2007-03-22
forum: General Help
---

### Post by madcow72 on 2007-03-22
I was just setting up LaTeX again from the TeXLive2007 cd and was in the middle of adding the new pathway to PATH, but accidentally hit "Enter" too soon and lost all of my default pathways.  I added back in certain pathways that I knew about, but some programs, Beryl in particular, are still not working.  Right now, an echo $PATH command yields the following:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/local/texlive/2007/bin/i386-linux

```
Any paths I'm obviously missing or suggestions how to recover?

Thanks!

---

### Post by Ramses de Norre on 2007-03-22
This is my PATH, I guess yours should have the same plus the ones you wanted to add:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

---

### Post by madcow72 on 2007-03-22
Ramses de Norre,

Merci beaucoup pour ton aide!  I think I figured out what I was doing wrong.  I didn't realize that the PATH environment is lost as soon as I close the terminal, so after doing that and restarting X, my paths were gone which caused lots of things not to work properly.

In case anyone does the same stupid thing as me in the future, this is basically what to do:

```
PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
export PATH
```
Then to make sure it exists for the future, I edited my /etc/environment file to include the paths at startup:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
```

---

### Post by Ramses de Norre on 2007-03-22
Mine is set in /etc/environment, have you got an empty path set there?
The .bashrc solution does the same though (but only for your user).

---

### Post by madcow72 on 2007-03-22
Thanks again, Ramses!  You're right, of course.  I'm still learning how everything works in Linux, and I'll chalk this up as one more lesson.  Best way to learn is to break things and get 'em going again.

I edited my earlier response to set the paths within /etc/environment instead of .bashrc

---

### Post by ayoli on 2007-03-22
> **madcow72 said:**
> 
I edited my earlier response to set the paths within /etc/environment instead of .bashrc
:) may i enlarge this topic to say that not every distribs uses the same configs in /etc so path may not be in /etc/environment for all distribs
> **madcow72 said:**
> Best way to learn is to break things and get 'em going again.
yes it is :)

---

