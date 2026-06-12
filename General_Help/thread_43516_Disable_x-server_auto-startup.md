---
title: "Disable x-server auto-startup"
date: 2005-06-22
forum: General Help
---

### Post by billiejoex on 2005-06-22
I'd like to start my Ubuntu in consolle mode only, disabling the x-server auto starts up. 
How can I do it?

Thanx a lot

---

### Post by Zeddicus on 2005-06-22
Hiya,

Running:

```
sudo update-rc.d -f gdm remove
```
...will remove all symlinks in /etc/rc#.d/ which point to /etc/init.d/gdm, preventing it from starting at boot.  If you're using kdm, simply substitute that as appropriate.

If you want return it to its previous state,

```
sudo update-rc.d gdm defaults
```
...should do it, I believe. :)

Also, there's a 3rd party runlevel editor called bum, if you'd prefer a gui app for such things:

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by billiejoex on 2005-06-22
Intresting.
Can you explain me a little more about the startup programs procedure?
How ubuntu manage this stuff?
For example: how can I automatically put a script/executable in startup? 
Is there a specific directory where all the process that must be runned at startup are listed?
I took a look at /etc/init.d and /etc/rc*.d. Can you tell me something about them? 

Sorry 4 my noob questions but this is an important part in managing system. ;)
> Also, there's a 3rd party runlevel editor called bum
I'd prefer to manage it manually if it's possible. 

Thanx a lot

---

### Post by Zeddicus on 2005-06-22
As a sidenote before I continue, a quick revision to my earlier suggestion.  Apparently it's preferable to rename /etc/init.d/gdm to /etc/init.d/gdm.DISABLED (or whatever you wish), then run update-rc.d gdm remove (without the f).  The primary difference is that if you choose to re-instate gdm, you can just move /etc/init.d/gdm back, keeping the run order. :)

Seems kinda overly complicated to me, but whatever.

That said, if you ran it as I said, no harm done -- if you wish to get it back to the exact order, all that would be needed would be a re-install of gdm.

[QUOTE=billiejoex]Can you explain me a little more about the startup programs procedure?
How ubuntu manage this stuff?
[/QUOTE]

I can try.  For what it's worth, I've only been using the Ubuntu for a month or so, so I more than welcome anyone to clarify/expand on whatever I say. :)

First off, the all the ini-scripts (anything that you might want to run as a service) are stored in /etc/init.d/.  If you wished to add your own script, that would be the place to put it.

Now, the rc#.d directories correspond to runlevels.  These directories contain numbered symlinks to the scripts in /etc/init.d/.  The numbers determine the order in which the scripts are run.  As I understand it, the letter prefix (K or S) tells whether the runlevel will (K)ill or (S)tart the service.

The update-rc.d program simply updates/removes/adds those symlinks.  If the symlink isn't there, the script in /etc/init.d/ won't be run automatically.  You can still invoke the script, however, by simply using /etc/init.d/scriptname start|restart|stop.

In order to have your own script run at boot, you'd need to add it to /etc/init.d/, then add the symlinks (either manually or through update-rc.d).

> 
Sorry 4 my noob questions but this is an important part in managing system. ;)

Not a problem at all, I'm glad to help in whatever way I can. :)

---

### Post by billiejoex on 2005-06-22
You really helped me out with a clear explanation. Really, really thank you man.
I succesfully created a simply auto-startup script:
```

#!/bin/bash
touch /home/billiejoex/Desktop/Hi

```
...that properly worked out.
I encountered a problem when I created a script running a graphical program.
Like you'll surely know Ubuntu has the peculiarity of permit users to launch GUI programs and deny root to do it. Here's an example:
```

root@ubuntu:~ # firefox

(firefox-bin:10255): Gtk-WARNING **: cannot open display:

```

This problem involves the init too because it try to launch firefox with root privileges. In fact I can start line-command programs only. 
How con I avoid this? 


Greetings

---

### Post by billiejoex on 2005-06-22
PS - Another dumb question: 
I would avoid to use update-rc.d program and create links manually. 
I tried with a:
```

root@ubuntu:/etc/init.d # ln myscript /etc/rc2.d/

```
but it seems different from other links contained in rc2.d directory.

---

### Post by Zeddicus on 2005-06-22
[QUOTE=billiejoex]
I tried with a:
```

root@ubuntu:/etc/init.d # ln myscript /etc/rc2.d/

```
but it seems different from other links contained in rc2.d directory.[/QUOTE]

Well... I believe that that command will create a hard link, whereas all the links in rc.d are symbolic links (that is, ln -s instead of just ln).

Does that answer your question?


Oh, and as for the 'starting graphical apps' thing... that's really not what the init scripts are for.  Could you explain what you want to accomplish in putting firefox in an initscript?

---

### Post by billiejoex on 2005-06-22
Firefox it's just an example. All the graphical programs can't be launched with root privileges, and this could be a problem if I had the necessity to launch one of these. :-\
Anyway, don't worry about it. I'll try to open another thread about this problem.

---

### Post by piripallo on 2007-06-29
To stop local X I usually comment the line
0=Local
 in /etc/gdm/gdm.conf (so I can connect my box from other computer). But this won't work in Gutsy.
Hi

---

