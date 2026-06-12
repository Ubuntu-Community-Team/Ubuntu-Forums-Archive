---
title: "Startup script as root? (To change compiz niceness)"
date: 2013-06-04
forum: General Help
---

### Post by bluelight0 on 2013-06-04
My problem is simple.

Compiz is horrible on my computer when the niceness is 0.
How ever setting it to a lower value (say -10) makes it run like butter.

I can change it by opening up the system monitor and going through it graphically.

but on reboot/logout niceness goes back to default 0

Is it possible that when I login a script automagicaly sets the priority back?

Or any other methods?

thanks

ubuntu 13.04

---

### Post by ohnonot on 2013-06-04
after login? 
you'd have to setup a rule in /etc/sudoers that allows you (user) to execute this script and probably all commands used therein with root priviliges.
see also:
[http://ubuntuforums.org/showthread.php?t=1559167](http://ubuntuforums.org/showthread.php?t=1559167)
[http://ubuntuforums.org/showthread.php?t=1556333](http://ubuntuforums.org/showthread.php?t=1556333)
if you don't know how to create a startup entry, call back!

---

### Post by bluelight0 on 2013-06-05
thankyou ohnonot.

for future googlers this is how i now have it set up:

/home/USERNAME/scripts/nice.sh (Perrmissions set to read only)
```
renice -15 `pidof compiz`
```

added to end of /etc/sudoers
```
%sudo ALL = NOPASSWD: /home/USERNAME/scripts/nice.sh
```

when ever you want to set the niceness of compiz (search 'startup applications')
```
sudo -n /home/USERNAME/scripts/nice.sh
```

Logout and back in again.
Bam! compiz is nice and responsive.

just as a note:

what this helps with is when there is a heavy task normaly compiz gets shoved to the bottom making the whole interface lag.
Setting the niceness to '-15' means that when compiz needs the cpu it gets it.
I find numbers arround -10 and -15 show noticable results.

general performance should not be affected as compiz drops to 1-2 % CPU usage when your not changing windows.

if there is anything wrong with this setup (security wise/perfomance wise/stability wise) please tell me ;)

---

### Post by ohnonot on 2013-06-05
glad to be of help.

---

