---
title: "Trying to set &quot;PROGRAM_FILES&quot; variable"
date: 2008-04-15
forum: General Help
---

### Post by Alucard-sama on 2008-04-15
Alright so I got sick of having to type out cding to my Program Files folder every time I wanted to run a program in Wine so I decided to make a variable for it [I thought it'd also be a good learning experience since I figured I'd run into trouble somewhere since I'm such a n00b at bash [comparitively speaking anyway].

So anyways to set my Wine Program Files folder to a variable I typed
> PROGRAM_FILES="/home/alucard-sama/.wine/drive_c/Program\ Files/"

But of course this doesn't work because when the command line sees this it interprets it as setting the PROGRAM_FILES variable to be "/home/alucard-sama/.wine/drive_c/Program Files/" which it's supposed to do when I invoke the actual variable.
So how do I get it to include the "\" in the actual variable?

---

### Post by cm.squared on 2008-04-15
So far as I can tell you would need to quote the variable when you use it, as in:
```
cd "$PROGRAM_FILES"
```

What may be easier is to make an alias in your .bashrc file (in your home directory) to the effect of:
```
alias cdw="cd $HOME/.wine/drive_c/Program\ Files/"
```

While your at it you could alias the actual programs you want to run under wine like this:
```
alias winfox="wine $HOME/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe &"
```

Aliasing is just a way to make the shell associate an abbreviated command, or alias, with another command.  By putting the alias command in your .bashrc file it will be executed every time you open a terminal, so you'll be able to use the alias without having to manually type it when you open a shell.

---

### Post by cm.squared on 2008-04-15
Also, the ampersand at the of the command puts the process in the background, so you can go on using the terminal (try it with and without the & if that isn't clear).  Beware that if you close the terminal window in which you started a process the program will be killed.

---

### Post by Alucard-sama on 2008-04-15
Thanks, aliasing stuff does exactly what I needed :) and thanks for the ampersand tip too :)

---

### Post by cm.squared on 2008-04-15
You're welcome.  Glad I could help.

---

