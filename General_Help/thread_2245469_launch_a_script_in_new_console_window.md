---
title: "launch a script in new console window"
date: 2014-09-23
forum: General Help
---

### Post by baltic on 2014-09-23
Hi! 

I am trying to make a script run, when i click on it in nautilus (the default file manager), in a new console window, so i can see the output. After some googling, I've put this line in the begining of script file 
```
#!/usr/bin/gnome-terminal -x python
```
and made it executable. but what i get is 
```
Failed to parse arguments: Unknown option -x python

```
i've tried different terms and options, non is working. how do you launch scripts in new console window from nautilus?

---

### Post by Dreamer Fithp Apprentice on 2014-09-24
I haven't used Nautilus or gnome-terminal in a while and I suspect, though I may easily be wrong, there may be a way to do what you want with settings in the gui dialogue you get when you right click on the script and click "properties". Be that as it may, a less elegant way I'm pretty sure you can make work, is to write another script with something like this:```
#! /bin/bash
gnome-terminal -e path/to/your-script.sh
``` and double click it. Make both scripts executable of course. If that doesn't work you might want to type```
man gnome-terminal
```and press enter in a terminal and read the manual. Could be gnome calls the "execute the following command after opening a terminal" option something other that "-e" but I don't think so.

Now as to your script, I don't know anything about python. I've only used bash, tcsh, 4dos, and 4NT. But that shebang line looks pretty strange to me. Normally, in the scripts I've read, the first line of a script, the one that begins #! /bin/some_interpreter
doesn't specify a terminal emulator, but only the command interpreter that is supposed to run the script. You sure you got that part right? Are you writing this script from scratch (in which case you probably know a lot more about it than I do and can safely ignore this) or copying it from somewhere? If you are copying it, try it with whatever shebang line the original had. If that doesn't work, someone more familiar with the tools you are using will probably have a suggestion soon.

---

### Post by baltic on 2014-09-24
The main problem is, when i run a script, i dont see it's console output, since terminal does not open automatcally.
I've solved it combining your "non elegant solution" with nautilus scripts. Added the one below to the *~/.local.share/nautilus/scripts/Run in terminal* and made it executable
```
#! /bin/bash
for FNAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    gnome-terminal -x $FNAME
done

```
So in the context menu of a file, selected in nautilus, i can choose the "Run in terminal" script. I also had to change Profile settings in gnome terminal at *Title and Command->when command exits: hold the term open. *So it wont close the term window right away, and i can see the output.

Thanks!

---

### Post by CantankRus on 2014-09-24
If you're going to alter the terminal profile to stay open then you 
shouldn't need the script.
Just change nautilus preferences to "Ask each time" for executable text files.

---

### Post by baltic on 2014-09-24
Indeed. It works. I thought this option is only about "edit" or "run". But in reality it has the "run in terminal option"
Thanks for info!

---

### Post by CaptainMark on 2014-09-25
And instead of having all scripts that you run leave the terminal open, you could literally just add a single extra line ```
read
```to the bottom of your script that you wish to remain open, it will stop on this final line until you press enter.

---

### Post by baltic on 2014-09-25
the problem is, sometimes i run them from console. and maybe would want to batch them further. so i don't like the solution of hitting enter all the time :)

---

