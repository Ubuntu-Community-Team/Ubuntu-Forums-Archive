---
title: "the vncviewer command options"
date: 2007-08-20
forum: General Help
---

### Post by WetWired on 2007-08-20
I was wondering if it were possible to add some flags or something onto the vncviewer command. The first thing I'd like to add is the ip I'd like it to connect to, and then another for the password, so that when I click on the menu link I've made in fluxbox, it'll just open without me having to do all of that other crap.

---

### Post by fragos on 2007-08-20
in a terminal enter "vncviewer --help"

---

### Post by bodhi.zazen on 2007-08-20
man vncviewer

[http://linux.die.net/man/1/vncviewer](http://linux.die.net/man/1/vncviewer)

Try the -passwd option

Otherwise the "problems" with the password is a little more difficult ...

Take a look at expect

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

