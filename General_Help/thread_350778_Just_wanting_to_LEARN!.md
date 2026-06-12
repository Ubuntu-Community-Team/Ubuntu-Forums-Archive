---
title: "Just wanting to LEARN!"
date: 2007-02-01
forum: General Help
---

### Post by hollipharm on 2007-02-01
Just wanting to know if anyone had any suggestions on some basic steps for using terminal services (various commands, etc.) that would be good practice fro myself and possibly others.  I am new to this whole linux thing (been brain washed by microsoft for most of my life and feel like it is time to break the chains).  Any suggestions would be much appreciated! thanks

---

### Post by 3rdalbum on 2007-02-01
> **hollipharm said:**
> Just wanting to know if anyone had any suggestions on some basic steps for using terminal services (various commands, etc.) that would be good practice fro myself and possibly others.  I am new to this whole linux thing (been brain washed by microsoft for most of my life and feel like it is time to break the chains).  Any suggestions would be much appreciated! thanks

How much terminal do you already know?

[http://www.linuxcommand.org](http://www.linuxcommand.org) is a good guide, but if you already know the basic commands you might not get so much out of it. If you really want to learn the power features, try looking in the manuals for *top*, *at*, and *kill*.

Top lets you view what programs are using the most CPU. At lets you schedule commands relative to the current time. Kill gives you a lot of control over shutting down misbehaving programs.

Some other useful ones:

ps aux | grep "[/i]something[/i]" - where *something* is the name or process number of a program. Then you can see if a particular program is running.

fuser -k *filepath* - where *filepath* is the path to a file that is "busy" and you can't figure out which program is using it. This kills the program - get rid of the *-k* bit to merely have it list the process number of the program (and you can then find its name through *ps aux | grep "whatever"*).

The best thing is, Ubuntu installs manuals for all the programs, so you can just look at the "man pages" if you get stuck. For instance, type *man fuser* to learn about the example I gave above.

---

### Post by evilc on 2007-02-01
Here's a few for you to see in terminal. Have fun learning :D

---

### Post by reclusivemonkey on 2007-02-01
> **hollipharm said:**
> Just wanting to know if anyone had any suggestions on some basic steps for using terminal services (various commands, etc.) that would be good practice fro myself and possibly others.

Are you wanting to know more about the commands themselves or actually scripting things? I find RUTE very useful for the former;

[http://rute.2038bug.com/](http://rute.2038bug.com/)

and this is a great guide for the latter;

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

In paper form, "Linux in a Nutshell" by O'Reilly is a joy to read/refer to;

[http://www.amazon.co.uk/s/203-1163832-0213515?ie=UTF8&tag=mycroft16-21&index=blended&link%5Fcode=qs&field-keywords=linux%20in%20a%20nutshell](http://www.amazon.co.uk/s/203-1163832-0213515?ie=UTF8&tag=mycroft16-21&index=blended&link%5Fcode=qs&field-keywords=linux%20in%20a%20nutshell)

Of course by far the best way is to get stuck in and do. Remember, for everything you do in a GUI, there is a command line equivalent. To start off, just think "Can I do this at the CLI?"

Things you might want to start with are;

1. A backup script
2. A talking clock script
3. A reminder system

Good luck and enjoy!

---

### Post by hollipharm on 2007-02-01
Thanks for all the suggestions.  I will try them all and keep the suggestions coming if you guys think of any more!

---

