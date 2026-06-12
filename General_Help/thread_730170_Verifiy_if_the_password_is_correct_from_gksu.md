---
title: "Verifiy if the password is correct from gksu"
date: 2008-03-20
forum: General Help
---

### Post by greis on 2008-03-20
Hi,

I am coding a bash script to ask the user to type his password.
The problem is that, when using the gksu command, if you type the wrong password, the screen to retype the password doesn't appear.

Here is:

PASS=`gksu -p -m "Type your password"`
echo $PASS


I know if you put a command at the end of the gksu, and you type the wrong passwd, the retype screen appears. Ex: gksu ls /

Is there any way to verify if the entered password was correct?

---

