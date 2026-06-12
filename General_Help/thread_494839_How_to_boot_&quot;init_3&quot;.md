---
title: "How to boot &quot;init 3&quot;"
date: 2007-07-07
forum: General Help
---

### Post by satimis on 2007-07-07
Hi folks,

Ubuntu desktop 7.04

At boot, edited the kerenel line adding "init=3".  The PC booted ending at;

/bin/sh: can't access tty job control 
turned off
(initramfs)

Please help.  TIA


B.R.
satimis

---

### Post by jimbob on 2007-07-07
Try taking out the quiet and splash and just put in the number 3 without the "init=".
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by satimis on 2007-07-07
> **jimbob said:**
> Try taking out the quiet and splash and just put in the number 3 without the "init=".
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...
Hi jimbob,


Tks for your advice.

Tried it but failed.

$ cat /boot/grub/menu.lst```

....
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=d9cb5057-ee1d-448b-b635-e24be0deb7a1 ro quiet acpi=force splash
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault

....

```

At boot changed the line as```

kernel          /vmlinuz-2.6.20-16-generic root=UUID=d9cb5057-ee1d-448b-b635-e24be0deb7a1 ro acpi=force 3

```

It booted with text scrolling.  But finally the GUI login page started.


B.R.
satimis

---

### Post by jimbob on 2007-07-07
Exactly what is it that you are trying to do?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by satimis on 2007-07-07
> **jimbob said:**
> Exactly what is it that you are trying to do?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]
Hi jimbob,

I need booting "init 3" to run "Xorg -configure".


satimis

---

### Post by scxtt on 2007-07-07
you should be able to type "init 3" from any runlevel you are in ... and if you just don't need X, typing Ctrl+Alt+F1 should get you a CLI login - and you can kill your X session (running "on" F7) ...

---

### Post by satimis on 2007-07-07
> **scxtt said:**
> you should be able to type "init 3" from any runlevel you are in ...
Hi scxtt,

Yes, I can do that but X-window is still running.  I can't run "Xorg -configure"


satimis

---

### Post by scxtt on 2007-07-07
then kill it ... **ps -ef | grep X** and kill the PID ...

---

### Post by satimis on 2007-07-08
> **scxtt said:**
> then kill it ... **ps -ef | grep X** and kill the PID ...
Hi scxtt,


$ ps -ef | grep X```

root      4809  4806  9 21:06 tty7     00:01:21 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
satimis   6007  5938  0 21:21 pts/0    00:00:00 grep X

```

Which pid shall I run;

$ sudo kill pid 6007/5983/4809/4806
???

Tks.


B.R.
satimis

---

### Post by jimbob on 2007-07-08
Sorry to butt in but I believe you want the first number, 4809
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by satimis on 2007-07-08
Hi jimbob,

> 
.... I believe you want the first number, 4809

Performed following steps;

1)
[Ctrl]+[Alt]+F4
booted to init-3 and login as satimis.

2)
$ ps -ef | grep X```

root      5665  5664  6 23:45 tty7     00:00:18 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
satimis   6004  5938  0 23:50 pts/0    00:00:00 grep X

```

3)
$ sudo kill pid 5665

It killed all but finally started Login page automatically.  X started.


Problem Solved
=========
At boot started "Recovery mode"

# Xorg -configure

It created /root/xorg.conf.new

# mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
# cp -p /root/xorg.conf.new /etc/X11/xorg.conf
# reboot

That is all.


B.R.
satimis

---

### Post by cbbs on 2007-07-08
nm

---

