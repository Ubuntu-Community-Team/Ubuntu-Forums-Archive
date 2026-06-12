---
title: "Regaining control"
date: 2004-11-05
forum: General Help
---

### Post by trico on 2004-11-05
First a little background:  I'm working from home today on my Ubuntu Linux system.  I'm writing a small python program to analyze some trace files of the I/O activity of a graphics adapter.  I added a new feature to my program which turned out to be ill concieved.  It caused the memory requirement to increase linearly with time and after a while it was into the swap area and then had used up the swap area.  

I had started the program with the CLI, but had long since gone on to reading mail and looking at stuff on the web while it ran.  By the time I noticed the chatter of the disk and looked with the system monitor to see what was going on - I was just in time to see the use of the swap file max out. 

At this point I had no real control over the system. I would have liked to start a new instance of Terminal and kill the offending job.  The mouse moved, but not in real-time.  I'd move the mouse a quarter inch and after 30 seconds or so the mouse pointer would move to a new position.  The keyboard was even less responsive.  I never did get it do do anything.

How do I regain control of the system in this situation?  Is something maladjusted?  Should the mouse or the keyboard have a higher priority than it does?  Or is there some magic key combination that will do the trick.

To Linux's credit, I left things alone and about 8 minutes later the program completed and I had control once again.  But it would have been nice to be able to kill the program while it was driving the system whacko.

Any suggestions?
Trico

---

### Post by jdodson on 2004-11-05
you can run "top" find the process and its "PID" and then type "kill <pid>" at the console.  that should get things back to normal.

---

### Post by trico on 2004-11-05
Once I could get to a Terminal - yes, I could do that.

The problem was that the mouse was unresponsive.  So was the keyboard.  Lacking a mouse and/or a keyboard I was unable to open a new Terminal.

My guess is that they were unresponsive because of the heavy swapping going on.  

Trico

---

### Post by mr_ed on 2004-11-05
[QUOTE=trico]Once I could get to a Terminal - yes, I could do that.

The problem was that the mouse was unresponsive.  So was the keyboard.  Lacking a mouse and/or a keyboard I was unable to open a new Terminal.

My guess is that they were unresponsive because of the heavy swapping going on.  

Trico[/QUOTE]
 Um, buy more RAM?  ;)

There's not much you can do in a case like that.

On my parents' machine, I ended up opening 110 instances of Eye of Gnome, instead of 110 pictures into 1 instance of Eye of Gnome.  Needless to say, there was a lot of heavy swapping going on.  (and the system was completely non-responsive)

---

### Post by jwenting on 2004-11-05
What I've done is make sure I can always use ssh to get into the machine from a remote system.
This does require installation of openssh-server package.
In the past this has saved me more than once when an X configuration error caused the screen to not work :)

---

### Post by trico on 2004-11-05
Interesting idea.  I don't have another Linux box at home, but I suppose I could telnet in from a windows box as well...

Thanks,
Trico

---

### Post by Rancoras on 2004-11-05
Telnet is unsecure.  Use putty for windows and SSH into the box.

---

### Post by josel on 2004-11-05
But using telnet or ssh from another machine is only possible if you have another machine and it is  connected.
When things go irresponsive - and it happens sometimes - i miss a feature where i allways can press a key combination, and get a list of processes that i  can terminate.  Probably this can be done with some kind of process priority.

---

### Post by -synapse- on 2004-11-05
[QUOTE=josel]But using telnet or ssh from another machine is only possible if you have another machine and it is  connected.
When things go irresponsive - and it happens sometimes - i miss a feature where i allways can press a key combination, and get a list of processes that i  can terminate.  Probably this can be done with some kind of process priority.[/QUOTE]
 My suggestion would be to kill X using:
CTRL + ALT + BACKSPACE 
Then do top and then kill the process.

---

### Post by josel on 2004-11-06
[QUOTE=-synapse-]My suggestion would be to kill X using:
CTRL + ALT + BACKSPACE 
Then do top and then kill the process.[/QUOTE]

I have not had yet had this problem on ubuntu but remenber it on Mandrake. Ctrl Alt Backspace killed X sometimes, sometimes it jus set the machine on standby mode and sometimes nothing happened.  Besides its more interesting to kill the application responsable than X11 :-)

Three or four times i have had problems with ubuntu where they keyboard was dead sudenly.. no swapping going on.  I have no idea what process dies but could the responsable process be activated if no keyboard input is possible for say 60 sec? - I can tell when this happens by hitting caps-lock and seeing that the LEDs dont acitvate.

---

### Post by olejorgen on 2007-01-18
I guess the CTRL + ALT + 1,2,3,4,5,6 terminals was unresponsive too?

---

