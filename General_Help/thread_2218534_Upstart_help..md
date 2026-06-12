---
title: "Upstart help."
date: 2014-04-21
forum: General Help
---

### Post by vixsandlee on 2014-04-21
Hiya.


I am trying to work out how to run two commands on an upstart script, I currently use this to start xbmc

```

# xbmc-upstart
# starts XBMC on startup by using xinit.
# by default runs as xbmc, to change edit below.
env USER=xbmc


description     "XBMC-barebones-upstart-script"
author          "Matt Filetto"


start on (filesystem and stopped udevtrigger)
stop on runlevel [016]


# tell upstart to respawn the process if abnormal exit
respawn


script
  exec su -c "xinit /usr/bin/xbmc --standalone -- -bs -nocursor :0" $USER
end script

```


this works fine.

I want to run a second command once xbmc is running, it is called "projoff" and is in /usr/bin/.

How can I run this second command once xbmc has started, I tried adding && /usr/bin/projoff, but obviously that didnt work, I tried adding "exec su -c "/usr/bin/projoff" $USER" after the first command, but that didnt work.

any hints and advice would be great.


Thanks in advance.

---

### Post by ian-weisser on 2014-04-21
You add a second upstart job.
[FONT=arial]
Look at making the second job a [session job]("http://upstart.ubuntu.com/cookbook/#session-job") (not a system job), and placed in either $HOME/.config/upstart/ [/FONT](for specific users) or /usr/share/upstart/sessions/ (for all login users). This may avoid the need for su and $USER. 

The start condition should be: Start on xmbc

---

### Post by vixsandlee on 2014-04-22
Thank you, I am going to have a play later and try and work this out.

---

