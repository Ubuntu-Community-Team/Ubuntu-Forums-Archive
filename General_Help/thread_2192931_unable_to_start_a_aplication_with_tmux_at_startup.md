---
title: "unable to start a aplication with tmux at startup"
date: 2013-12-10
forum: General Help
---

### Post by davidtuti2 on 2013-12-10
I'm trying to start an application (newsbeuter) at boot but I can't. I'm tyring with:


```
tmux new-session -d -s main
tmux new-window -t main:1 '/usr/bin/newsbeuter'
```




Tmux is up but the newsbeuter dont start:


```
ps -ef | grep -i tmux 


root      2118     1  0 16:09 ?        00:00:00 tmux new-session -d -s main 
pi        2245  2211  0 16:09 pts/1    00:00:00 grep --color=auto -i tmux pi@raspberrypi 


ps -ef | grep -i news 


pi        2247  2211  0 16:09 pts/1    00:00:00 grep --color=auto -i news
```


Could you help me please? Many thanks and sorry fo

---

### Post by ian-weisser on 2013-12-12
I don't use Neusbeuter, but I'll take a stab at it...

There are a couple possibilities:
1) Neusbeuter may check to see if it's being run as root, and quit. Do you *really* want to run an rss feed reader as root? That's not a great idea.

2) Newsbeuter may need a DISPLAY environment variable. Most applications do. Root jobs don't get a DISPLAY - they are mostly designed to run headless. User jobs don't get a DISPLAY until after login.

There is a difference between boot and login:
 A job that runs at boot will be running before you login. Those are system-level jobs (cron, networking, logrotate, etc) and are controlled by Upstart.
A job that runs at login runs as your user. It stops when you logout. It's associated with your DISPLAY. Those are controlled by the Startup Applications control panel.

You might simply need to put tmux and Neusbeuter in Startup Applications instead of a boot start.

---

