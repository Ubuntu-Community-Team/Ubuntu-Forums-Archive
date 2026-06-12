---
title: "making a program run on startup do i need to be root?"
date: 2008-02-06
forum: General Help
---

### Post by Cew27 on 2008-02-06
hi i have some applets installed for my keyboard and i have one running on startup already
i did this by compiling the program (this put the executable in /usr/sbin
i then edited the sessions so that the command was sudo /usr/sbin/g15daemon i also have one on root without the sudo at the beginning
the other applets i tried to make work on startup wasn't successfully i compiled the program, this time the executable was put into the desktop folder from where i compiled so i copied it to usr/sbin and set it to boot as sudo /usr/sbin/g15stats but this isnt sucessfull
do i need to create one for root as /usr/sbin/g15daemon aswell as having one in my account as sudo /usr/sbin/g15daemon??

---

### Post by pointone on 2008-02-06
Either create a startup script in /etc/init.d or edit /etc/rc.local. See:

```
man update-rc.d
```

... for details on init.d. 

rc.local is easier, though. Just run your program right before the end, as in:

```
/usr/sbin/g15daemon
exit 0
```

Using sudo won't work unless it's from the command line. You want gksudo if running it from your "session"; but using rc.local or init.d is even better (more correct).

---

### Post by nemilar on 2008-02-06
Just add it to /etc/rc.local as described above (before the exit command), and it will run at startup, and be executed as root.

---

### Post by Cew27 on 2008-02-07
that didn't work either 
i have set it so it starts when i log in as root and it works under the command /usr/sbin/g15stats however the command on my account is names the same g15stats will this effect it in any way

---

