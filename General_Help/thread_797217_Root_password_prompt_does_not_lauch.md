---
title: "Root password prompt does not lauch"
date: 2008-05-17
forum: General Help
---

### Post by Dotakon on 2008-05-17
Hello, 
I have upgraded to ubuntu 8.04 two week ago, and I am not able to launch any root privilege program because the root password prompt does not launch (looks like it is launching, but it never does).
I have been looking in different forums for a bug or a solution, bu nothing.
I would appreciate any idea.
Thanks,
Dotakon

---

### Post by ramjet_1953 on 2008-05-17
Do you mean that when you prefix a command by using [COLOR="Blue"]sudo[/COLOR], nothing happens?

Under Ubuntu the root password is locked and temporary root access is granted through the [COLOR="Blue"]sudo[/COLOR] command.

This provides a much safer OS.

In case you don't know sudo means super user do.

Regards,
Roger :cool:

---

### Post by aysiu on 2008-05-17
Paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gksudo synaptic
``` If there are any error messages, please paste those back here.

---

### Post by prshah on 2008-05-17
> **Dotakon said:**
> Hello, 
I have upgraded to ubuntu 8.04 two week ago, and I am not able to launch any root privilege program because the root password prompt does not launch (looks like it is launching, but it never does).

Looks like the common broken sudo problem. To confirm, Open a terminal (Applications-Accessories-Terminal) and give the command 
```
sudo
```, you should get an error "Cannot resolve hostname". If you get this, it's easy to fix! Continuing in the terminal:

```
hostname
```

Note the name shown.

Then ```
gksu
```, and in the box that opens up, give the command as ```
gedit /etc/hosts
``` and the user as root. Find the line with "127.0.0.1". The name following that number series should be EXACTLY the same as the hostname above. If it isn't change it, save, and quit. Note that you should have 2 entries for 127.0.0.1; one should have localhost, and the other should be exactly the same as the hostname command above.

sudo should start working immediately.

---

