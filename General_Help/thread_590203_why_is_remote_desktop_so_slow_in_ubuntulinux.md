---
title: "why is remote desktop so slow in ubuntu/linux?"
date: 2007-10-24
forum: General Help
---

### Post by xmrkite on 2007-10-24
Hello, i frequently remote in to my windows xp computer at the office using my windows xp laptop. I use the Remote Desktop Connection program included with windows xp. This works great.

I also have a P4 2.8GHZ dell computer upstairs running ubuntu. When i use that remote desktop connection to connect to my computer at the office, it just seems so sluggish.

For example, when i alt-tab to another window, it seems like it takes 5 seconds or so to "draw" that new window. On my windows computer, it seemed like real-time, no delay. From the windows computer, you almost can't tell you're remote connecting into another computer. From the linux computer, it is totally obvious.

This makes me not want to remote in from my linux computer.

Any ideas? Are there better programs to connect to that i just need to install, like is the one that comes with ubuntu no good?

PS. I also notice this when i remote from this same linux computer into another linux computer running vnc, in fact, i have vnc'd using ubuntu's vnc program into numerous computers, and they all have this same sluggish lag. At this point, the windows remote desktop is just killing the linux one as far as usability goes. I don't want to stick with the windows one unless i absolutely have to.

-Thanks

---

### Post by millavro on 2007-12-14
I had the same problem.  If you have a Nvidia Video card, it was Xinerama.  As soon as I disabled that and switched to TwinView is was just like being there.  IF you are running dual screens that might be a fix.

---

### Post by cytg on 2007-12-14
xmrkite -> true that .. as i figure, thats just the way it is ... microsofts remote dekstop cheats as far as i can tell .. it "draws ahead" so to speak .. and its pretty obious that there has to be widget support in the client .. i mean try running a 3d app and it will puke.

---

