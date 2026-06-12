---
title: "Display message on remote computer via ssh"
date: 2013-07-18
forum: General Help
---

### Post by Azdour on 2013-07-18
Hi,

We are switching from Ubuntu to Xubuntu 12.04 but one of the scripts that we have written no longer works under Xubuntu.

Under Ubuntu at the terminal I can run the command 'who' and see the display number for each user.  

The script would ssh into the machine and call another script.  The script on the remote computer would get the display number from the who command and use yad to display a message (it exporting the display).

Under Ubuntu this works but running the who command on Xubuntu does not show the display numbers.

I've tried exporting :0. :1 etc... but I have a feeling that XFCE does things differently.

So does anyone know of a solution how can I display a message via ssh on a remote machine, or maybe something else to look at.

---

### Post by Azdour on 2013-07-18
Hi,

I think I have found a solution based on:

[http://unix.stackexchange.com/questions/10121/open-a-window-on-a-remote-x-display-why-cannot-open-display](http://unix.stackexchange.com/questions/10121/open-a-window-on-a-remote-x-display-why-cannot-open-display)

I am using the xfdesktop process to look at its /proc/$pid/environ file for the DISPLAY and XAUTHORITY.  Exporting both of this yad works and displays the message on the remote machine.

Now my question: is the xfdesktop the best process.  I guess it is as the remote computers will all be running Xubuntu and graphically logged in.  Any one have a better suggestion as to which process I should use?

---

### Post by Azdour on 2013-07-19
I'm going mark this thread as solved.

---

