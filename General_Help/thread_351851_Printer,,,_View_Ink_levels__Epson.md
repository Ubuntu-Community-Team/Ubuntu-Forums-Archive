---
title: "Printer,,, View Ink levels / Epson"
date: 2007-02-02
forum: General Help
---

### Post by delta99 on 2007-02-02
Hello

I installed a few things on getting my printer working, It works nicely... :)

However when I open 'printer tools>Epson Inkjet (Epson Inkjet Printer Utilities)
I cannot do any of the options, I get the error pictured below.

Please help me, thank you. Also another thing, is there any way of saving ink?? 
My cartiridges just seem to drain and the economy settings is too low quality, any suggestions?

Thanks again :)
delta99

---

### Post by david_2001 on 2007-02-02
I can suggest a way around the first problem.  In the days when I used KDE I never, ever managed to get the Epson Inkjet tools to work.  My solution was to use the console program escputil instead (Ubuntu has it in the universe repository).  It works like this for my Epson Stylus C80:
> david@darkstar:~$ sudo escputil -r /dev/usblp0 -m C80 -i
Escputil version 5.0.0, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

         Ink color       Percent remaining
             Black                      37
              Cyan                      38
           Magenta                      15
            Yellow                       7


---

### Post by deanjm1963 on 2007-02-02
There's a small application in the repos called mtink. I used it with success when I had an epson printer. It shows ink levels, cleaning, etc. Once installed open up a terminal and type

sudo mtink (and enter your password)

It likes to be run as root tho I had no problems running it as user in other distros. It takes one or two runs to get it up and running correctly, e.g. correct detection of printer, ink levels, etc. I found the first run it took a while initialise properly but just wait, then it all works.

hope it helps... and works!

---

### Post by david_2001 on 2007-02-02
> **deanjm1963 said:**
> There's a small application in the repos called mtink. I used it with success when I had an epson printer. It shows ink levels, cleaning, etc.

I hadn't come across mtink before.  Works for me!

---

### Post by delta99 on 2007-02-02
mtink looks promising! I will try it tomorrow and let you know.

thank you for helping :d

peace

---

### Post by delta99 on 2007-02-03
worked great thanks.

---

### Post by Spike-X on 2007-09-04
This works great, thanks!

---

### Post by DavidFourer on 2007-10-23
email from Jean-Jacques Sarton who created mtink:

> The problem is that mtink has no rights for reading and writing to
/dev/usblp0
The easyest way is to set the rights to srwxr-xr-x via  the command

sudo chmod 4755 /usr/bin/mtink

issued witin a terminal

Jean-Jacques

That got mtink working for me.  The scanner software had the same problem.  Now I just have to find out what's wrong with my printer--see below.

Low-ink-level light flashed on my new Epson CX-5000 scanner-printer.  Prints fine, and all the cartriges are new, from vacuum-sealed packages.  I bought printer and ink dircect from Epson.  I decided to check ink levels.  Escputil reports 50% level for black, 15%, 1%, 1%, for the colored inks.  Sometimes the light stops flashing by itself, so I re-run the escputil and get the same low ink levels.  Since I've barely got it out of the box, I also tried mtink utility and got same result.

What I don't understand is why Epson officially does not support Linux, but Linux-Foundation and all the Ubuntu people and Linux wikis all support Epson.  Everything I read said buy an Epson, and it prints and scans well.  But Epson tries to tell me that it won't work.  What will they say if I need warranty support for a hardware problem?

---

### Post by dasunsrule32 on 2008-03-22
> **david_2001 said:**
> I can suggest a way around the first problem.  In the days when I used KDE I never, ever managed to get the Epson Inkjet tools to work.  My solution was to use the console program escputil instead (Ubuntu has it in the universe repository).  It works like this for my Epson Stylus C80:

Or You can simply type:

sudo escputil -ir /dev/usblp?

This will give you the ink levels of any Epson printer hooked up via usb.

Yay! My first post in the Ubuntu community!

---

### Post by Paulo M. on 2008-05-09
Hello Buddies!
Please, can anyone help me...
I've read this thread and all the others I found about this issue, but I still can't get Mtink to run properly (can't find the printer) nor found escputil in any repository...

Thanks in advance!

(In escputil, I can only get info with the command "sudo escputil -ir /dev/usblp?" I saw here...
Is there other way of getting this info?)

---

