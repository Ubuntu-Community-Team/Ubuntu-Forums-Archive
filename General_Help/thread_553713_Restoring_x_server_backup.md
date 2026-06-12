---
title: "Restoring x server backup"
date: 2007-09-18
forum: General Help
---

### Post by jose_rizal on 2007-09-18
Hi,

I ran the command for modifying the x server "sudo dpkg-reconfigure xserver-xorg". Unfortunately now after I restart, x server no longer works and the system kicks me out to the terminal.

How do I restore the automatic backup of my x server? Thanks!

---

### Post by por100pre1 on 2007-09-18
First let's see if there is actually a backup:

```
cd /etc/X11
```

```
ls -a
```

look for any file with xorg.conf in its name

and post those results...

You can also use this:

```
locate xorg.conf
```

post the results...

---

### Post by jose_rizal on 2007-09-18
In /etc/x11 there are two files named xorg:

xorg.conf
xorg.conf.20070917210834

So I'm assuming the second one is a backup right?

---

### Post by dcstar on 2007-09-18
> **jose_rizal said:**
> In /etc/x11 there are two files named xorg:

xorg.conf
xorg.conf.20070917210834

So I'm assuming the second one is a backup right?

```

cd /etc/X11
sudo mv xorg.conf xorg.conf.bad
sudo mv xorg.conf.20070917210834 xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by por100pre1 on 2007-09-18
I think that's it:

```
sudo cp /etc/X11/xorg.conf.20070917210834 /etc/X11/xorg.conf
```

EDIT: Never mind, do as the previous poster indicated.

---

### Post by jose_rizal on 2007-09-18
It's working now. Thanks for the quick reply! :guitar:

---

