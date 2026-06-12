---
title: "How do I  run  program either as root or to not need root access?"
date: 2008-06-12
forum: General Help
---

### Post by foldor on 2008-06-12
I am currently trying to get a program to run on startup and it needs to be run as root. It is vino-session if it matters. I have managed to get it to run and even as root, but only if I use gksu and it needs the password.

I need this to run on startup and as root automatically so I can vnc into the machine.

Any ideas? I have heard of using visudo, but I have no idea how to work that. If  anyone has any ideas let me know.

---

### Post by ibuclaw on 2008-06-12
If you use Ubuntu/Gnome, then you can include the line to startup your app in the startup scripts, as found in **/etc/gdm/PreSession**

To open it with write access, type in:
```
gksu gedit /etc/gdm/PreSession/Default
```

Then scroll down to the bottom, and before the **exit 0** line, put in the line you would use to start up the program.

ie:
```
/usr/bin/vncviewer &
```
The **&** symbol after the command is essential, it basically prevents any lock-ups or slow-downs in your logging in stage by not waiting for the program to load/exit, but carrying on with the rest of the logging in process.

Also, "**sudo**" is not needed because the script is executed as root. 

Regards
Iain

---

### Post by foldor on 2008-06-12
Hi and thanks for responding.

Unfortunately that did not seem to work for me. I opened up .xsession-errors and it said to me 

"(vino-session:4771): Gtk-WARNING **: This process is currently running setuid o$ This is not a supported use of GTK+. You must create a helper program instead. For further details, see:
       http://www.gtk.org/setuid.html"

And having gone to that site basically it tells me that it thinks what I am doing is a security risk and should not be done.

I guess I should also mention that I am running fluxbox with a GDM login manager that logs me in automatically.

EDIT: I have read somewhere about creating a shell script and placing it in /etc/init.d, and then placing a symbolic link to it in /etc/rc5.d. That didn't work for me and I have no idea how to see any error logs it produced.

---

