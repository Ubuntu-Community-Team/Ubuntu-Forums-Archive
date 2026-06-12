---
title: "Borked lightdm..."
date: 2013-09-22
forum: General Help
---

### Post by waspbr on 2013-09-22
Hi everyone, 

I have made a bit of a mistake using 13.10, but the bug does not seem to be related to the fact that it is pre-release but something I did. 

I was trying to install NX no machine and apparently it does not play well with unity, so I searched around and it sorta recommended that I installed gnome-session-fallback , which I did. 

So this morning I booted my machine I was greeted with something that looked like gmd (might be something else) but it had a bit of gnome shell look. I put my login information and it would not login, it would refresh the screen . I managed to login through the guest session but it open what seems to be a unity desktop on top of a gnome-shell like environment.... 

So, I logged out and pressed alt + F1 to drop to the command line and logged in there, Then I used the command "startx" that lead me to my desktop without unity which I started by opening a terminal window and typed unity& .

Long story short, somehow I need to figure out a way to set lightdm as default... which config file it that contained? I am not too familiar with upstart, but I guess I have some learning to do. 


Thanks in advance

---

### Post by CaptainMark on 2013-09-22
try```
sudo dpkg-reconfigure lightdm
```

---

### Post by waspbr on 2013-09-22
I am not sure if that is what did it, I tried a few things and upon restarting I was greeted by gnome 2.0 - like desktop. (Ah the old days). I then logged out and switched to unity. Apparently the problem is solved. 

I had tried that before, but I thought it didn't work because I was under the impression that it would display a dialog, and no such dialog appeared. 

Thanks for the help.

---

