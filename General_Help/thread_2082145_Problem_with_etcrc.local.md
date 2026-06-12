---
title: "Problem with /etc/rc.local"
date: 2012-11-08
forum: General Help
---

### Post by mshajiali on 2012-11-08
HI guys i am new here in fact its my first post here so heres my problem
what i am trying to do is to make a script which saves the time and date at when my computer restarts 
Heres what i have done so far

> #!/bin/bash

sudo touch /var/log/restart.txt

su root

sudo last reboot > /var/log/restart.txt/

saved it as restart.sh ,made it sure that its executeable and this is what my /etc/rc.local file looks like
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/home/pc/restart.sh

exit 0

now the problem is its not overwriting my restart.txt file with the new restart time and date

dont know what to do now so please guys help me with this one

---

### Post by Lars Noodén on 2012-11-08
Will the script run manually?  It looks like there is a mistake in the last line.

This line

 sudo last reboot > /var/log/restart.txt/ 

should read

 sudo last reboot > /var/log/restart.txt

---

### Post by Dave_L on 2012-11-08
/etc/rc.local runs as root. The "sudo" and "su root" are not needed.

---

### Post by mshajiali on 2012-11-08
ya sorry my mistake but  the script is without the last slash and i want the script to run automatically when the computer starts and Dave_L if i remove sudo and su root it doesnt make any difference if i am not wrong

---

### Post by pqwoerituytrueiwoq on 2012-11-08
is the script executable? if not
```
chmod +x /home/pc/restart.sh
```
then your rc.local file will run the script you made

---

### Post by Lars Noodén on 2012-11-08
Right, /etc/rc.local runs as root so any script that it calls will also run as root.  So sudo and su are not needed or desired in that context.

---

### Post by mshajiali on 2012-11-08
yes as i have mentioned above that the script is executeable

---

### Post by rnerwein on 2012-11-08
> **Lars Noodén said:**
> Will the script run manually?  It looks like there is a mistake in the last line.

This line

 sudo last reboot > /var/log/restart.txt/ 

should read

 sudo last reboot > /var/log/restart.txt

hi
what's about to insert the following command into /etc/rc.local
[COLOR=Blue]
 echo "#[COLOR=Red] `[/COLOR]/usr/bin/who -r[COLOR=Red]`[/COLOR]" >> /home/xy/blu[/COLOR]

exit 0
 
 who -r will give you on every restart a line like 
          Runlevel 2   2012-11-08 13:06

---

### Post by Dave_L on 2012-11-08
> **mshajiali said:**
> ...if i remove sudo and su root it doesnt make any difference if i am not wrong

Actually, "sudo" and "su root" will prevent it from working.

---

### Post by pqwoerituytrueiwoq on 2012-11-08
```
cat /home/pc/restart.sh
```what does that give you? (i know it is the content of your script)

---

### Post by Slim Odds on 2012-11-08
> **Dave_L said:**
> Actually, "sudo" and "su root" will prevent it from working.
Exactly, since sudo will wait for a password

---

### Post by pqwoerituytrueiwoq on 2012-11-08
> **Slim Odds said:**
> Exactly, since sudo will wait for a password
sudo should not hurt anything try using sudo su then run a sudo command, you will see
root can use sudo to run something as another user

---

### Post by mshajiali on 2012-11-08
did what rnerwein said i just put the  command given by him in a script and and put its location in etc/rc.local and it worked 

Thank you all for your help

---

### Post by Slim Odds on 2012-11-08
> **pqwoerituytrueiwoq said:**
> sudo should not hurt anything try using sudo su then run a sudo command, you will see
root can use sudo to run something as another user
Reread the script... the first command contains a sudo, which will ask for a password.

---

### Post by pqwoerituytrueiwoq on 2012-11-08
> **Slim Odds said:**
> Reread the script... the first command contains a sudo, which will ask for a password.
not if run as root, sudo is used to run a command as another user default being root
using sudo poweroff in a script run as root is root telling root to run poweroff, it is just inefficient
when you are root you need to enter passwords cause you out rank everyone, when root tells you do so something you do not you don't ask root for a password

---

