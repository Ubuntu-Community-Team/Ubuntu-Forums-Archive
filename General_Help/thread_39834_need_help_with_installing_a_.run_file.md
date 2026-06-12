---
title: "need help with installing a .run file"
date: 2005-06-06
forum: General Help
---

### Post by hampton on 2005-06-06
Hi there,

I am messing around trying to install America's Army just to see if I could get it to work. I downloaded the game and its a .run file (armyops23-linux.run). Whats the next step? Complete newbie here just trying to learn. Any help would be great!

-hampton

---

### Post by Gtaylor on 2005-06-06
Try this:
```

chmod a+x armyops23-linux.run
./armyops23-linux.run

```
It should be in their installation documentation somewhere.

Edit: Do that in a shell console in the same directory as the armyops23-linux.run file.

---

### Post by hampton on 2005-06-06
Thanks for your help Gtaylor,

It worked perfectly. Is there any way you can explain what the code means?

-hampton

---

### Post by Gtaylor on 2005-06-06
Sure. The first line (chmod) is the command that you use to change permissions on a file. In this case, you're adding execute permissions to the file you want to execute. Try doing a:
> 
chmod -x armyops23-linux.run
./armyops23-linux.run

And see what happens. The -x removes the executable flag.

The second line
> 
./armyops23-linux.run

Actually executes the file. The period denotes your current directory and if you directly reference a file, your shell will attempt to execute it. You could have done something like
> 
/home/yourhomedir/armyops23-linux.run

And it'd work as well. But the period followed by a slash means you're reference a file in your current directory (which you may see by typing **pwd**).

Hope that helps. Do some googling on 'Linux Permissions' if you want to better understand this stuff.

---

### Post by hampton on 2005-06-06
Thanks for taking the time to do that Gtaylor, it really did help.  :) 

-hampton

---

### Post by Gtaylor on 2005-06-06
[QUOTE=hampton]Thanks for taking the time to do that Gtaylor, it really did help.  :) 

-hampton[/QUOTE]
 Not a problem at all, and good luck!

---

### Post by dezgot on 2005-06-19
i did the same thing and it goes: 

```
Verifying archive integrity... All good.
Uncompressing ArmyOps 2.3.0 for GNU/Linux........Extraction failed.
Signal caught, cleaning up
``` 

and then returns me to the prompt.

Also noob here, help please?

---

### Post by allforcarrie on 2005-06-20
rite click and look at the propertys, there should be a run as exicuteable box. once you click that box, you should be able to install that way.

---

