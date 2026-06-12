---
title: "how do i run a command at start up?"
date: 2007-09-12
forum: General Help
---

### Post by gorilly on 2007-09-12
how do i run a command at start up?

i want to 

sudo tuncfg
sudo hamachi start

thanks

ubuntu 6.06 server by the way

---

### Post by tszanon on 2007-09-12
> **gorilly said:**
> how do i run a command at start up?

i want to 

sudo tuncfg
sudo hamachi start

thanks

ubuntu 6.06 server by the way
If I recall correctly, just add them to /etc/rc.local and set this file as executable (chmod +x /etc/rc.local). The file will look like this:
```
tunecfg
hamachi start
```

---

### Post by digitalbenji on 2007-09-12
If each time you do this, it will be after you log into Gnome, you can just create a script with those two commands in it, then set it to autorun on login also.

---

### Post by gorilly on 2007-09-12
im running server so no gnome.

i tried as you said

sudo nano /etc/rc.local
chmod +x /etc/rc.local

still nothing :confused:

---

### Post by x-point on 2007-09-12
> **gorilly said:**
> im running server so no gnome.

i tried as you said

sudo nano /etc/rc.local
chmod +x /etc/rc.local

still nothing :confused:

I would like to recommend to put absolute path to your commands into /etc/rc.local instead of relative. You can read how to find that path here: [http://www.linuxscrew.com/2007/08/29/find-out-where-unixlinux-executable-binary-is-located/]("http://www.linuxscrew.com/2007/08/29/find-out-where-unixlinux-executable-binary-is-located/")

---

### Post by tszanon on 2007-09-12
> **x-point said:**
> I would like to recommend to put absolute path to your commands into /etc/rc.local instead of relative. You can read how to find that path here: [http://www.linuxscrew.com/2007/08/29/find-out-where-unixlinux-executable-binary-is-located/]("http://www.linuxscrew.com/2007/08/29/find-out-where-unixlinux-executable-binary-is-located/")
Oh yeah. My bad. You're right. Sorry. :)

---

### Post by jrmontg on 2007-09-12
A way that I run some things at startup is System > Preferences > Sessions

Startup Programs...
I put stuff like skype and gaim in there.

---

### Post by tszanon on 2007-09-12
> **jrmontg said:**
> A way that I run some things at startup is System > Preferences > Sessions

Startup Programs...
I put stuff like skype and gaim in there.
There's nothing wrong with that, but servers usually don't have a graphical interface. So, as it's the case of the OP, unfortunately it can't be done.

---

### Post by eggdeng on 2007-09-12
Think we need a trailing ampersand
```
tuncfg &
hamachi start
```
assuming both are in the system path.

---

