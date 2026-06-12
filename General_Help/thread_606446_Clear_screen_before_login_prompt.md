---
title: "Clear screen before login prompt"
date: 2007-11-07
forum: General Help
---

### Post by chocolatetoothpaste on 2007-11-07
Hey everyone,
  I've searched google and the forum, and it seems no one has been able to answer.  Is there any way to clear the screen right before the login prompt is displayed?  I have a 14" laptop monitor, and it seems like the text gets a little screwed up because of this.  So I want to "clear" before it shows the system name and asks to login.  I put this line in /etc/rc.local:
```

clear > /dev/tty1

```
but this doesn't clear at the proper time.  Can anyone offer some suggestions?

---

### Post by troyer81 on 2007-11-09
Here's a link to describe the whole "login prompt" process (as well as a very in-depth look at many aspects to the Linux system).

[http://www.linuxfromscratch.org/blfs/view/stable/postlfs/logon.html](http://www.linuxfromscratch.org/blfs/view/stable/postlfs/logon.html)

Basically, you need to add the "clear" escape sequence to the /etc/issue file.  In other words issue the following command:

```
clear > /etc/issue
```Note that you only run this once, you don't have to add it to any scripts (as far as I know?)  There's also a whole lot of other cool things you can do to your login prompt, but you'll have to read the link to see how to set those. ;-)

Good luck!

---

