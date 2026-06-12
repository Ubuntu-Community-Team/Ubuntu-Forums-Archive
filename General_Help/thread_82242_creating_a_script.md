---
title: "creating a script?"
date: 2005-10-26
forum: General Help
---

### Post by PriceChild on 2005-10-26
Hiya... i'm using eciadsl to connect to the net, and everything works better than on the inferior OS which doesn't deserve to be named here.

Anyway, back to the point, i have to remember/copy+paste 2 commands from a little file i keep handy on my desktop:

```
modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a

/usr/bin/eciadsl-start | tee log.txt
```

However, these also require a "sudo su -" before starting, a standard "sudo" doesn't work.

Is there a way i could put these into a little handy script onto my desktop which i could just double click, enter my password, and be connected to the net?

Thanks for any help....
                                 Pricey

---

### Post by mykey on 2005-10-26
make it a shell script with **#! /bin/bash** as its first line, save it as a file and give it a name - put it in e.g. /usr/local/bin/<scriptname> - make it executable - then make a launcher with the command **gksudo <scriptname>** on your dektop

voila

---

### Post by PriceChild on 2005-10-26
when you say shel script... do you mean a *.sh file?

---

### Post by mykey on 2005-10-26
[QUOTE=PriceChild]when you say shel script... do you mean a *.sh file?[/QUOTE]
you can add the .sh but don't have to - since the commands for starting your connections are executed in a shell (terminal) they make it a shell script

---

### Post by PriceChild on 2005-10-26
```
**Error:**
Failed to run net.sh as user root:
 Child terminated with 1 status
```

---

### Post by mykey on 2005-10-27
make sure the file is executable (sudo chmod +x <path to script>/net.sh) - if it is check its syntax again

---

### Post by fannymites on 2005-10-27
What does the script do?  I use eciadsl but don't need to do anything like that.  Just wondering if I'm missing something.

---

### Post by PriceChild on 2005-10-30
It's just so i can double click a launcher on my desktop to start up the net without having to type in the terminal :)

Lazy :)

---

### Post by SergioA on 2006-04-19
Hi there!

Just found your interesting thread...

[QUOTE=PriceChild]It's just so i can double click a launcher on my desktop to start up the net without having to type in the terminal :)

Lazy :)[/QUOTE]

I'm wondering if it's possible to write a script that can start (eciadsl-start) the ADSL connection if it's down and stop it (eciadsl-stop) if it's already running?

This way you just can put a shortcut on the desktop and double click it at the beginning and at the end of your ADSL session...

Any suggestion is welcome ;-)

Ciao from Italy!

Sergio

---

### Post by PriceChild on 2006-04-19
Would be nice... but still haven't figured it out :)

---

### Post by wheelspin on 2006-04-21
I could be way off base here but how about this:

```
#!/bin/bash

gksu -u root -k -m "Please enter your system password:" "modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a && /usr/bin/eciadsl-start | tee log.txt"
```

or this:

```
#!/bin/bash

gksu -u root -k -m "Please enter your system password:" "sudo -v"
modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a
/usr/bin/eciadsl-start | tee log.txt
```

---

### Post by SergioA on 2006-04-27
Thanks Wheelspin,

I followed your advice but made it simpler...

I just created two new launchers on my desktop, both set to "Run in terminal", one with the command "gksudo eciadsl-start" an the other with "gksudo eciadsl-stop", set type to "application", chose two nice icons et voilà, when I need to connect/disconnect, I just double click on my two new icons :-)

Thanks again and Ciao fro Italy!

Sergio

PS: sloooowly downloading 100 Mb and more of upgrades of my Dapper beta installation...

---

### Post by SergioA on 2006-05-03
Hi there!

The above two launchers work fine: the only strange behavior is that the "gksudo eciadsl-start" one never works at the first launch...

After completing the synch process it hangs, so I hit Ctrl+C, run the "gksudo eciadsl-stop" and then again the "Start" one, this time with success...

---

