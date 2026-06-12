---
title: "making a &quot;go to monitor standby&quot; shortcut"
date: 2007-09-15
forum: General Help
---

### Post by DuplexEmotions on 2007-09-15
Hello!

I have an NEC lcd2070wnx monitor, which I love dearly aside from the power button not working properly. I am tired of having to unplug the monitor power whenever I want to turn it off and smacking the power button 50 times whenever I want to turn it back on.

But my question isn't about this hardware (which I'm sending in soon for repairs), but software. I'd like to make a shortcut that flips the monitor to standby mode so I don't have to deal with it when I go to bed. I'd just set the delay to an absurdly low number, but I often leave my monitor on waiting for instant messages and the like.

Any help would really be appreciated! Thanks.

---

### Post by jocko on 2007-09-15
This is one way of doing it:
Make a new file with the following line in it:
```
xset dpms force standby
```
Save it wherever you want it and make it executable (chmod a+x filename)
Make a starter on your desktop or panel that points to that file.

---

### Post by DuplexEmotions on 2007-09-15
that works perfectly. Thanks a bunch!

---

