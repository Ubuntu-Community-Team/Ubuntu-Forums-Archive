---
title: "Need Root Password?"
date: 2007-07-07
forum: General Help
---

### Post by Mohammad Ansarin on 2007-07-07
Hi. I need help getting my root password back. I've anything but a photographic memory ;).

---

### Post by aquavitae on 2007-07-07
Why do you have a root password?  In ubuntu you never need to login as root or even use su.  Sudo (which uses your user password) does it all.

---

### Post by smiley2billion on 2007-07-07
To set the root password:

(from terminal)

sudo passwd

It will then prompt you to enter a new password, after that your root now has a password!

---

### Post by Mohammad Ansarin on 2007-07-08
Ok, thanks all, but I need help on executing an SH (?) file using the root user. It's an Nvidia Graphics driver.

---

### Post by bigken on 2007-07-08
to execute a sh file open a terminal cd to where the sh file is and and type 

sh xxxxxxxxxxxx.sh

---

### Post by aquavitae on 2007-07-08
> **Mohammad Ansarin said:**
> Ok, thanks all, but I need help on executing an SH (?) file using the root user. It's an Nvidia Graphics driver.

sudo nvidia..etc..sh

But why do you need to use the shell installer - have you tried the drivers in the repositories?

---

### Post by aysiu on 2007-07-08
Try this:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

