---
title: "Is Automatic login + lock screen possible"
date: 2013-01-05
forum: General Help
---

### Post by nainsurvolte on 2013-01-05
I will eventually put my server in the basement and do remote management  from my desk upstairs. Up to a while ago I needed automatic logon to enable XVnc and I manage to make it work. 

But now I am wondering if it is possible, in addition to automatic logon, to have the screen lock without impacting XVnc. Basic scenario, logon is automatic, but screen is locked at the same time while still being able to access machine through a Vnc client.

Is that possible and if so how?

Thanks,

---

### Post by Rebelli0us on 2013-01-05
I had asked if it's possible to [remotely suspend a machine]("http://ubuntuforums.org/showpost.php?p=11976263&postcount=62"), and the answer was yes. If so, it should also be possible to send a lock-screen command remotely. Though I haven't succeeded in doing that yet.

---

### Post by sudodus on 2013-01-05
Maybe you can try something like autostarting

```
xscreensaver-command -lock
```

But do you really have to log in to the computer? A server can run without anybody logged in, unless you use some special program, that needs a logged in user.

---

### Post by nainsurvolte on 2013-01-05
Thanks, but I am mostly interested in having the screen automatically locked after auto logon, not simply lock the screen remotely.

As the machine will be 3 floors down, I wish to do maintenance on it, reboot it, wait that it restarts and then login with Vnc client. I am actually able to do that, but I wish to have the screen locked. I expect then to connect through Vnc client and have my login screen asking for my user pasword while having Ubuntu already be up and running.

I hope I am clear in my goal...

---

### Post by nainsurvolte on 2013-01-05
> **sudodus said:**
> Maybe you can try something like autostarting

```
xscreensaver-command -lock
```But do you really have to log in to the computer? A server can run without anybody logged in, unless you use some special program, that needs a logged in user.

Maybe, where would that command be issued/located.

I am fairly new to making a server. I am adding up features to this install. It started as a MythTV backend and now I am transfering all of my files to it. I am also in the process of looking at puting up LDAP for all the machines at home (need some education first). 

It is also my only Linux machine. My main computer for now is Win7 and I don't know how I could manage efficiently a Linux server through a Windows machine. Maybe it is possible, but my Linux knowledge does not give me this confidence, and I am a visual type of person.

---

### Post by Rebelli0us on 2013-01-05
Since you said that you manage the machine remotely, then a remote command seemed most appropriate.  Otherwise you can just set the power-manager to automatically lock the screen after some period of inactivity.

---

### Post by nainsurvolte on 2013-01-05
Got it to work.

Went into Session and startup and added the xscreensaver command suggested by sudodus to the Application Autostartup. The command is as listed in the thread, no more no less.

@Rebelli0us, I sure manage it remotely, but sometimes I do update, reboot and just leave it on its own. Sometimes, power just go down a bit, machine reboots and I am not there. My goal was really to have something that resume automatically with my MythTv and my VNC running, waiting for my next visit, but locked, The above did the trick.

---

### Post by sudodus on 2013-01-06
I'm glad it works for you :-)

---

