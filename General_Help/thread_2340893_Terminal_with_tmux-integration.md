---
title: "Terminal with tmux-integration?"
date: 2016-10-23
forum: General Help
---

### Post by nielsk2 on 2016-10-23
Hi,

is there a terminal emulator that isn't just tiling like Terminator or Terminix but also integrates tmux? iTerm2 does that on OS X. My understanding is that it tiles like Terminator or Terminix but uses in the background tmux in the background, thus I can detach it and can attach to the session when I ssh into my box.

---

### Post by deadflowr on 2016-10-23
*Thread moved to **General Help**.* 

Look into the package byobu

---

### Post by 1clue on 2016-10-23
Not sure what you're asking. Why not just use tmux in the terminal?

Frankly I use different tabs for different hosts, and generally there's a tmux in each, and another tmux for my local box. I seriously do not want a terminal app messing with my tmux sessions.

Or maybe I'm missing your point?

---

### Post by nielsk2 on 2016-10-23
ok, byobu is just a configuration layer. I already have my own tmux-config.

What am I asking? The difference between just using tmux and a terminal emulator with tmux-integration would be better looks (like native scrollbars for each window/pane), tiling via mouse and not only via shortcuts, maybe even templates for tiling. Sure some of that I could realize somehow but integration would be nicer.

Here is a demo of iTerm2s tmux-integration:
[https://www.youtube.com/watch?v=m9j1GvZypq0](https://www.youtube.com/watch?v=m9j1GvZypq0)

---

### Post by mathew-boorman-h on 2017-01-18
Terminator is working on Tmux support, and just what you are looking for. 
[https://bugs.launchpad.net/terminator/+bug/1301605](https://bugs.launchpad.net/terminator/+bug/1301605)

---

