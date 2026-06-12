---
title: "recover terminal output after crash"
date: 2007-10-24
forum: General Help
---

### Post by zorkerz on 2007-10-24
hi is the contents of a terminal saved in a log anywhere?

I am trying to run Civ4 Beyond The Sword and I get this weird crash were I am logged out of ubuntu. I would like to be able to see what is happening in the terminal that I run the game from. How can this happen?

cheers

---

### Post by rax_m on 2007-10-24
Hi 

If you are running the game from the terminal, then you could do the following:

> command > log.txt

where command is whatever you type in to start the game and then add the "> log.txt" bit. 
When it crashes go back to the directory you started the game from and there should be a log.txt file there.

Rax

---

### Post by zorkerz on 2007-10-24
Thanks a bunch!
this is so handy.
cheers

---

### Post by zorkerz on 2007-10-24
Shove my foot in my mouth. So I apparently don't know how this works.

Here is the command i tried ```
ninor@anoak:~$ > wine '/home/estle/media/games/civiv/Beyond the Sword/Civ4BeyondSword.exe' > log.txt
```

This creates two files log.txt and wine in my home folder. Both of witch are empty.

Ive been trying to get it to work with the free command (shows how much memory you have free) but i still get the two empty files one named free and there terminal ouput for free does not show up.

What am I doing?

---

### Post by zorkerz on 2007-10-24
Ok progress I think I get how this command works now.

'> free'
this creates an empty file named free (after the command) and prevents the terminal from showing the free commands output for some reason

'free > log.txt'
this creates a log file named log.txt with the output of the free command

so my question is this: why do I get an empty log file when I enter this command when I can see there is an output in the terminal?

```
wine '/home/estle/media/games/civiv/Beyond the sword/Civ4BeyondSword.exe' > log.txt
```When the game crashes it logs me out of ubuntu. Could the crash somehow prevent the information from being entered into the log?

thanks

---

### Post by rax_m on 2007-10-25
Hi .. sorry if my first explanation was a bit unclear.. i was tired ;) 

Basically what the > symbol does is re-direct the output that was initially supposed to go on the screen into some file eg. log.txt .. you can call it whatever you want obviously. 

Hmm... I'm not sure why it's not working when you using it with wine... Anything that should normally be printed in the terminal should go into the file immediately.  I think the syntax we're using with the wine command is causing problems.. but I can't figure it out right now. 

I'll do some checking in the mean time .. but maybe someone else might be able to help as well. 

Rax

---

### Post by zorkerz on 2007-10-25
Thanks for the help im still playing with it also at least until i find out whats going wrong. I will let you know if I figure out anything

---

