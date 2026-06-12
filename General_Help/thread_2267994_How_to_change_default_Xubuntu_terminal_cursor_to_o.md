---
title: "How to change default Xubuntu terminal cursor to others (like i-Beam and underline)"
date: 2015-03-05
forum: General Help
---

### Post by flaymond on 2015-03-05
How to change the default cursor in Xubuntu, I Googled them at first...but not found ~/.config/Terminal/terminalrc

I found others than that :( and there is no terminal configure files..

Is there anyway I can fix/do this?

---

### Post by nerdtron on 2015-03-05
I don't think the default xcfe4-terminal has that option.

I prefer a better terminal such as Terminator.
"sudo apt-get terminator"

It can split the window into section and broadcast a single command to all terminals. You can change the cursor in it's preferences.

---

### Post by Toz on 2015-03-05
Actually, you can change the cursor shape in xfce4-terminal. See: [http://docs.xfce.org/apps/terminal/advanced]("http://docs.xfce.org/apps/terminal/advanced").

In a nutshell, create (if it doesn't already exist) the configuration file ~/.config/xfce4/terminal/terminalrc and add the following directive to it:
```
MiscCursorShape=TERMINAL_CURSOR_SHAPE_IBEAM
```
...or:
```
MiscCursorShape=TERMINAL_CURSOR_SHAPE_UNDERLINE
```

More info at the link above.

---

### Post by flaymond on 2015-03-06
[QUOTE=Toz]Actually, you can change the cursor shape in xfce4-terminal. See: [http://docs.xfce.org/apps/terminal/advanced](http://docs.xfce.org/apps/terminal/advanced).

In a nutshell, create (if it doesn't already exist) the configuration  file ~/.config/xfce4/terminal/terminalrc and add the following directive  to it:
     Code:
     MiscCursorShape=TERMINAL_CURSOR_SHAPE_IBEAM 
...or:
     Code:
     MiscCursorShape=TERMINAL_CURSOR_SHAPE_UNDERLINE 
More info at the link above.[/QUOTE]

Thank you. Sadly, I don't found any terminalrc directory...whenever I cd to xfce4..there is only couple of files that not helping for this case

Here is my view in terminal -


```
user@user:~/.config/xfce4$ ls
desktop  helpers.rc  panel  src  xfconf  xfwm4
```

I tried cd to each one of the directory, and still don't found any terminalrc  directory..

[QUOTE=nerdtron]I don't think the default xcfe4-terminal has that option.

I prefer a better terminal such as Terminator.
"sudo apt-get terminator"

It can split the window into section and broadcast a single command to  all terminals. You can change the cursor in it's preferences.
[/QUOTE]

Actually...I have done once before I reinstalling Xubuntu (for a reason) using terminal.

but I don't found any of terminal config file in this install....:(

Anyway,  thanks for the suggestion. It's cool though :)

---

### Post by nerdtron on 2015-03-06
The file and folder does not exist and you need to create a fresh one. I tested it and it works. Here note the contents of my terminalrc file:

```
kenneth@nerdtron:~/.config/xfce4$ mkdir terminal
kenneth@nerdtron:~/.config/xfce4$ nano terminal/terminalrc
kenneth@nerdtron:~/.config/xfce4$ ls
desktop  helpers.rc  panel  terminal  xfce4-screenshooter  xfconf  xfwm4
kenneth@nerdtron:~/.config/xfce4$ cat terminal/terminalrc 
[Configuration]
MiscCursorShape=TERMINAL_CURSOR_SHAPE_IBEAM
kenneth@nerdtron:~/.config/xfce4$ 
```

---

### Post by flaymond on 2015-03-06
[QUOTE=nerdtron]The file and folder does not exist and you need to create a fresh one. I  tested it and it works. Here note the contents of my terminalrc file:

     Code:
     [EMAIL="kenneth@nerdtron:~/.config"]kenneth@nerdtron:~/.config[/EMAIL]/xfce4$ mkdir terminal
[EMAIL="kenneth@nerdtron:~/.config"]kenneth@nerdtron:~/.config[/EMAIL]/xfce4$ nano terminal/terminalrc
[EMAIL="kenneth@nerdtron:~/.config"]kenneth@nerdtron:~/.config[/EMAIL]/xfce4$ ls
desktop  helpers.rc  panel  terminal  xfce4-screenshooter  xfconf  xfwm4
[EMAIL="kenneth@nerdtron:~/.config"]kenneth@nerdtron:~/.config[/EMAIL]/xfce4$ cat terminal/terminalrc 
[Configuration]
MiscCursorShape=TERMINAL_CURSOR_SHAPE_IBEAM
[EMAIL="kenneth@nerdtron:~/.config"]kenneth@nerdtron:~/.config[/EMAIL]/xfce4$ 
[/QUOTE]

Thanks! It's worked! :D

---

