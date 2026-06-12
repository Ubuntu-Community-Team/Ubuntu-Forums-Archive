---
title: "Problems running firestarter"
date: 2007-12-11
forum: General Help
---

### Post by drewcoon on 2007-12-11
When I try and run Firestarter through Applications > Internet > Firestarter, It asks for my password, then the "Starting Firestarter" appears on the applications list for a few seconds, then nothing happens. If I run Firestarter through the terminal, I get:

```

andrew@linxp:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:22920): Gtk-WARNING **: cannot open display:  
andrew@linxp:~$ 

```

I've tried googling around, but I can't find anyone with a similar problem, so I came here. Anyone have any suggestions? Please? :)

also, If I try starting Firestarter via terminal, I get this output,

```

andrew@linxp:~$ sudo firestarter -s
Error spawning shell process: Failed to execute child process "firestarter.sh" (No such file or directory)
Failed to start the firewall
An unknown error occurred.

Please check your network device settings and make sure your
Internet connection is active.
(null)andrew@linxp:~$ 

```

Might the problems be related?

---

### Post by taurus on 2007-12-11
Try 

```
gksudo firestarter
```

p.s.  Which release are you running and how did you install firestarter?

---

### Post by drewcoon on 2007-12-11
I'm running Fiesty, and I got Firestarter with
```

sudo apt-get install firestarter

```

I've tried reinstalling it from synaptic, still have the same problem.

---

### Post by drewcoon on 2007-12-11
Sweet! I google searched the error that I got the second time, and found this tutorial,

[http://ubuntuforums.org/showthread.php?t=187899](http://ubuntuforums.org/showthread.php?t=187899)

I picked up at the "How to have Firestarter start without the root password" part, which is apparently not secure, but at least it works at the moment :)

It's good to have it working, I was pulling my hair out with the other firewalls (lokkit doesn't have enough options, guarddog wasn't working right), Firestarter is at least one that I can understand.

Thanks for the help!

---

### Post by nvteighen on 2007-12-13
> **drewcoon said:**
> Sweet! I google searched the error that I got the second time, and found this tutorial,

[http://ubuntuforums.org/showthread.php?t=187899](http://ubuntuforums.org/showthread.php?t=187899)

I picked up at the "How to have Firestarter start without the root password" part, which is apparently not secure, but at least it works at the moment :)

It's good to have it working, I was pulling my hair out with the other firewalls (lokkit doesn't have enough options, guarddog wasn't working right), Firestarter is at least one that I can understand.

Thanks for the help!
Hey, look at my sig. I've written a little How-to on how to make Firestarter start without root password but in a secure way.

---

