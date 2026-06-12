---
title: "is there any way to make printer settings persistant for specific printer only?"
date: 2021-05-03
forum: General Help
---

### Post by rebeltaz on 2021-05-03
What I mean is, I use a laser printer most of the time, but I also have a thermal label printer. When I print with the label printer, not only do I have to change the printer to which I am printing, but I also have to remember to change tabs and select the 4x6 paper size. That's not so bad but when I print normal pages on the laser printer, I have to always check the paper size tab to make sure that that is set correctly. Is there no way to associate one paper size (or any other settings) on a printer by printer basis?

---

### Post by dragonfly41 on 2021-05-03
If there is a config file (possibly hidden) associated with each printer it should be possible to write a simple script to toggle between different printer profiles.

---

### Post by rebeltaz on 2021-05-03
> **dragonfly41 said:**
> ... it should be possible to write a simple script...

That's easy for **you** to say! :)

---

### Post by dragonfly41 on 2021-05-03
> That's easy for you to say! 


If you gave some indication of your level of knowledge of scripting or even the types of printer perhaps we could home in on a script to try. You did join this forum 4 years before me!


If it was *my* problem I would look at automating the settings through CUPS UI.  I would create an automation script using Actiona tool. Or even xdotool. The key is driving the user interface automatically and Actiona does this nicely - at least for my workflows. I use it often to automate various commands and workflows (some quite complex).

---

### Post by gsahli on 2021-05-03
I'm not certain because I only have one printer connected now...
But, in the local CUPS server, there are settings for Default Options like: Media Size Media Source, Resolution.
To get access, use a browser, and enter this URL:
127.0.0.1:631
(this means, localhost, port 631 is the CUPS server on your computer)
Click on the Printers tab (you'll be asked for password at some point)
Click on your print-queue shown in blue on left side.
Go to Administration, then Set Default Options.
Make changes, then click Set Default Options, to save.

Now try it.

---

### Post by dragonfly41 on 2021-05-03
**QED** .. but my point is that this CUPS interface can be managed/toggled using Actiona (or other) script if you have multiple printers (as does OP).

---

### Post by rebeltaz on 2021-05-03
> **dragonfly41 said:**
> If you gave some indication of your level of knowledge of scripting or even the types of printer perhaps we could home in on a script to try. You did join this forum 4 years before me!
lol... that's no indication of my expertise. I can write some bash scripts - usually after searching for the bits I need because everytime I learn how to do something, I forget it soon thereafter and have to relearn it again next time I need to do it. 

> **dragonfly41 said:**
> 
If it was *my* problem I would look at automating the settings through CUPS UI.  I would create an automation script using Actiona tool. Or even xdotool. The key is driving the user interface automatically and Actiona does this nicely - at least for my workflows. I use it often to automate various commands and workflows (some quite complex).

See... to me actiona and xdotool are like greek. lol... but I will research those and see what's what. Thank you for shoving me in the right direction :)

---

### Post by rebeltaz on 2021-05-03
> **gsahli said:**
> 
Now try it.

I didn't know you could get to the cups server settings that way. I did that but I still have the same issue. The correct settings were already saved, but when I switch printers, the default settings for that printer aren't being selected. I thought maybe it was just Document Reader doing it since I'm working with PDFs, but I tried printing from gedit, too and I get the same issue.

---

### Post by dragonfly41 on 2021-05-03
[COLOR=#000000]> Thank you for shoving me in the right direction

It is only one direction which I use often.

Reading here [/COLOR][http://localhost:631/help/options.html](http://localhost:631/help/options.html)  I can see that the entire workflow of toggling printer settings could be command driven.
And I use Actiona for such CLI scenarios (including Google and AWS commands to give some idea).

---

### Post by gsahli on 2021-05-04
RE: CUPS. Disappointing that it doesn't do what it says. Like I said, I hadn't tried it in the real world.

---

### Post by dragonfly41 on 2021-05-04
Examples?

What does this command return?

[FONT=monospace][COLOR=#000000]```
lpstat -p -d
```[/COLOR]
[/FONT]

---

