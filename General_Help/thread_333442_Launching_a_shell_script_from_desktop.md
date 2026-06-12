---
title: "Launching a shell script from desktop"
date: 2007-01-07
forum: General Help
---

### Post by japan on 2007-01-07
I'm a relative Linux newbie, but I've run into a small problem.

I installed Neverwinter Nights using the instructions on the Bioware page on my install of Dapper. It works fine, but I'd like to have an icon on the desktop that launches the game.

The game's installed to "/home/andrew/nwn/", and run by executing a shell script called "nwn" from that folder. If I navigate to that folder and double click the script, it runs.

I tried to create a launcher which executed the comand "sh /home/andrew/nwn/nwn" but that doesn't work. If I try the same command in the terminal, it gives me a "no such directory" error.

Thinking that must be it, I backed up the script and edited it so all the references to directories were absolute, i.e. instead of "./nwmain" it has "/home/andrew/nwn/nwmain"

Now if I launch a terminal and navigate to the nwn directory, I can launch the game with a "sh nwn" command. If I try "sh /home/andrew/nwn/nwn" I get a segmentation fault error.

Am I missing something obvious? It seems this should be a relatively simple thing to do.

Thanks for any help.

---

### Post by Ocxic on 2007-01-07
right click on you desktop and click creat launcher, basiclly like creat shortcut in windows, but not really. put in all relitave info and click ok.

---

### Post by japan on 2007-01-07
> **Ocxic said:**
> right click on you desktop and click creat launcher, basiclly like creat shortcut in windows, but not really. put in all relitave info and click ok.

I did, but it still won't work. The command I'm using is "sh /home/andrew/nwn/nwn", but that doesn't seem to work either from a launcher or from the terminal. I can only seem to get the script to run by navigating to the "nwn" directory first, then using "sh nwn".

---

### Post by bodhi.zazen on 2007-01-07
Is it a bash script ?

Try:```
bash /home/andrew/nwn/nwn
```both in a terminal and in your launcher ...

---

### Post by aysiu on 2007-01-07
You can try this: ```
sudo mv /home/andrew/nwn /opt/
cd /opt/nwn
sudo chmod +x nwn
sudo ln -s /opt/nwn/nwn /usr/bin/nwn
``` and then create a launcher with the command *nwn*

---

### Post by phossal on 2007-01-07
Make it executable:

```
sudo chmod +x <script>
```

If it's a Bash script, you won't need sh to execute it.

---

### Post by japan on 2007-01-07
> **aysiu said:**
> You can try this: ```
sudo mv /home/andrew/nwn /opt/
cd /opt/nwn
sudo chmod +x nwn
sudo ln -s /opt/nwn/nwn /usr/bin/nwn
``` and then create a launcher with the command *nwn*

I'll try this in a sec, but could you explain what it does?

Using bash instead of sh has the same results I'm afraid.

EDIT: Tried the instructions above, same results. What is a segmentation fault, exactly?

---

### Post by reclusivemonkey on 2007-01-10
> **japan said:**
> 
The game's installed to "/home/andrew/nwn/", and run by executing a shell script called "nwn" from that folder. 

I would imagine that you need to navigate to the folder first before launching it. A standard shortcut to /home/andrew/nwn/nwn should of worked. However, now you've moved it to /opt and changed permissions, it might not be totally straightforward. If navigating to your nwn directory and then clicking on nwn shell script works, then in your bash script, use;

```

#!/bin/sh
cd /path/to/nwn
./nwn

```

and it should work. If the script is executable, there is no need to use sh or /bin/bash to launch it. I believe the reason you had problems before is that the shell script will be looking for things in its own directory, but as you launched it from your desktop, it was looking there.

---

### Post by LMelior on 2007-04-28
Sorry for reviving this thread, but I just wanted to say that adding the line changing the directory to the location of the shell script worked for me, as I was having the same problem as the original poster.  Should have thought of that myself.  Thanks a bunch!

---

