---
title: "What is tty and pty?"
date: 2008-06-18
forum: General Help
---

### Post by meepok88 on 2008-06-18
When I did a ls /dev/tty*, I noticed that almost hundred of tty1, tty2..ttya1, ttyb6, and ptya1, ptya2 and so on and show up.

What is the the purpose of tty and pty? When I nano them, it show nothing.

Do the system need to have so many tty and pty? If not, can they be remove and how?

Will so many tty and pty files occupy memory spaces? When I did a "free" check, it show almost 550M of memory is being used. For XP, I am able to bring the memory used down to 100M. How do I do it for Ubuntu?

Thanks to any one who can provides some guide.

---

### Post by iaculallad on 2008-06-18
> **meepok88 said:**
> What is the the purpose of tty and pty? When I nano them, it show nothing.

From what I understand, TTY "terminal" is where you have physical access to keyboard/Screen (Physical presence in front of the system). PTY "terminal" is for accessing remote systems virtually.

---

### Post by ibuclaw on 2008-06-18
Leave tty and pty alone! :)

They are important parts of the Linux system.

tty is the controlling terminal.
pty is the pseudo-terminal interface.

You are currently running on a tty, (tty7). Just type in
```
who
``` in the terminal and you'll see it.

In ubuntu, you have 6 tty terminals (7th+ reserved for X screens).

To switch between tty's, press "**Ctrl+Alt+F1**" right through to "**F7**" to see each one.

There is a way that you can disable it, but there really is no use, as it doesn't take up virtually any memory to hold them whatsoever.

If you are having memory problems, can you open up a terminal and type in this command for us.
```
top | head -n10
```
Run it around 3 times and post the output of the command in your next post.

Regards
Iain

---

### Post by fenian on 2008-06-18
tty = teletype ; the first unix terminals were teletyps,remotely controlled typewriters that were connected through serial ports.Thus the address for serial ports on unix machines is /dev/ttyS# (# being the number of the serial port).

pty = pseudo terminal :  Pseudo terminal acts like a pipe between a pair of devices i.e: /dev/ptyp3 and /dev/ttyp3.More info can be found [here.]("http://tldp.org/HOWTO/Text-Terminal-HOWTO-7.html")

as mentioned above they should be left alone.

---

### Post by meepok88 on 2008-06-19
Thank you everyone for sharing.

---

