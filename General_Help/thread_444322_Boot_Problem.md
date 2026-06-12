---
title: "Boot Problem"
date: 2007-05-15
forum: General Help
---

### Post by coolzgeek on 2007-05-15
When I boot, Ubuntu boots into shell and i have to run gdm manually. I tried editing the inittab config file but it isn't there. I heard of the upstart but i don't know wheres the config file. So where is it?

---

### Post by taurus on 2007-05-15
```
sudo /etc/init.d/gdm start
```

---

### Post by coolzgeek on 2007-05-16
No the problem is I want GDM to start on boot. Not how do i start GDM.

---

### Post by coolzgeek on 2007-05-17
How do i Get GDM to start on boot?Without the inittab file, what is the file i have to edit?

---

### Post by coolzgeek on 2007-05-18
Hey Could some one help?

---

### Post by merlinus on 2007-05-18
I believe you can do this by editing /etc/X11/default-display-manager and make sure it says:

/usr/sbin/gdm

You can do this from a terminal with the command:

gksudo gedit /etc/X11/default-display-manager

hth....

-merlin

---

### Post by coolzgeek on 2007-05-23
no the problem is that my computer does not boot into run level 5. I want it to boot to Level 5

---

### Post by coolzgeek on 2007-05-24
Could anyone help me to get X on boot?

---

### Post by coolzgeek on 2007-05-25
could anyone help?

---

### Post by live4fun on 2007-05-30
Try 
sudo dpkg-reconfigure gdm
it should setup gdm again as the default window manager.
If this doesn't help reinstall gdm.
apt-get remove gdm
apt-get install gdm
Might be not the minimal inversive method but worked for me.
Together with gdm eventually more packages are removed than you want.
Than you can try to get them back by installing
apt-get ubuntu-desktop

Hope this helps.

---

### Post by jonallport on 2007-05-30
> **coolzgeek said:**
> no the problem is that my computer does not boot into run level 5. I want it to boot to Level 5


Ooo, ooo, I know this.  I've told someone else this, but I can't find the post - darn!

Will get back to you.

J :^)

---

### Post by jonallport on 2007-05-31
Right, I'm back.

You can either:

1) Make /etc/inittab with the line 'id:5:initdefault' to set runlevel 5
2) Edit /etc/event.d/rc-default and change the 'fallback' runlevel to 5

You'll see that /etc/event.d/rc-default looks for /etc/inittab and parses for a string 'id:{n}:initdefault' where {n} is the runelevel (number 0-9) and calls telinit to set that runlevel.

I hope that solves it for you.

J :^)

---

