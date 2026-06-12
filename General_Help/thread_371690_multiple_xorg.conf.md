---
title: "multiple xorg.conf"
date: 2007-02-27
forum: General Help
---

### Post by CuBone on 2007-02-27
I have my system setup so that when I log on to an xgl-session beryl automaticly starts. If I log in to a normal session beryl is not started. 
Since beryl is beta and still buggy it won't work if I have both my mointors i extended desktop mode (its something about resolution limitations i beryl). 

I have two different xorg.conf files one with my montiors i extended mode the other with only one monitor. **The problem is**: How can I get a gnomesession to use one xorg.conf file and an xgl session to use the other? 

First I was thinking of making a script that renames the files so the one to be used this session is the one named xorg.conf. But there must be a better way. Any ideas?

---

### Post by caldevil on 2007-02-27
Well, you can have two different layouts in xorg.conf. the exact how to should be there somewhere on ubuntuforums.

---

### Post by bodhi.zazen on 2007-02-28
Here is a how to for multiple server configurations in 1 xorg.conf :

[http://www.ubuntuforums.org/showthread.php?t=240150](http://www.ubuntuforums.org/showthread.php?t=240150)

---

### Post by CuBone on 2007-02-28
That looks great. Will read it more carefully and try it out. Thank you.

---

