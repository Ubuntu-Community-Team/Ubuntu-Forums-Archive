---
title: "close an application window from command line?"
date: 2008-05-12
forum: General Help
---

### Post by jonkulp on 2008-05-12
Does anyone know how to close an application window from the command line?  Here's what I want to do.  I'm working in the Texinfo format and need to preview my work in a web browser.  I've written a shell script to handle the conversion from texinfo into html, redirecting files into appropriate directories, and it ends with a command to open the newly-created .html file in firefox.  This all works fine.

What I'd like to do is add a command to the script that will close the current tab or window in firefox before displaying the new version of the document.  Otherwise it keeps opening a new tab every time I run the script and I end up with lots of tabs open.  

I'd also like to be able to do this with Acrobat Reader, as I also work with Lilypond music notation engine that displays output in .pdf format, and I have to manually close the current acroread window every time I run my lilypond script.  Thanks,

Jon

---

### Post by SgtDude on 2008-05-12
I'm not sure exactly how to do this off of the top of my head, but I'm pretty sure of the components.

Basically, you'll need to find firefox's process number with
```
ps -ef | grep firefox
```
and pipe that into a command that will filter out all but the 2nd word (the PID in this case), and pipe that into "kill".

Sorry I don't know the specifics, but hopefully this will point you in the right direction.

---

### Post by SpaceTeddy on 2008-05-12
mhm - i am far from an expert on this - but how about you "remember" the pid of the programm you just started and next time your run your script, it checks if the last pid exists, and kills it - then restart firefox/acrobat/whatever...

this is just an idea - i don't know if this acctually works :(

---

### Post by jonkulp on 2008-05-12
Thanks for the responses, guys.  I can't quite make it find the process id and kill the process automatically.  But, I don't really want to kill the process, anyway.  What I'm after, really, is a command-line equivalent to the "Ctrl+W" keystroke that closes a window without quitting the application.  Is this possible?  JK

---

### Post by sdennie on 2008-05-12
You could use wmctrl.  To install it:

```

sudo apt-get install wmctrl

```

To close a window:

```

wmctrl -c "The title of the window"

```

---

### Post by jonkulp on 2008-05-13
Many thanks for this, vor!  Just what I needed.  I've added it to my scripts and it works just right.

I notice that you're in Buenos Aires, a city I visited for a few weeks while doing research for my doctoral dissertation.  That was one of the best times of my life.  Wish I were there so I could buy you a cafe con leche y tres facturas!  Gracias! :)

---

### Post by sdennie on 2008-05-13
> **jonkulp said:**
> 
I notice that you're in Buenos Aires, a city I visited for a few weeks while doing research for my doctoral dissertation.  That was one of the best times of my life.  Wish I were there so I could buy you a cafe con leche y tres facturas!  Gracias! :)

Hah.  I'm surprised you made it out.  It's quite common for people to come visit and, several years later, realize they forgot to leave.

Glad wmctrl worked for you.

---

### Post by bodhi.zazen on 2008-05-13
nice one vor :)

you can also use xkill

Open a terminal, type in xkill

your cursor will change to a cool skull and crossbone -> move it to the mis-behaving window, click mouse - > poof

---

### Post by Vashu on 2008-05-13
I ussually do either "xkill" or "sudo killall appname". but that last one might not allways be your best choice.

---

### Post by bodhi.zazen on 2008-05-13
> **Vashu said:**
> I ussually do either "xkill" or "sudo killall appname". but that last one might not allways be your best choice.

kill / killall / pkill does not always work. If the application refuses to close you may need to add some flags.

kill -1 PID

kill -9 PID

You (I) get the PID with

ps aux | grep appname

---

