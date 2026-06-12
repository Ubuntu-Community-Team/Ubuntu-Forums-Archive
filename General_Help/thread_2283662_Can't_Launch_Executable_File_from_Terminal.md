---
title: "Can't Launch Executable File from Terminal"
date: 2015-06-23
forum: General Help
---

### Post by Kpenguin on 2015-06-23
Hi everyone,
I'm trying to launch an application from the terminal. The executable file is contained in a folder on my desktop. When I type in the path in terminal, it says "No such file or directory!" The file is marked as executable, and I can't think of anything that might be causing it to not work. Does anyone know what's causing this issue? I have a screenshot attached that shows the terminal and file properties.
Thanks!
Kpenguin
[ATTACH=CONFIG]262808[/ATTACH]

---

### Post by jamesisin on 2015-06-23
Most likely you need to set the execution bit:

> sudo chmod +x /path/to/file.ext

---

### Post by deadflowr on 2015-06-23
You might want to try to tweak the file manager to allow usage of executables.
Open the file manager go to edit >> preferences >> behavior.
The default is view, change it to either ask each time or run when open.

They should execute normal from then on.

Hope this helps.

---

### Post by matt_symes on 2015-06-23
Hi

Try this.

```
~/Desktop/Droidmote/droidmote
```

EDIT: 

To explain. 

You were trying to change directory to the actual file instead of the parent directory of the file. This will not run it.

As the file is executable you need to run the file itself by using the path to the file and the filename itself.

If you are in the same directory as the executable file you want to run then you need to precede the file with this ./ (as shown below) where <filename> is the file you wish to run.

**./**<filename>

Try this.

```
cd ~/Desktop/Droidmote/
``` 

```
./droidmote
```


Kind regards

---

### Post by mc4man on 2015-06-23
You can't cd to a file, so try (no need to ./ either
```
cd Desktop/Droidmote
```
then run script
./droidmote
or whatever it's named
or don't use cd to begin with...

---

### Post by jamesisin on 2015-06-23
Actually, looking more closely at your screenshot... are you attempting to cd into a file?  If the file you want to execute is on your desktop and called file.ext for example, you want to do this:

> cd ~/Desktop
sudo chmod +x ./file.ext

---

### Post by Kpenguin on 2015-06-23
Sorry, none of this worked. :( See attachments
[ATTACH=CONFIG]262811[/ATTACH][ATTACH=CONFIG]262812[/ATTACH]

---

### Post by matt_symes on 2015-06-23
Hi 

You typed it incorrectly.

```
~/Desktop/Droidmote/droidmote
```

and not

```
~/Desktop/Droidmote/droimote
```

EDIT: I had to fix my own typo so it looks like we're both doing it today :)

Kind regards

---

### Post by jamesisin on 2015-06-23
Ok, a quick primer on using the terminal.

The cd command changes directories (which you know), but what you seem to be missing is how the paths which typically follow cd are to be understood.

./ is a shorthand way to say "whatever directory I am in currently".  This is usually written out before the $ in your command prompt.  There is one exception to this and that is if your current directory is your home directory.

~/ is a shorthand way to say "my home directory".

All other paths begin with a / which means the root or beginning of your file system.

Mostly you will be interested in paths which begin with ~/

Also of use, when someone types file.ext what they are saying is "the name of the file"."the file extension".  As you have seen, not all files have extensions.  Nonetheless this is a pretty typical way of communicating the idea.

Finally, if you want to discover what your current directory is, what is called your working directory, you can ask the terminal to print your working directory:

> pwd

Hope that helps you keep moving forward.  And I hope that between Matt and myself we have helped you get your file executed.

---

### Post by jamesisin on 2015-06-23
Two more things about cd because they are very useful.

If you type cd by itself that is the same as typing cd ~/

../ means "the directory above the directory I'm currently in" and it can be compouned (so ../../ means "the directory above the directory above the directory I'm currently in").

---

### Post by Kpenguin on 2015-06-23
Thanks for your patience and help everyone, it's working now!

---

