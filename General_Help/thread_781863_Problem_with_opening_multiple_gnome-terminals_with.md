---
title: "Problem with opening multiple gnome-terminals with a script"
date: 2008-05-04
forum: General Help
---

### Post by lavarock on 2008-05-04
Hi, I am relatively new to linux and Ubuntu (only been using for a year).  In general I found solutions to problems rather fast, but this one has been bugging me for a while without finding the solution.

I have some programs that I need to run a bunch of processes in different terminals (I use gnome-terminal that comes with Ubuntu).  I also need them to  lay out on the desktop correctly so I can see the output as they run.  I wrote a script that open those terminals.
```

gnome-terminal --geometry 56x21+1000+0 --hide-menubar &
gnome-terminal --geometry 56x21+1000+400 --hide-menubar &
gnome-terminal --geometry 56x21+335+400 --hide-menubar &
gnome-terminal --geometry 56x2+335+330 --hide-menubar &
gnome-terminal --geometry 56x2+335+270 --hide-menubar &
gnome-terminal --geometry 56x2+335+210 --hide-menubar &
gnome-terminal --geometry 39x2+0+650 --hide-menubar &
gnome-terminal --geometry 39x2+0+730 --hide-menubar &

```

Now they usually work fine, but sometimes (and it's not reproducible and happened multiple times already), this script only open a few windows but not others, and then Ubuntu seems to "hang" in a sense that all the buttons on the desktop stop responding (include the shutdown icon), at which point I have to restart the computer to fix the problem.  If I terminate all the gnome-terminals the buttons are responding again, but I can no long open any more gnome terminals.
The problem is that this happens rather sporadically, with no way that I know of to reproduce it.  I am not sure it's a bug or some problem with my script.

Also, this is Ubuntu 7.10. Thanks for help in advance.

---

### Post by unutbu on 2008-05-04
When your system "hangs", have you tried CTRL-ALT-F2 to get to a virtual terminal? If you can, then log in and do:

```
ps axuw | grep gnome-terminal
```

You should get a bunch of lines that look something like:

```

lavarock    7988  0.0  2.2  92300 23696 ?        Sl   13:53   0:01 gnome-terminal --geometry 101x28+840+30
```

The number after 'lavarock' is the process id (PID).

To kill a process (that you own) you can type:

```
kill -9 7988
```
Kill all the hanging gnome-terminals and your system should 'unhang' itself hopefully. 

If, by the way, you launch gnome terminal with a command, such as
```

gnome-terminal --command="alsamixer"
```

It might be the command which is hanging, in which case you might have to use "ps auxw | grep ..." to search for the true hanging command.

---

### Post by lavarock on 2008-05-04
Thanks for the reply.  Yes I did know how to terminate those hanging terminals.  The problems is after they are terminated, I can't open anymore gnome terminals.  So far the only fix for it I know is to restart the computer.

---

### Post by unutbu on 2008-05-04
Hm, I just tried running your script, and I noticed I actually don't get multiple instances of gnome-terminal showing up under ps. I just get one, followed by lots of bash processes, one for each window. Did you kill all the bash processes too?

---

### Post by Zorael on 2008-05-04
Brainstorming:
```
gnome-terminal --geometry 56x21+1000+0 --hide-menubar &
sleep 0.5
gnome-terminal --geometry 56x21+1000+400 --hide-menubar &
sleep 0.5
gnome-terminal --geometry 56x21+335+400 --hide-menubar &
sleep 0.5
gnome-terminal --geometry 56x2+335+330 --hide-menubar &
sleep 0.5
gnome-terminal --geometry 56x2+335+270 --hide-menubar &
sleep 0.5
gnome-terminal --geometry 56x2+335+210 --hide-menubar &
sleep 0.5
gnome-terminal --geometry 39x2+0+650 --hide-menubar &
sleep 0.5
gnome-terminal --geometry 39x2+0+730 --hide-menubar &
```
Might work.

---

### Post by lavarock on 2008-05-04
> **unutbu said:**
> Hm, I just tried running your script, and I noticed I actually don't get multiple instances of gnome-terminal showing up under ps. I just get one, followed by lots of bash processes, one for each window. Did you kill all the bash processes too?

It should work... Just making sure I am not missing something, I saved the script in a file called openwindows, then chmod +x it, then used ./openwindows to open it.  Doing the above is working on my computer (albeit with the problem described in my first post from time to time).

> **Zorael said:**
> Brainstorming...
I will try that, thanks.

---

### Post by lavarock on 2008-05-04
> **unutbu said:**
> Hm, I just tried running your script, and I noticed I actually don't get multiple instances of gnome-terminal showing up under ps. I just get one, followed by lots of bash processes, one for each window. Did you kill all the bash processes too?

You are right, it seems that it doesn't open multiple gnome-terminal processes, but instead a bunch of bash processes.  (I wonder if this in general cause problems? I do see 8 gnome-terminal showing on my desktop)
I will try to kill all the bash processes next time when this issue arises again.

---

### Post by owlgorithm on 2008-06-26
I think this is the same problem:
[http://ubuntuforums.org/showthread.php?t=841756]("http://ubuntuforums.org/showthread.php?t=841756")

Unfortunately it doesn't have a solution yet either. I wonder, from some of the links on the other page, whether this is caused by a bug in gnome-terminal related to the --geometry argument.

---

