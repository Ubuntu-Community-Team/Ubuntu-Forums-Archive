---
title: "Linux startup script"
date: 2008-07-06
forum: General Help
---

### Post by ceclauson on 2008-07-06
Hello!  I'm trying to find out if a linux system has a startup script, i.e. a number of shell commands that are run at startup, similar to a DOS autoexec.bat.

The reason for this is that I just started running Apache and MySQL on my system, and I noticed that when I boot my computer, it starts running these automatically.  I was wondering how
(a) I could change this behavior and/or
(b) change the command line options with which these programs are run.
I thought that this might be happening in a startup script, and this would be the place to look.

Thanks in advance for any enlightenment you can shed on any of these issues!

-Cooper

---

### Post by sdennie on 2008-07-06
The closest thing to autoexec.bat would be /etc/rc.local.  However, for apache and mysql, you can probably turn them off by default with System->Administration->Services.

---

### Post by hoooootz82 on 2008-07-06
This might not be exactly what you want, but you can write your own script and make a link to it with the start up applications in System>Preferences>Session.

---

### Post by ghostdog74 on 2008-07-06
all your startup scripts are in /etc/rc?.d and /etc/init.d

---

### Post by ceclauson on 2008-07-06
Okay, that's definitely helpful.

What I'd like to do eventually, though, is have these services start up automatically, but change the command line options that they're started with.  Is there a text file behind the scenes here on this?

---

### Post by ghostdog74 on 2008-07-06
you can use sysvconfig to configure your startups:
sudo apt-get install sysvconfig

---

### Post by txcrackers on 2008-07-07
The actual start/stop scripts are located in /etc/init.d - you will need to be root to edit these files. You will definitely want to back them up somewhere safe before you start trying to modify them - just in case you muck it up, which *will* happen. (Done it lots of times myself - why do you think I recommend backups? :wink:)

---

