---
title: "Using gksu -u with non-root user to open nautilus"
date: 2007-10-15
forum: General Help
---

### Post by roastbeef on 2007-10-15
I have tried to run 'gksu nautilus' which works without a problem to run nautilus as root.  I have created a new user john (which works fine with logging-in and such), but I cannot seem to open a nautilus window as john using gksu.

So, as me (zberry) I type 'gksu -u john nautilus', and I get in return:

cannot open display: 
Run 'nautilus --help' to see a full list of available command line options.
No protocol specified

Alternatively, I type 'su john' to become john, then type 'nautilus' to open a nautilus window, and I get in return:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: 
Run 'nautilus --help' to see a full list of available command line options.

Researching the Xlib error, all I seem to find is that I need to type 'xhost +localhost' which still doesn't solve my problem.

I'm not sure what to do.  I have both myself and john as part of the 'admin' group, and since I have left my sudoers file untouched john should have administrative rights.

Can anyone point me in the right direction?  Thanks.

---

### Post by roastbeef on 2007-10-15
Damn, I just solved my own problem - Found this: [http://www.linuxquestions.org/questions/linux-software-2/xlib-connection-to-0.0-refused-by-server-331779/](http://www.linuxquestions.org/questions/linux-software-2/xlib-connection-to-0.0-refused-by-server-331779/)

Typing 'sudo xhost local:root' resolved my problem.

---

### Post by FuturePilot on 2007-10-15
Does the new user you created have admin privileges, or are they a desktop user. If they're only a desktop user you won't be able to gain any type of root access from that account.

---

