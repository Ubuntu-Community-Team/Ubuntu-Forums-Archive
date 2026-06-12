---
title: "Can you give a user privilages to a root command?"
date: 2007-01-02
forum: General Help
---

### Post by Scorpuk on 2007-01-02
Is there any way of giving a user rights to a root command?

I need to add the command "shutdown" to my .lircrc file so that I can shut down the computer from the remote, but adding sudo requires me to enter the password.


Thanks in advance for any help.

---

### Post by aysiu on 2007-01-02
Can you clarify a bit what you're asking?

Your user already has *sudo* rights, but you don't want to enter a password for that one command?

Or your user doesn't have *sudo* rights, and you want to add *sudo* rights so the user can run commands as root?

---

### Post by Scorpuk on 2007-01-04
I need to do the following:


```
# lircrc for iMON
#
# To check button names on your remote, make sure lircd is running and run irw
# Pressing buttons will show the appropriate button name
#

# Non-program specific
#

# Command bindings

begin
     button = Power
     prog = irexec
     repeat = 0
     config = sudo shutdown -h now
end
```


But irexec will wait for password to be entered.

So any way of by-passing this?

---

### Post by aysiu on 2007-01-04
[This](http://ubuntuforums.org/showpost.php?p=123242&amp;postcount=13) should help. It's for the command /usr/sbin/xfsm-shutdown-helper, but the same principle could apply to any command, really.

---

