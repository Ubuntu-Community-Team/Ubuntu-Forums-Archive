---
title: "Run a script automatically after log on"
date: 2013-04-14
forum: General Help
---

### Post by meebix on 2013-04-14
Hi All,

I am curious how I would go about running a script after log on with Linux.  I would do something similar in Windows by using the Task Scheduler.

What I'd like to do is automatically start an instance of a Rails Server after I log on, so that I can access Localhost immediately, without having to manually go into the terminal, change directories, and run "rails s".

I'd like to make a script that did that for me.

Can someone point me in the right direction as to how I'd go about setting up something like this?

Thanks!
Meebix

---

### Post by GameX2 on 2013-04-14
Go into the Settings (Well, press the button at the top-right corner), and choose "Startup applications".  You'll be able to select your Shell Script to add.

Notice that putting multiple startup applications will slow down the login.  I encourage you to delay a few applications to make the login faster.  For example, to delay Dropbox startup, you'll put this:
```
bash -c 'sleep 50 & dropbox start -i'
```
This wait 50 seconds.

And to delay a script of 5 seconds:
```
bash -c "sleep 5 & home/gamex/myscript.sh"
```

Delay Firefox of  10 seconds:
```
bash -c "sleep 10 & firefox"
```

You get the idea.
Remember to make your script executable!

---

