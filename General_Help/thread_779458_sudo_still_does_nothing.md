---
title: "sudo still does nothing"
date: 2008-05-02
forum: General Help
---

### Post by evanct on 2008-05-02
whenever i use sudo - it doesn't matter what i use it with, apt-get, gedit, whatever, nothing happens. no error messages or anything, it just goes back to the prompt. gksudo and gksu don't work either, but they do return this error in an alert box:

"Failed to run [whatever] as user root.

The underlying authorization mechanism(sudo) does not allow you to run this program. Contact the system administrator."

I can go into recovery mode, drop into a shell and sudo will work there.

i edited /etc/hosts that way, as per directed in the "sudo unable to resolve host" bug workaround thread i changed the first two lines to read:
127.0.0.1 localhost
127.0.1.1 evans-computer

this accomplished nothing.

does anyone have any ideas? this bug is really frustrating, it strikes me as odd that they would let this into a final release.

---

### Post by evanct on 2008-05-02
oh and this is hardy upgraded from gutsy.

---

### Post by |{urse on 2008-05-02
Try this,
 
[http://www.mepislovers.org/forums/showthread.php?t=9319&page=2](http://www.mepislovers.org/forums/showthread.php?t=9319&page=2)

its the really long post halfway down

where it initially says to use su substitute 

sudo su     <--- be careful you will be root after you type this and enter your password

where it says leafpad substitute gedit.

Oh and just skip the part where it says to type sux

---

### Post by bodhi.zazen on 2008-05-02
> **evanct said:**
> whenever i use sudo - it doesn't matter what i use it with, apt-get, gedit, whatever, nothing happens. no error messages or anything, it just goes back to the prompt. gksudo and gksu don't work either, but they do return this error in an alert box:

"Failed to run [whatever] as user root.

The underlying authorization mechanism(sudo) does not allow you to run this program. Contact the system administrator."

I can go into recovery mode, drop into a shell and sudo will work there.

i edited /etc/hosts that way, as per directed in the "sudo unable to resolve host" bug workaround thread i changed the first two lines to read:
127.0.0.1 localhost
127.0.1.1 evans-computer

this accomplished nothing.

does anyone have any ideas? this bug is really frustrating, it strikes me as odd that they would let this into a final release.

Please check two things :

1. You have "evans-computer" in /etc/hostname (although I doubt that is the problem).

2. Your user is in the admin group.

If that fails, are you running kubuntu ?

Log out and back in help ? Reboot ?

Run ```
sudo ls
``` in a terminal, any additional clues ?

---

### Post by aysiu on 2008-05-02
You may also want to check out [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by evanct on 2008-05-02
> **bodhi.zazen said:**
> Please check two things :

1. You have "evans-computer" in /etc/hostname (although I doubt that is the problem).

yep, i do.

> 2. Your user is in the admin group.

my user had admin privleges before i upgraded and sudo worked fine, i don't see how that could have changed.

> If that fails, are you running kubuntu ?

no, this is ubuntu 8.04.

> Log out and back in help ? Reboot ?

i've logged in and out and rebooted many many times over the past few days.

> Run ```
sudo ls
``` in a terminal, any additional clues ?

nothing happened.

---

### Post by |{urse on 2008-05-02
Edit

---

### Post by |{urse on 2008-05-02
does gksudo work?
 try 
```
gksudo nautilus
```

let me know what happens.

---

### Post by evanct on 2008-05-02
oh wow, it turns out my user did somehow lose admin privleges during the upgrade. all i had to do was type adduser evan admin in single-user mode.

thanks for the link aysiu.

---

