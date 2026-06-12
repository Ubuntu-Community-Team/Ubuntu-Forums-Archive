---
title: "Running commands on login on Ubuntu 13.10 with Xmonad and zsh"
date: 2014-01-15
forum: General Help
---

### Post by davidystephenson on 2014-01-15
[COLOR=#333333][FONT=UbuntuRegular]There are several commands I would like automatically run on startup; remapping keys with xmodmap, opening a terminal and a browser, etc. I'm trying to figure out how to run a set of commands on login without using Gnome (as I use Xmonad) or a .bashrc file (as I use zsh). Any suggestions?[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-01-16
Upstart session jobs: [http://upstart.ubuntu.com/cookbook/#session-job](http://upstart.ubuntu.com/cookbook/#session-job)

---

### Post by davidystephenson on 2014-01-17
I'm not exactly sure how to use these. Could you give me some instructions on how to set up some basic startup commands?

---

### Post by hwttdz on 2014-01-17
There are some pretty simple examples in the link ian-weisser gave: [http://upstart.ubuntu.com/cookbook/#non-graphical-sessions-ubuntu-specific](http://upstart.ubuntu.com/cookbook/#non-graphical-sessions-ubuntu-specific)

It's also worth noting that the "best" place to put these files is not exported by default (I'd classify this as "bug" as things should be working out of the box), see: [http://superuser.com/questions/365847/where-should-the-xdg-config-home-variable-be-defined](http://superuser.com/questions/365847/where-should-the-xdg-config-home-variable-be-defined)

---

### Post by davidystephenson on 2014-01-17
Is this upstart-session application installed by default? Where should these files be placed? These files see to require more than just shell syntax - what syntax do they use?

---

### Post by hwttdz on 2014-01-17
> **davidystephenson said:**
> Is this upstart-session application installed by default?
Upstart is installed by default.

> **davidystephenson said:**
> Where should these files be placed? These files see to require more than just shell syntax - what syntax do they use?
[http://upstart.ubuntu.com/cookbook/#session-job](http://upstart.ubuntu.com/cookbook/#session-job) , but be aware of [http://superuser.com/questions/365847/where-should-the-xdg-config-home-variable-be-defined](http://superuser.com/questions/365847/where-should-the-xdg-config-home-variable-be-defined)

> **davidystephenson said:**
> These files see to require more than just shell syntax - what syntax do they use?
Doc for conf files: [http://upstart.ubuntu.com/cookbook/#configuration](http://upstart.ubuntu.com/cookbook/#configuration)

I also found these examples helpful: [http://ifdeflinux.blogspot.com/2013/04/upstart-user-sessions-in-ubuntu-raring.html](http://ifdeflinux.blogspot.com/2013/04/upstart-user-sessions-in-ubuntu-raring.html) (like the xclock example)

I've never really played with upstart much, but after looking at this, it's really awesome.  Does anyone happen to know of a list of signals that are frequently used?

---

### Post by ian-weisser on 2014-01-17
There's a great discussion of common start-on and stop-on conditions at [http://upstart.ubuntu.com/cookbook/#how-to-establish-a-jobs-start-on-and-stop-on-conditions](http://upstart.ubuntu.com/cookbook/#how-to-establish-a-jobs-start-on-and-stop-on-conditions)

There's a great more-specific list of signals at [http://upstart.ubuntu.com/cookbook/#ubuntu-well-known-events-ubuntu-specific](http://upstart.ubuntu.com/cookbook/#ubuntu-well-known-events-ubuntu-specific)

There is, of course, no universal list of signals since any job can create new signals as needed.

---

