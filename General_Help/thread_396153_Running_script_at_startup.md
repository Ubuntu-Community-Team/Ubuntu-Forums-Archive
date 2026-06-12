---
title: "Running script at startup"
date: 2007-03-29
forum: General Help
---

### Post by shaqan on 2007-03-29
Hello.

I have a script I want to run at startup. I know there are several ways to make scripts start, but for some reason it wont start wherever I put it. I'm not that experienced in Linux but I'm getting very good at following guides :p 

I think my problem might be one or both of the following:
*I need to give the script a command as i run it. 
*I need to be superuser to run it.

"/etc/init.d/fancontrol start"

---

### Post by kerry_s on 2007-03-29
Put it in /etc/rc.local it will run as root at startup.

Example:

#!/bin/sh -e
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

exec /etc/init.d/fancontrol &

exit 0

---

### Post by shaqan on 2007-03-29
Thanks a lot Kerry_s

The "exec" part worked very well :KS

---

