---
title: "Firefox can't talk to modem"
date: 2007-03-04
forum: General Help
---

### Post by Whiteruby on 2007-03-04
Hello, I've got an unusual problem.
I've used the Network tool (6.06lts) to configure and activate my Lucent Winmodem.
It dials in but Firefox (or anything else) will not load any page (except local ones).
After a while, it disconnects.
I found a modem log that says that the connection timed out.
I've tried pretty much everything over the past few days and still no go.

Does anyone know how to fix this?

Thanks

---

### Post by kevinlyfellow on 2007-03-04
hmm, my first assumption is that its bad drivers... I know that there has been something new happening with their driver development, have you installed the martian drivers or the old lucent ones?  [http://martian.barrelsoutofbond.org/index.html](http://martian.barrelsoutofbond.org/index.html)  

Further, I remember having issues like that on arch, the way I solved it there was to link /etc/ppp/resolv.conf to /etc/resolv.conf in other words
```
ln -s /etc/ppp/resolve.conf /etc/resolv.conf
```

(to see the arch post [http://bbs.archlinux.org/viewtopic.php?id=27755](http://bbs.archlinux.org/viewtopic.php?id=27755))

---

### Post by Whiteruby on 2007-03-04
Thanks. I suppose I could download a driver in XP and move it to Ubuntu with a flash drive.
Now all I've got to do is to work out how to install a driver in Ubuntu....

---

### Post by kevinlyfellow on 2007-03-04
have you tried to do the linking yet?  I'd try that first so you don't need to bother to build the driver

---

### Post by Whiteruby on 2007-03-04
So all I do is to copy that line into a terminal window and hit enter?

OK! Here I go - Exit XP and then Ubuntu!

PS: How come "Terminal" is really the command line? And how come that simple fact is not in any documentation?

---

### Post by kevinlyfellow on 2007-03-05
Well, a terminal is where you use command line.  I guess command line and terminal are used interchangeably sometimes, which is technically wrong.  Also watch out when using other linux environments, because it is sometimes called a console.

Good luck, I think that you can just copy and paste the line.  If it doesn't work telling you the target can't be found, then try it the other way around ;-)

As for documentation on this: Linmodems are often best dealt with on an individual basis.  For whatever reason (probably the fact that much of it is closed source) it acts differently on every computer.  I remember dealing with trying to install it on Red Hat 8 and every set of instructions were completely different (never ended up working, but I was a "newbie" then).  Same with nVidia drivers.  Hopefully the martian project works out and we can have the driver integrated into the kernel.

---

