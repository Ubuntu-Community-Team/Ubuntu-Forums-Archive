---
title: "Don't close the program when closing the terminal"
date: 2007-04-01
forum: General Help
---

### Post by Kalixa on 2007-04-01
Hello. I was wondering if anyone could tell me how to launch a program from the terminal so that when you close the terminal that program is still running?

---

### Post by 23meg on 2007-04-01
Put an ampersand ("&") at the end of the command. 

You can also use the "Run Application" dialog (Alt+F2).

---

### Post by Kalixa on 2007-04-01
> **23meg said:**
> Put an ampersand ("&") at the end of the command. 

You can also use the "Run Application" dialog (Alt+F2).

I tried doing a lyx& and a vlc& command but the programs were still dependant of the terminal.

---

### Post by 23meg on 2007-04-01
You need to put a space between the name and the ampersand.

```
nautilus &
```

---

### Post by Spr0k3t on 2007-04-01
Another option would be to do a CTRL-Z, then type bg to send the task to the background.

---

### Post by WW on 2007-04-01
Whether or not you put a space between the command and the ampersand is not relevant. The behavior depends on the command itself.  If you run nautilus like this
>  nautilus &
or
>  nautilus&
and then kill the terminal, nautilus will remain running.  On the other hand, if you run vlc (or gedit, or many other programs) like this, it will die when the terminal is closed with the "Close Window" button.

Edit:
Actually, if you run
> $ vlc &
and then kill the terminal by clicking on the "Close Window" button (the X in the upper right of the terminal), vlc will also be killed. If you use the **exit** command, e.g.
> $ vlc &
$ exit
vlc will remain running.

---

### Post by 23meg on 2007-04-01
The ampersand tells the shell to run the program in the background and report its process ID and job number, but yes, some graphical programs don't respect this. 

The rationale of getting used to putting a space between the ampersand and the command would be that an unspaced ampersand has another completely different role in I/O redirection syntax. 

To me it seems a better idea to just hit Alt+F2 and start typing the program's name. It will autocomplete without having to press the Tab key, and you can quickly choose the last few applications you ran with the arrow keys.

---

### Post by Spr0k3t on 2007-04-01
Yeah, but it would be nice to have a list of files rather than just autocomplete for one.

---

### Post by 23meg on 2007-04-01
> **Spr0k3t said:**
> Yeah, but it would be nice to have a list of files rather than just autocomplete for one.

List of which files?

---

