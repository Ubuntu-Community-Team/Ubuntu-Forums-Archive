---
title: "Application shortcuts"
date: 2006-10-29
forum: General Help
---

### Post by Completenutter2 on 2006-10-29
Ok first off, sorry if this has been posted before, but I don't know what to search by, as I can't for the life of me think what these things are called, other than shortcuts.

In SuSE (or perhaps it was just KDE), I could put links to applications in ```
~/bin
``` and this would allow me to type the name of this file into "Run Application" and it would launch the file.

However, the closest thing I can replicate in Gnome/Ubuntu, is putting a file directly into my home directory, but for executable text files, it just opens the file up in Gedit. No doubt I'm missing something simple, but thought I'd ask you guys for some help before I start breaking things :)

TIA

Alex


Example of one of the files I'm trying to get to work:

```
#!/bin/sh
nautilus /home/alex/Music
```

---

### Post by Choad on 2006-10-29
executable text files must be made executable

chmod +x ~/myapp.py

or whatever. every file in linux is potentially executable, you just need to flag it so

shortcuts.... well im not entirely sure what you want to get done... could you elabourate with an example?

---

### Post by Choad on 2006-10-29
im running xubuntu, so its with xfce not gnome, but if i press alt-f2 to bring up the run dialog, then type in a program, such as mozilla-thunderbird it launches just fine...

---

### Post by Completenutter2 on 2006-10-29
The files are already executable, thats not the issue, and I can run them manually just fine.

An example, would be running a game in Cedega, instead of loading Cedega I can run the application by using the command:

```
cedega /directory/game/is/stored/game.exe
```

This will then launch the game. I might however want to save this in a file, and call it 'game' and be able to launch it in the same way I can other applications, such as 'mozilla-thunderbird' as you said.

---

### Post by CatKiller on 2006-10-29
If you want stuff in ~/bin to run from just the command name, you need to add ~/bin to your path - it isn't included by default in Ubuntu. I don't know how to do it, but there was at least one thread about it in the last few days.

As for executing text files through Nautilus, mine always asks me what I want to do - "Display", "Run" or "Run in Terminal". There's an option in the Preferences (Behaviour tab) to adjust this.

---

### Post by kerry_s on 2006-10-29
In ubuntu you would put it in /usr/bin for user application's.

---

### Post by invalid on 2006-10-29
You could toss that file into /usr/bin or /usr/local/bin to make it executable by name.

---

### Post by llamakc on 2006-10-29
Just add ~/bin to your path.

Edit your ~/.bashrc and add:

PATH=$HOME/bin
export PATH

then type: source ~/.bashrc 

and check it with `echo $PATH`

---

### Post by Completenutter2 on 2006-10-29
> **llamakc said:**
> Just add ~/bin to your path.

Edit your ~/.bashrc and add:

PATH=$HOME/bin
export PATH

then type: source ~/.bashrc 

and check it with `echo $PATH`

I just tried this, and the check 'echo $PATH' was good. Yet it still says it can't find the file when I try that, any ideas?

> **invalid said:**
> You could toss that file into /usr/bin or /usr/local/bin to make it executable by name.

I know this would work, but thats for all users.

---

### Post by llamakc on 2006-10-29
Well I believe my suggestion was faulty: doing the above makes $HOME/bin the ONLY path you would have. You'd have to add all of the other ones in .bashrc if you wanted it for that one particular user.

I tested it myself and after commenting it out, `source .bashrc` is erroring. I may have to logout/in. Sorry. (nope: just start a new Terminal)

Okay, you would have to add the following for that PATH declaration in .bashrc:

```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:$HOME/bin
export PATH

```

That should do it for you.

---

### Post by Completenutter2 on 2006-10-29
Ah, thanks, I was getting a bit worried when all of a sudden 'sudo' wasn't working, lol. 

This still didn't fix the fact that file isn't found when I type it into 'Run Command'

---

### Post by CatKiller on 2006-10-29
> **Completenutter2 said:**
> This still didn't fix the fact that file isn't found when I type it into 'Run Command'

Actually, I don't think that it would be - the Run Command box doesn't open a bash terminal. Maybe it would work if you ticked the "Run in terminal" box, or maybe you can set a different path variable somewhere.

---

### Post by llamakc on 2006-10-29
Perhaps Gnome needs to be told about the change? Log out/log in and see if the result is any different.

---

### Post by Completenutter2 on 2006-10-29
Will do, when I get a chance to log off. Will get back to you on the outcome.

---

### Post by Completenutter2 on 2006-10-30
> **CatKiller said:**
> Actually, I don't think that it would be - the Run Command box doesn't open a bash terminal. Maybe it would work if you ticked the "Run in terminal" box, or maybe you can set a different path variable somewhere.

Running it from the 'Run Command' window doesn't work, I just tried ticking the 'Run in Terminal' box, didn't work either.

So I opened a terminal, and typed in 'music' (name of the file to open up my music folder, and up popped my music folder.

Luckily this isn't something it is overly troublesome, just means I need to click some more, so I'll survive without it for now, but it'd be nice to figure it out, I have no doubts that its possible.

> **llamakc said:**
> Perhaps Gnome needs to be told about the change? Log out/log in and see if the result is any different.

No change.

---

