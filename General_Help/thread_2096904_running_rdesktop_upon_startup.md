---
title: "running rdesktop upon startup"
date: 2012-12-21
forum: General Help
---

### Post by choppyfireballs on 2012-12-21
I currently am using ubuntu 12.04 as a thin client on a users machine. I have a script on her desktop that connects her to a virtual machine, however I need this script to run automatically at startup. The catch here is that I did an ubuntu minimal install and then installed unity onto it, and I don't have the startup applications program or if i do, I cannot browse to it through the unity bar. So I was wondering if there was a way to run it when she logs in to connect her to the VM without using the startup applications program. 

She is running a minimal install with unity on it due to hardware requirements. so reinstalling with Ubuntu isn't quite an option.

---

### Post by Rexilion on 2012-12-21
I don't use Unity, so 'startup applications program' is kind of vague to me. I'm assuming you don't have the program to create the autostartup. That is why I give you the procedure to do create this yourself.

And then I assume that you do have the tools to add this program to the start procedure of your session.

Btw, if you want to go lightweight, why not go with Xubuntu?

You could try this:

[QUOTE=~/.local/share/applications/rdesktop_start.desktop][Desktop Entry]
Name=Rdesktop
Terminal=false
Type=Application
Exec=sh -c '~/rdesktop.sh'
Icon=/usr/share/pixmaps/gksu.png[/QUOTE]

And then add it through the autostart application.

---

### Post by choppyfireballs on 2012-12-21
I have that currently set up, i just don't have access to the startup applications app to add it to startup. I think what I am going to try is changing the runlevel to 1 so that no gui starts up then testing it using xwindow and and rc.local entry.

---

### Post by lykwydchykyn on 2012-12-21
Question: do you want this system to actually have unity available for local features, or do you just want this thing to run rdesktop seamlessly like a regular thin-client (where all you see is the remote desktop window)?

If you want the latter, check out this article I wrote on kiosks; the same principle can be used to run other programs (such as an rdesktop script) and give a user any kind of Xsession you want.

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

---

### Post by Rexilion on 2012-12-22
Yes, if you want what lykwydchykyn is mentioning, then this is all you should do:

Put the below snippet in /etc/rc.local

> su - -- USERNAME -l -c '/usr/bin/startx </dev/null >/dev/null 2>&1' &

Move your script to:

~/.xsession

```
chmod 755 ~/.xsession
```

Now, when you boot the computer. An X-session will start under user USERNAME and will run your script. If your script ends, X will terminate. You could make the box shutdown after that.

Before this works, make sure that in the file /etc/X11/Xwrapper.config, you make sure that this line is used:

> allowed_users=anybody

---

### Post by choppyfireballs on 2012-12-26
Ok, so I found out why my previous attempts weren't working. When I installed Unity on the client I did not install the Ubuntu-Desktop package so Unity and X were missing some packages needed to do certain things. (Basically I screwed up on the installation.) So I installed Xubuntu, to help with the resources, and have it loading on startup, however it's loading before XFCE and it launches the connection, then closes it, and launches XFCE over it, is there a way to delay the start, I'm using startup applications in XFCE to start the program on startup.

---

### Post by Rexilion on 2012-12-27
You can make it fork into the background by using and '&' sign after the rdesktop command.

But really, you can also use my method. That is just X and rdesktop, and no other DE.

---

### Post by choppyfireballs on 2012-12-31
Well thank you all for all of your help. When I changed the resolution on the clients monitor to the native resolution, everything started up in the right order. Weird right, any way thanks for all of your help.

---

