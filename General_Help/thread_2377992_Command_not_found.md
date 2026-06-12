---
title: "Command not found"
date: 2017-11-18
forum: General Help
---

### Post by linuxnoob89 on 2017-11-18
What is this?  I hack around with Ubuntu varients on different machines, and get the same message when trying to install a VPN client from file.  Does any one have a way to make it work?

---

### Post by Holger_Gehrke on 2017-11-18
With as much INFORMATION as you have given us we can only guess. What client, what did you do and what did type that resulted in the error ?

My guess would be that you ran into the old "current directory is not in $PATH for security reasons"-problem when trying to run some kind of installer program. Prefix the command with './'.

Holger

---

### Post by linuxnoob89 on 2017-11-19
Sorry, the client is PIAv75.  I open the downloads folder, open terminal and enter 
'[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Sudo [/FONT][/COLOR]./pia-v75-installer-linux.sh' and get the command not found.  [COLOR=#4D4D4D][FONT=monospace]

[/FONT][/COLOR]

---

### Post by raja.genupula on 2017-11-19
yeah , you should be typing 'sudo' not 'Sudo'. 

and filename: pia-v75-installer-linux.sh , it must have permissions to be executable. 
Verify its permissions with 
> ls -l pia-v75-installer-linux.sh

If permissions not there to execute the file, change it with 
> chmod +x pia-v75-installer-linux.sh

and then try again.

---

### Post by linuxnoob89 on 2017-11-19
You are of course correct about the capitilisation of 'S' in sudo.  [COLOR=#000000]*chmod +x did the job, so many thanks!*[/COLOR]

---

### Post by raja.genupula on 2017-11-22
Glad your issues got solved. Please mark this thread as solved.

---

