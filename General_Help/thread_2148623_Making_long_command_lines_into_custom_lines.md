---
title: "Making long command lines into custom lines?"
date: 2013-05-26
forum: General Help
---

### Post by RocketPenguin on 2013-05-26
Okay, so my question is, is it possible to make a very long (or any length) command into whatever you like, as in a phrase? I know you can do it in python, but can you do it for ubuntu's terminal command? I would like to shorten a rather lengthing command into a short word, or word phrase. I run a uTorrent server, and i usually have to start it by entering the command to start the internal server. for this, i have to go to a web page, copy and paste it into terminal. So, instead of putting the command, put something like "start utorrent' and it executes the command?

---

### Post by Dennis N on 2013-05-26
create an alias for your command.

---

### Post by deadflowr on 2013-05-26
Yep, bash_aliases is the way to go.

If you don't have one already make a file called .bash_aliases in your home folder. then write an alias
```
alias nameyouwilluse='the-command-that-is-super-long-that-the-alias-will-write'
```

Then save.
Open up a terminal and if any errors were made it'll tell you off the bat.
Then test it out.

---

### Post by HiImTye on 2013-05-26
or enter it into the shell before saving it in the file, then you can test it out right away, such as
```
$ alias test="echo it works really"
$ test well
it works really well
```
keep in mind that an alias can onoy accept input at the end, so if you want to reference it before that, you have to use a bash script or define a function, but it can still be useful. here's my tracksearch alias to search mpd's current playlist for a song
```

alias tracksearch="alias tracksearch; mpc playlist -f '%position%. (%time%) %artist%: %album% -  %title%' | grep -iE"

```
lets me do something like:
[http://imageshack.us/a/img541/8539/screenshot2013052600041.png](http://imageshack.us/a/img541/8539/screenshot2013052600041.png)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by RocketPenguin on 2013-05-27
Awesome! Thanks guys, it worked!! :D

---

