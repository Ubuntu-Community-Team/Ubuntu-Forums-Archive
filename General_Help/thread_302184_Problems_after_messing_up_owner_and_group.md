---
title: "Problems after messing up owner and group"
date: 2006-11-18
forum: General Help
---

### Post by hanspb on 2006-11-18
Hi, I recently did a fresh install of Edgy (with Gnome) on my desktop machine which had Dapper on it previously. All went well until I accidentally changed the owner and group of everything on the default user to another user. I have changed it back, but now strange things are happening to that default user:

1. Anything that I change like themes, desktop background, panel settings, font size in Gedit and so on is not saved. After reboot everything is back to default.
2. When I try to start Firefox I get a message that Firefox is already running, which it is not.
3. Trying Opera, every time I start is like the first time, with the licence agreement and all that, and also it won't accept the plugin path.

Anyone got any ideas?
](*,) 
Hans Petter

---

### Post by taurus on 2006-11-18
Boot into recovery mode from GRUB menu and at the prompt, change it back with

```
chown -R john:john /home/john
(assuming john is your login name...)
```
Reboot and see if john owns everything in /home/john...

---

### Post by hanspb on 2006-11-18
I already did that, as I said in my first post. All ownerships seem to be fine, but I still have these other problems.

---

### Post by taurus on 2006-11-18
Then what is the output of this command?

```
ls -la /home/john
```

---

### Post by hanspb on 2006-11-18
Well, I thought I had done it right, but I did not do it exactly the way you said, that must be a more powerful way than just do chown and chgrp on everything when logged in as normal. I did it your way, and now everything works!

Thank you ever so much.

:D 
Hans Petter

---

### Post by taurus on 2006-11-18
If you do it by hand, then you have to change every file and every directory and after a while, it would just take way too much time.  However, if you use the "-R", then it will change everything, and I mean everything, in your $HOME directory for you so one little command does a great job!

I just you just found out how powerful that command is, eh!!!  ;)

---

### Post by hanspb on 2006-11-18
What I did first was:
```
sudo chgrp -R hpb /home/hpb/
sudo chown -R hpb /home/hpb/

```
when I was logged in as my self. My user is hpb. It just seems like doing it your way is even more powerful.

:-)

---

