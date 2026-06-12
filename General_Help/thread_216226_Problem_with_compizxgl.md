---
title: "Problem with compiz/xgl"
date: 2006-07-15
forum: General Help
---

### Post by [knap] on 2006-07-15
Hello, my compiz was working great but after reading [this](http://www.ubuntuforums.org/showthread.php?t=148351&highlight=compiz+rule+nvidia) thread i decided to update it. I added this repositories ```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
``` to my sources.list. 

And then the update manager said that there was new updates, i said ''ok, lets update it'', it updated some packages but said that didn't updated compiz, compiz-gnome and some other two i think. 

I restarted my computer and then logged in again into gnome, called the script ''thefuture'' but everything was black, i could only see the mouse pointer. Called Metacity back and put this in the console ```
sudo apt-get update
sudo apt-get dist-upgrade
```

It updated compiz, compiz-gnome but said that have been kept back libwnck18.

Now it gives me this error

```
luis@Home-PC:~$ thefuture
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
luis@Home-PC:~$ compiz.real: Couldn't load plugin 'libgconf.so'
```

It loads Compiz but it is messed up, i don't have those buttons in the right upper corner to minimize, unmaximize and close windows for example.

If i go to Synaptic and try to update libwnck18 it says 

```
libwnck18:
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed
```

Can you guys help me?
Thanks.

---

### Post by Colonel Kilkenny on 2006-07-15
You need to use the Dapper-updates repository to get the needed version of libpango.
Add "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse" to /etc/apt/sources.list
and sudo aptitude update; sudo aptitude upgrade;

---

