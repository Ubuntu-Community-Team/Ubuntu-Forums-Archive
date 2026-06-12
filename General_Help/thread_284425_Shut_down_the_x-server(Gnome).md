---
title: "Shut down the x-server(Gnome)"
date: 2006-10-25
forum: General Help
---

### Post by jørgen on 2006-10-25
I am using my old computer as a LAN server for all my music. I am running the normal Ubuntu 6.06 version, not the server version. It's running terrible slow so that i want to shut down Gnome in order to increas the performance. (Will it increas the performance??) I dont want to remove the desktop completly, just close it when I am not using the computer.

How do I close down Gnome so that i only have the terminal?

---

### Post by T.Louis on 2006-10-25
I guess you could edit /etc/inittab and the line where it says "d:5:initdefault:" you could change the number 5 to 3.

That way you load to the prompt next time you restart and log in there. When you need gnome you just write "startx" and when you don't want just shut it down or crash the xserver with CTRL-ALT-BACKSPACE.

---

### Post by bswilson on 2006-10-25
> **jørgen said:**
> How do I close down Gnome so that i only have the terminal?

Easy.  On UNIX systems, a default **runlevel** is defined on the system.  On Ubuntu (desktop flavor), the runlevel is 5, which means multi-user with a GUI environment.  By contrast, the runlevel on Ubuntu server edition is 3, which means multi-user without a GUI interface.

Now if you just kill gnome, the runlevel is going to tell your system to start it right back up again.  So what you want to do is temporarily change to runlevel 3 to operate with no GUI.  Do this:

```
sudo telinit 3
```

Note that doing this will also restart your current session(s).

For more details, refer to **man init**, **man telinit**, **man runlevel**.

---

### Post by jørgen on 2006-10-25
> **T.Louis said:**
> I guess you could edit /etc/inittab and the line where it says "d:5:initdefault:" you could change the number 5 to 3.
BACKSPACE.

I cant see that this actually do anything, when i restart it's just like before, it goes straight into Gnome.


> **bswilson said:**
> 
So what you want to do is temporarily change to runlevel 3 to operate with no GUI.  Do this:

```
sudo telinit 3
```


When i run that command, nothing happends

---

### Post by Ramses de Norre on 2006-10-25
Ubuntu doesn't have the gui and cli runlevels like previous posters mentioned.
But they are easily created, all runlevels are identical (except 1,6 and 0) but you can tweak them.
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
Now you see all runlevels, 2 is the default and you can safely change 2 to 5.
To make gnome not to start on startup you need to uncheck "gdm" on runlevel 2. (The runlevel ubuntu boots into by default)

If you then decide you want to start gnome you can do ```
sudo /etc/init.d/gdm start
```
To stop gnome you log off, go to a tty (ctrl-alt-F1) and execute the same command with "stop" instead of "start".

[This](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf+boot) guide shows you more sysv-rc-tweaks.

---

### Post by jørgen on 2006-10-25
Wihoo! It worked, Thanks!

---

### Post by T.Louis on 2006-10-26
> **Ramses de Norre said:**
> Ubuntu doesn't have the gui and cli runlevels like previous posters mentioned.
But they are easily created, all runlevels are identical (except 1,6 and 0) but you can tweak them.


Ops, thank you for the correcting post!

---

### Post by T.Louis on 2006-10-26
> **jørgen said:**
> I cant see that this actually do anything, when i restart it's just like before, it goes straight into Gnome.

My apologize, its not doable straight away with Ubuntu.

---

