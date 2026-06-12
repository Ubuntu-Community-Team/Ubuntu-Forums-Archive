---
title: "Steam + ALT F2."
date: 2006-08-27
forum: General Help
---

### Post by Roasted on 2006-08-27
Since Steam is a Windows program, is that why I can't hit ALT F2 and find Steam to launch it? Up until now I've just double clicked the icon on the desktop, but I hate having ANYTHING on the desktop...

---

### Post by peabody on 2006-08-27
> **Roasted said:**
> Since Steam is a Windows program, is that why I can't hit ALT F2 and find Steam to launch it? Up until now I've just double clicked the icon on the desktop, but I hate having ANYTHING on the desktop...

Put it in a folder then ;) .

The command you need to run for steam to work is not just one word.  It's basically a big long wine command.  Open the desktop file in a text editor and you'll see what I mean.

---

### Post by Roasted on 2006-08-27
How do I open it in a text editor? Is what's in the text editor what I'd put in ALT F2 to launch it?

---

### Post by kaptainlange on 2006-08-27
The reason steam isn't openable with just a simple command is because it isn't located in your path.  Your path is a kind of list of locations the shell looks for commands in.  You can see your current path by typing:

```

echo $PATH

```

That should output a list of the current directories the shell is looking for commands in.

You could put the command that's in that text file into an executable script located in a folder belonging to your PATH.  That way you could just type something like "steam" at command line or run to get it up and running.

The script would looking something like this.

```

#!/bin/bash
wine /run/steam/executable

```

Then chmod it to be executable.

And you could place that somewhere like, /home/yourname/bin though I don't think that directory is in your default path.

---

### Post by Roasted on 2006-08-27
No, it's not. So now that it's not I'm kind of confused over how to do this... Either that or it's entirely too early and I'm not thinking clearly enough. :confused:

---

### Post by maka on 2006-08-27
> **Roasted said:**
> No, it's not. So now that it's not I'm kind of confused over how to do this... Either that or it's entirely too early and I'm not thinking clearly enough. :confused:

type this in a terminal:
```

sudo pico steam

```

add these lines into that file:
```

#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/Steam/
wine Steam.exe

```
[B]
press Control+X and hit Y for yes to save the file.[/B]
then type:
```

sudo chmod +x steam
sudo mv steam /usr/local/bin

```

once that is done, you should be able to alt+f2 and type in **steam** and enter to run steam ;)

---

### Post by Roasted on 2006-08-27
Hm, so what did each step essentially do here? 

Also, ALT F2 doesn't display any icons or anything, but if I just type steam and hit enter, steam pops up. I assume that's how it's supposed to be - figured I'd make sure.

---

### Post by maka on 2006-08-28
> **Roasted said:**
> Hm, so what did each step essentially do here? 

Also, ALT F2 doesn't display any icons or anything, but if I just type steam and hit enter, steam pops up. I assume that's how it's supposed to be - figured I'd make sure.

what you did was basically create a custom launcher called steam.

in the file, you go into the directory where Steam.exe is located and run it with wine.

then you made this launcher/file executable and moved it into the bin folder where you can run it from anywhere (ie with alt+f2)

and no icon shows up because we didn't set up one for the launcher, which is fine because its not necessary.

---

