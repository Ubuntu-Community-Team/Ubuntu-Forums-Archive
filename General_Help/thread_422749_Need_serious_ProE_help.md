---
title: "Need serious Pro/E help"
date: 2007-04-25
forum: General Help
---

### Post by hambone79 on 2007-04-25
I installed Kubuntu 6.10 on a Dell M70 laptop a few weeks ago and then installed Pro/Engineer Wildfire 2.0. I had to install a few extra packages like libmotif3 and csh to get Pro/E working, but it worked flawlessly after I got everything setup. 

I used this setup for the past two weeks without a problem, then all of a sudden Pro/E started acting weird. The application launches very quick and opens model and drawing files very quick, but for some reason pan/zoom/rotate has become agonizingly slow. I really shouldn't say that it is slow, it's more like the input from the mouse is delayed. If I pan/zoom/rotate it takes about 1-2 seconds for the model to actually do what I want.

I'm not sure what I installed or what I upgraded in the past few days to cause this, but I would really like to know what I can do to fix this and get Pro/E functioning properly again.

BTW, upgrading to Feisty didn't help either.

---

### Post by hambone79 on 2007-04-25
Please someone help me!

I don't want to go back to Windows!

---

### Post by hambone79 on 2007-04-25
bump

---

### Post by hambone79 on 2007-04-25
Come on, I can't be the only person with this problem. Someone please help!

---

### Post by hambone79 on 2007-04-26
Ok, here is a little more information about my problem. I ran xev to get my mouse events when I clicked the middle mouse button and this is what was spit out by the program:

```

ButtonPress event, serial 31, synthetic NO, window 0x2c00001,
    root 0xef, subw 0x2c00002, time 1043442, (33,34), root:(1772,58),
    state 0x0, button 2, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x2c00001,
    root 0xef, subw 0x0, time 1043442, (33,34), root:(1772,58),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 512

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 31, synthetic NO, window 0x2c00001,
    root 0xef, subw 0x2c00002, time 1045801, (33,34), root:(1772,58),
    state 0x200, button 2, same_screen YES


```

When I click the the "ButtonPress" starts and nothing happens again until I release the middle mouse button. At that point I get "ButtonRelease". I tried this same test on a Fedora Core 6 machine and I get the "ButtonPress" and "ButtonRelease" events as soon as I click the middle mouse button.

If someone can tell me how to modify this behavior, I think I can get Pro/E working properly agian.

---

### Post by salariua on 2008-03-04
The way my problem was to install the latest driver for ati video card. I have used the [wiki]("http://wiki.cchtml.com/index.php/Ubuntu") to install it and had no problems sice. Before this, proe crashed xserver (got me to login screen) and the whole proe was acting really weird.

Try and see maybe it will fix your problem.

---

### Post by ravichandrra on 2008-07-08
Hi, 

I am also looking to install the ProE for my Ubuntu 8.04 through wine. can you tell me the steps how to install it?

---

