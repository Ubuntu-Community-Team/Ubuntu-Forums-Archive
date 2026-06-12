---
title: "Is there a way to keep tmux session after logout in ubuntu 16.10?"
date: 2017-03-18
forum: General Help
---

### Post by Kastagir on 2017-03-18
Today I noticed a problem with tmux. I detached a session from it and logged out. When I logged in the session has dissapeared. Literally.
```
ps xa | grep tmux
tmux list-sessions
```
gave me nothing. I was astonished because for the last 10 years I remember it always worked. Never had any problems til now.

I reached for google. Found this nasty bug report (insane right?):
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825394]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825394")

So I edited **/etc/systemd/logind.conf** and tried options **KillUserProcesses=no** and **KillUserProcesses=0**.
After restarting systemd-logind
```
sudo systemctl restart systemd-logind
```
logout and login the problem still persisted.

Thought maybe it is a tmux problem but dtach also don't preserve sessions after logout.

I dug a little deeper and found out that yakkety systemd package maintainer added **--without-kill-user-processes** flag to configure command line which should resolve problem: [here is the script]("https://anonscm.debian.org/cgit/pkg-systemd/systemd.git/tree/debian/rules"). It didn't.

I run out of ideas.

My goal is simple. I want to run tmux, detach a session, logout, login and attach previous session. The way it worked since the dawn of time.

---

