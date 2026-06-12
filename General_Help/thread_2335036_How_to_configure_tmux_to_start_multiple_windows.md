---
title: "How to configure tmux to start multiple windows?"
date: 2016-08-24
forum: General Help
---

### Post by YourSurrogateGod on 2016-08-24
Hi all,

I have a ~/.tmux.conf file.  Whenever I start up tmux, I'd like to have about 8 windows and in the first two I want to have htop and nload running.  I've mucked around with the conf file and cannot for the life of me figure out how to do this!

Does anyone know anything that can help me?

---

### Post by papibe on 2016-08-24
Hi YourSurrogateGod,

This .tmux.conf would create 2 windows:
[LIST]
[*]0: with htop, sensors (temperature), and gpu temp
[*]1: a bash prompt
[/LIST]
```
new-session -s demo -d 'htop'
split-window -v -p 25 -t demo 'watch -n 15 sensors'
split-window -h -t demo 'watch -n 30 nvidia-settings -q gpucoretemp'
new-window
attach-session -t demo
```
To start your tmux session run:
```
tmux attach
```
or simply:
```
tmux a
```
Hope it helps. Let us know how it goes.
Regards.

---

