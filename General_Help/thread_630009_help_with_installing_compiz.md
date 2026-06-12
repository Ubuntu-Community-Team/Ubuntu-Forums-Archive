---
title: "help with installing compiz"
date: 2007-12-02
forum: General Help
---

### Post by ktru on 2007-12-02
Hey everyone I'm trying to install compiz on my sony vaio nr laptop. I added the application from the add/remove under applications. My laptop has Intel GM965/GL960 Integrated Graphics Controller.

When I try to run it in terminal this is the response I receive

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

also when I try to turn on visual effects in Appearance I get a "Desktop effects could not be enabled" 

So im wondering if it's just my laptop's graphic's card?

---

### Post by jpittack on 2007-12-02
Install xserver-xgl via the package manager or entering

> sudo apt-get install xserver-xgl

in the terminal.  Hope this solves it.

---

### Post by ktru on 2007-12-02
> **jpittack said:**
> Install xserver-xgl via the package manager or entering



in the terminal.  Hope this solves it.

I tried the code you gave me, and i think it installed xgl. But for some reason I'm still getting the same thing back when I try compiz in terminal or appearence :(

---

### Post by jpittack on 2007-12-03
Are you using the restricted drivers?  You need 3-d to get compiz to work.

---

### Post by PeterJS on 2007-12-03
> **ktru said:**
> 
Blacklisted PCIID '8086:2a02' found 


Sorry, it's you're video card. There's something wrong with that model card that it doesn't handle something correctly and was blacklisted. See here for more info and a possible (**but not recommended**) work around:
[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

---

### Post by ktru on 2007-12-03
> **PeterJS said:**
> Sorry, it's you're video card. There's something wrong with that model card that it doesn't handle something correctly and was blacklisted. See here for more info and a possible (**but not recommended**) work around:
[http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112)

ahhh i hope the kinks get worked out :|

---

### Post by jpittack on 2007-12-03
Sorry to hear your card is blacklisted.  If it makes you feel better, if I close the terminal I use to start compiz, I lose my windows borders.

Sorry I couldn't be of help either.  It bums me out.  Glad Peter stopped by.

---

### Post by PeterJS on 2007-12-03
> **jpittack said:**
> Sorry to hear your card is blacklisted.  If it makes you feel better, if I close the terminal I use to start compiz, I lose my windows borders.

Sorry I couldn't be of help either.  It bums me out.  Glad Peter stopped by.

When you start compiz put a & after the command to run it in the background, and then close the terminal using the exit command instead of just closing the window, and compiz will stay running.

---

### Post by jpittack on 2007-12-03
freaking sweet man.  Thanks for the tip.  Could you explain what exactly I am doing by runing compiz in this way?

---

### Post by PeterJS on 2007-12-03
Not a problem. Usually when you're running something in the terminal it assumes that you want to run the program in the foreground. This is in fact a very good assumption, probably ~80% of what you do in the terminal is going to be foreground. When things are running in the foreground the terminal itself won't do anything else until the program finishes and all keyboard input goes to the running program. When the terminal is closed it closes all foreground programs as it assumes if they are foreground they're interactive and will need access to the terminal that's about to close.

The opposite of running something in the foreground is running it in the background. Putting the & symbol after a command tells the terminal that you want to run the command in the background. When programs are run in the background they operate differently, firstly as soon as you start them the terminal will come back ready to accept a new command, and the program will not print out any standard output, but will still print out errors (which can be quite annoying having a bunch of random error message jump up a few minutes late for no apparent reason). Since no output is printed, and the terminal itself takes back control of the keyboard you can't directly (via the terminal anyway) interact with background processes. Above I mentioned the a terminal will take any foreground programs with it when it closes, but will leave background programs running.

So, why do we want to run compiz in the background, first and fore most we want it to stay running after we close the terminal, but also we don't *need* to run compiz in the foreground as it doesn't use the terminal for input.

---

### Post by jpittack on 2007-12-04
Thanks a whole bunch.  I would keep getting an error about 8 bit something, and this solves it.

---

### Post by drenalinejunki92 on 2007-12-12
well At first this seems great being able to finally run compiz. I was able to keep  it running in the back round but of course as soon as i restart i have to start through the terminal again. on the compiz.org website it says" You can also store this value, where it is depends on your distribution, usually it is a matter of putting

SKIP_CHECKS=yes

in ~/.config/compiz/compiz-manager ."


[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)


I cannot seem to find this file 
in ~/.config/compiz/compiz-manager .

btw new to ubuntu  thanks in advance

---

### Post by kayel_justice on 2008-04-09
Hey.
Try this.
type "sudo gedit /usr/bin/compiz" in your terminal
put a # in front of the list with your blacklisted drivers
I have a vaio I think yours is intel as well.
The # comments it out.

---

