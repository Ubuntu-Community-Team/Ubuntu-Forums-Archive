---
title: "Close terminal window with script"
date: 2007-09-11
forum: General Help
---

### Post by o3rat on 2007-09-11
I just installed matlab 7 and I want to run it from a launcher in the top toolbar.  The problem I'm having is that I have to launch matlab from terminal. if I run 'matlab &' and type 'exit' after matlab opens the program runs fine without the terminal. Is there anyway I can make a script, that i can launch, like matlab_run : ```
 #!/bin/bash
matlab &
exit 
```that will open temrinal, run matlab, and then close the terminal? As it stands the matlab_run above doesnt work.

Thanks for the help.

---

### Post by prince_niceguy on 2007-09-11
why not run the command directly?

i am sure you would have tried that.. but just curious to know what happened?

---

### Post by bettlebrox on 2007-09-12
try this:

xterm -e mathlab

From the xterm man page:
[INDENT]
     -e program [ arguments ... ]
               This option specifies the program (and its command line arguments) to be run in the  xterm  window.
               It  also  sets  the  window title and icon name to be the basename of the program being executed if
               neither -T nor -n are given on the command line.  This must be the last option on the command line.[/INDENT]

---

### Post by o3rat on 2007-09-12
> **bettlebrox said:**
> try this:

xterm -e mathlab

From the xterm man page:[INDENT]
     -e program [ arguments ... ]
               This option specifies the program (and its command line arguments) to be run in the  xterm  window.
               It  also  sets  the  window title and icon name to be the basename of the program being executed if
               neither -T nor -n are given on the command line.  This must be the last option on the command line. 
[/INDENT]


Maybe im doing it wrong, but when I add 'xterm -e' before matlab it opens another window and still doesnt close the original window.

---

### Post by bettlebrox on 2007-09-13
Does the terminal window close when you close mathlab?

---

### Post by peterpat on 2007-09-14
> **o3rat said:**
> I just installed matlab 7 and I want to run it from a launcher in the top toolbar.  The problem I'm having is that I have to launch matlab from terminal. if I run 'matlab &' and type 'exit' after matlab opens the program runs fine without the terminal. Is there anyway I can make a script, that i can launch, like matlab_run : ```
 #!/bin/bash
matlab &
exit 
```that will open temrinal, run matlab, and then close the terminal? As it stands the matlab_run above doesnt work.

Thanks for the help.

Try add this 

   alias matlab='matlab & exit'

to /home/yourlogin/.bashrc
close your terminal and reopen it then try "matlab" again I think the term window should be gone after command line is executed.

---

### Post by o3rat on 2007-09-23
I just tried adding that line. The terminal window does end up closing, but as soon as it does matlab stops loading and closes as well,

---

### Post by peterpat on 2007-09-29
I think you should first try the command line ie. matlab & exit manually if it succeeds to open the matlab program and then exit the terminal leaving the matlab to continue. I insist it has to work as the book says & is to send the preceding command running in bg and do the next command on fg.

---

### Post by Wolki on 2007-09-29
"exec matlab" should replace the terminal with matlab.

---

### Post by peterpat on 2007-10-15
Hmm. I had tried myself, certainly the "exec metlab" will do it!

---

### Post by M_E_nerd on 2007-10-31
Have you tried using nohup?  I don't use it very often, but it has been helpful in situations like this.  Try:

nohup matlab 

you can use this directly on the command line, but I had trouble running it within a script.  I am sure there are more elegant ways to use nohup, but like i said, I don't use it all too often.  Maybe someone else knows more.

Good luck!

---

### Post by eneth80 on 2007-12-20
I am facing the same problem. I am trying with the following possibilities, but my matlab has become slower (I should reboot).
nohup matlab &
matlab &! exit
matlab &exit (and not matlab & exit)
disown
osascript -e 'tell app "Terminal" to close every window whose frontmost is true' &
then I read in another forum: "f a job is started with `&|' or `&!', then that job is immediately disowned."

or try 

#!/bin/bash
nohup matlab &
osascript -e 'tell app "Terminal" to close every window whose frontmost is true'


maybe you get the right solution from these tips.

now I have found that if you launch matlab,do Ctrl+Z on the open terminal and type exit the terminal goes off.
ale

---

### Post by Balk2K on 2008-03-05
Did anybody get a solution to this to run from a launcher without a terminal?  Why do shell scripts behave differently when you run them from a launcher as opposed to running them in a terminal anyway?

---

### Post by murataht on 2008-03-05
If I understand your problem correctly, I think you don't have to write a script.

what you should do is 
1) right click on the panel, and from the pop up menu choose "add to panel". (gnome panel).
2) and choose the button from the top of the dialog which says "custom application launcher". this shows a dialogue box. 
3) Give a name (for example "Matlab"), enter the command (in your case, it is "matlab", maybe with full path: "/usr/local/bin/matlab", if it is not in the PATH). Even you can give it a matlab icon. 
 
click OK, Voilà! it should work now.

this worked for me for other applications. hope it works for you too.

Good luck!

---

### Post by Balk2K on 2008-03-06
yes, it does work with most applications, however this issue with  matlab is different.
When you run the command 'matlab' it only shows the splash screen for a few seconds and then exits.  If you run the command 'matlab' from the terminal, it will work.
I tried to make a script to run it but when you select 'run' it also doesn't work, it only works if you click 'run in terminal'

---

### Post by kwood on 2008-04-08
The command to start from the window manager is 

matlab -desktop

(see matlab -h for other startup options)

---

