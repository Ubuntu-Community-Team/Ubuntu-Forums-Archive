---
title: "How do i avoid having to open new terminal /-tab"
date: 2013-05-31
forum: General Help
---

### Post by lavhmrps on 2013-05-31
Hi, 

Is there a way to run programs from the terminal without having to open a new terminal / tab after program start?
Ubuntu 13.04

Thanks in advance

---

### Post by sanderj on 2013-05-31
Put a " &" at the end of the command line?

---

### Post by lavhmrps on 2013-05-31
Thanks for answer! 

It still runs all the output in the terminal window, but allows me to Ctrl-C without exiting the program.
When i tried Ubuntu 12 the program just opened and thats was it. Isnt there a way to do this in U13 ?

---

### Post by sanderj on 2013-05-31
What is your ultimate goal? If you want no terminal and no output at all, press ALT - F2, and then type the command.

---

### Post by lavhmrps on 2013-05-31
It would be no output in the terminal.
I know i can do the Alt-F2 thing, but since im trying linux i want to do as much from the terminal as possible :)

edit: typo

---

### Post by CatKiller on 2013-05-31
If you're looking to do sensible cool stuff in the Terminal then it's all about screen. Not strictly necessary in this case, but awesome nonetheless.

---

### Post by efflandt on 2013-05-31
You may want to consider installing **screen** if you want multiple sessions in one terminal.  Example [http://www.thegeekstuff.com/2010/07/screen-command-examples/](http://www.thegeekstuff.com/2010/07/screen-command-examples/)

---

### Post by HiImTye on 2013-05-31
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you could suppress it's output and fork it
```
command -opts &>/dev/null &
```you can also hit ctrl+z while a program is running and then do the same thing
```
command
# -- ctrl+z --
bg &>/dev/null
```
if you want to return to it instead
```
command
# -- ctrl+z --
fg
```
screen is also a useful tool if standard flow control isn't enough

---

### Post by markbl on 2013-05-31
Note that tmux has essentially superseded screen nowadays. If you are learning something new you may as well learn tmux. It has more sensible defaults and a few better features. I have used screen for 20 years but use tmux on all modern linux/unix systems now.

---

### Post by lavhmrps on 2013-06-01
How do i 'undo' this command
```
[COLOR=#000000][FONT=Ubuntu Mono]command -opts &>/dev/null &[/FONT][/COLOR]
```

Im gonna try out tmux / screen 

Thanks for the tips

---

### Post by HiImTye on 2013-06-01
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you would just kill it and then start it again
```
pkill command
command
```

---

