---
title: "Firestarter on bootup??"
date: 2007-02-17
forum: General Help
---

### Post by icehammer on 2007-02-17
I wish to knw how to add Firestarter to my startup so that it starts automatically WITH the GUI.

So, i did:

```
export EDITOR=gedit && sudo visudo
```

and added: 

```
 icehammer ALL= NOPASSWD: /usr/bin/firestarter
```


then, did:
System -> Preferences -> Sessions -> Startup Prg
and entered:

```
sudo firestarter --start-hidden
```




However, when i reboot and come back.. nothing happens.!!! i still have to launch it manually.
occasionally, on launching manually, it would also give this error:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:6057): Gtk-WARNING **: cannot open display
```:  



What to do??
Also, in /usr/bin/firestarter, do i have to give /bin/ OR /sbin/...????

---

### Post by meng on 2007-02-17
First thing to make sure with you is: you do realize that the firewall is active even when firestarter is not running, correct? firestarter is just for modifying firewall settings (and logging activity).

---

### Post by Ramses de Norre on 2007-02-17
I think you just need to run **xhost +** once.

---

### Post by icehammer on 2007-02-17
xhost + says:

```
access control disabled, clients can connect from any host
```


now what?? ya, i know that.. and i need to use firestarter to modify rules and all.. is there anyway to do so??

---

### Post by the.phantom on 2007-02-17
might want to read this post?
[http://www.ubuntuforums.org/showthread.php?t=349050&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=349050&highlight=firestarter)
when you make a change in the firestarter rules it will stay that way till you change it, even if it doesn't show up on your taskbar/desktop
it is just controlling the linux firewall

---

### Post by moore.bryan on 2007-02-17
*i dropped firestarter like a bad-habit once i found ubuntu-firewall ([http://rob.pectol.com/content/view/2/1/]("http://rob.pectol.com/content/view/2/1/%29")), since it gave me so many issues.  might be something to look into...*

---

