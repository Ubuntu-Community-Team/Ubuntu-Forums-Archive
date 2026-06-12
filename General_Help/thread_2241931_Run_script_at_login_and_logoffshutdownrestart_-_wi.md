---
title: "Run script at login and logoff/shutdown/restart - with encrypted home"
date: 2014-08-29
forum: General Help
---

### Post by dekker-crater on 2014-08-29
I've been doing some research, but haven't found a good/workable solution yet, so I thought I'd give a shout out to all the experts out there...

I have an Ubuntu 14.04 system, with encrypted filesystem and encrypted home directory. 

I have a custom application that I want to be running whenever I login (```
/home/<username>/app.sh start
```), but stopped "kindly" when I logoff, or the system is shutdown or restarted (```
/home/<username>/app.sh stop
```). If the app is killed or the system restarted without shutting down, it causes all sorts of chaos that I'd like to avoid. I am the owner and admin of the machine, but for various reasons, the app must live within the encrypted userspace.

Note that because of the encrypted home direcory, I can not use the rc.d system.

I think I can start the app by adding the appropriate start line to my /home/<username>/.profile

What I can't resolve is where I could put the stop line for logoff, shutdown, or restart.

Any suggestions? Until I figure this out, I'm forced to remember to use the "start" and "stop" icons I placed on my desktop...

---

### Post by ian-weisser on 2014-08-29
> **dekker-crater said:**
> Note that because of the encrypted home direcory, I can not use the rc.d system.

You should be using Upstart or Systemd instead of Sysv (rc.d) anyway.
In Upstart, adding a user-level start-stop just is easy. I believe Systemd also makes it easy.

It's called a *session job* in Upstart: [http://upstart.ubuntu.com/cookbook/#session-job](http://upstart.ubuntu.com/cookbook/#session-job)
Several good examples on that page of how to start/stop a job.

---

