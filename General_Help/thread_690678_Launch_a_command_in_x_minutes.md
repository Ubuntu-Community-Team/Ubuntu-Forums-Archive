---
title: "Launch a command in x minutes"
date: 2008-02-07
forum: General Help
---

### Post by Xi0N on 2008-02-07
Hi all.
I need to know how to make my linux box after x minutes.

i.e.: I want to go sleep and i want my amuled to be launched automatically after 1h 30min, of course, only once.
¿How can i launch this kind of delayed commands?

Thanks

---

### Post by kevstar31 on 2008-02-07
sleep *(time in minutes)*m;*(command)*

---

### Post by bodhi.zazen on 2008-02-07
You can either use sleep or at

[http://unixhelp.ed.ac.uk/CGI/man-cgi?at](http://unixhelp.ed.ac.uk/CGI/man-cgi?at)

(sleep xx && command &)

or a cron job

I suggest at

---

### Post by PinkFloyd102489 on 2008-02-07
Try executing a sleep command before your amule. The default value for time period is seconds, so m is specified for minutes. Example:


```

sleep -m 90 && amule whatever &

```

I added an & at the end so that the command will pass into the background and allow you to retain further control of the command line. Use "jobs" to see commands/programs running in the background.


EDIT: Sniped. :-(

---

### Post by bodhi.zazen on 2008-02-07
> **PinkFloyd102489 said:**
> Try executing a sleep command before your amule. The default value for time period is seconds, so m is specified for minutes. Example:


```

sleep -m 90 && amule whatever &

```

I added an & at the end so that the command will pass into the background and allow you to retain further control of the command line. Use "jobs" to see commands/programs running in the background.


EDIT: Sniped. :-(

The parenthesis ( ) are one of several ways of running the entire tamale in the background, in a sub-shell to be exact. It is then independent of the terminal (and will not terminate if the terminal is closed).

---

### Post by tha_FLiP on 2008-03-06
umm.. just a question from someone who's still learning..
If I'd like to make a launcher with a sleep command for my mediaplayer (or any other application for that matter), with a variable for time so I can adjust from time to time, whenever I'm launching this..
how would I make the launcher actually ask for the value for this variable when I execute it..?
hope I managed to express myself clearly enough.. I'm a wee bit sleepy.. really need this script :p

---

### Post by bodhi.zazen on 2008-03-06
You can add :

```
Echo start application in how many minutes ?"
read time

sleep -m $time && application
```

Or, if you prefer a gui, use zenity.

Unfortunately there are no great how-to's on zenity, you will need to man zenity.

EDIT: Found a few links for Zenity :

[http://library.gnome.org/users/zenity/stable/index.html.en](http://library.gnome.org/users/zenity/stable/index.html.en)

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

(liked the last two)

---

### Post by koenn on 2008-03-06
try this : 
```
#!/bin/bash
# delayed execution
#
echo -n "delay in minutes: "
read DELAY
sleep -m $DELAY
mediaplayer   ## add options as needed
```

put it in a file, make it executable, create a launcher that points to it.
when using the launcher, choose 'run in terminal' so you can enter a number at the prompt

--
edit : someone was faster ...

---

### Post by tha_FLiP on 2008-03-07
hey thanks a lot! that's just what I needed :)
Now I'll go find out if it really is as simple as it seems :p
thanks again :)

---

