---
title: "Gnome-Terminal Help"
date: 2008-05-13
forum: General Help
---

### Post by Joe Momma on 2008-05-13
I was wondering if anyone could clue me in to the recent changes made to gnome-terminal.

To access HPC machines I need to run the terminal within their custom kerberos shell.  With gnome-terminal 2.18 I did this by launching:

kshell -c gnome-terminal

and everything I did in the new window would be wrapped in the secure kerberos shell including all tabs I opened.  But since the upgrade to 2.22, gnome-terminal launches differently, and the above command no longer inserts the terminal intor the kshell.  I can still run kshell from within the terminal, but I need to reinitialized in every tab I open (note "kshell -c konsole" still wraps an entire konsole window in the kshell).

It's almost like /usr/bin/gnome-terminal is just a launcher for another program.  Say I try to run:

/usr/bin/gnome-terminal &

 a new window pops up and in the first terminal it says:

[1]   Done                    gnome-terminal

immediately, and advances to the next command line, but the new terminal stays open.  I need to find the actual running process that contains the terminal emulator, so I can wrap this in the kerberos shell.  I don't think it can be /usr/bin/gnome-terminal, since that process terminates immediately.

If anyone can help, I would really appreciate it.

Or, lacking that, is there a way I can downgrade to gnome-terminal 2.18 if I am running Hardy?

---

### Post by bingoUV on 2008-05-13
In gnome-terminal, you can choose what command to run in every new tab. It is in preferences. It is the shell , bash by default. In your case, you could choose to run 
```

kshell -c /bin/bash

```

---

### Post by Joe Momma on 2008-05-13
Thank you for your reply, and that does indeed work.  The problem is it only wraps the tab I run it in, and I need to re-authenticate in every tab.  If I can manage to wrap the entire gnome-terminal (like I could with 2.18, and can with konsole), my credentials will be shared between tabs.

---

### Post by Joe Momma on 2008-05-15
does anyone know how I can downgrade to 2.18.2? it's not in the repos I don't think

---

### Post by Joe Momma on 2008-06-05
bump

---

### Post by bingoUV on 2008-06-05
try finding it in packages.ubuntu.com. 

If you know the exact version, apt-get might work
```

apt-get --install gnome-terminal=2.18.2

```

Generally exact versions are not simply 2.18.2, but something like 2.18.2.7.8-ubuntu3

---

