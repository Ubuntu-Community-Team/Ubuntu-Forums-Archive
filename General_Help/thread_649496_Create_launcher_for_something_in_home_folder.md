---
title: "Create launcher for something in home folder?"
date: 2007-12-25
forum: General Help
---

### Post by Tanjer1588 on 2007-12-25
ok so i have a number of aplications in my home folder in there own file that i would like to make some launchers for but every time so far it has not worked for me. The two main ones i want launchers for are sauerbraten and gmail notify. Saueraten is a .sh file and notify is a . py why i click them it opens a window asking me what to do, ask's me to Run in terminal, Display, Cancel, and Run. when i hit Tun in terminal or Run they work just fine. I was told before i could make a launcher that runs a terminal command such as
```
./notifier.py
or
./sauerbraten_unix
```
My problem here is that i have to naviagate to the folder to run that line, and when i open terminal im not in thos folders. so i was wondering if there is a line of code that would navagate to my folder and run my program for me so i could put that into my launcer, or if there is some other way.

thank you

---

### Post by xelapond on 2007-12-25
You could make a bash script to cd into the directory.  It would look something like this:

```
 #!/bin/bash 
##Change into the directory
cd <Directory>
##Run the script
notifier.py

```

Hope that helps!

---

### Post by Tanjer1588 on 2007-12-25
> **xelapond said:**
> You could make a bash script to cd into the directory.  It would look something like this:

```
 #!/bin/bash 
##Change into the directory
cd <Directory>
##Run the script
notifier.py

```

Hope that helps!

I dont know how to use bash scrips at all, do know of a tutuoril that can show me how to do that? and how would i use the bash scrip in the launcher?

---

### Post by xelapond on 2007-12-25
Heres a really quick guide:

[http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html](http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html)

Pretty much you put that in a file ending in .sh(GmailNotify.sh).  Then you run:

```
$ chmod ugo+x your_shell_script.sh
```

Then you can just double click the script and it will act just like any normal application.

Hope that helps!

---

### Post by Tanjer1588 on 2007-12-25
Ill read that and see if it helps, thank you

---

### Post by Tanjer1588 on 2007-12-25
I read it but was really confused, didnt help a lot but thank you, Could some one show me a script or something that i could run that would CD from 
User@user-desktop:~: to User@user-dekstop:~/sauerbraten$ and then execute ./sauerbraten_unix?

that would be most helpful

thanks again

---

### Post by TidusBlade on 2007-12-25
You can create the launcher on the desktop, Im pretty sure of that, and then drag it into the home folder..?

---

### Post by xelapond on 2007-12-28
The below script is all you need.  Just replace <directory> with the directory the script is in.

 #!/bin/bash 
##Change into the directory
cd <Directory>
##Run the script
notifier.py

---

### Post by Tanjer1588 on 2007-12-29
> **xelapond said:**
> The below script is all you need.  Just replace <directory> with the directory the script is in.

 #!/bin/bash 
##Change into the directory
cd <Directory>
##Run the script
notifier.py

Ok so i place this into a text file right, then save is as a .py and then how do i use it from there

---

