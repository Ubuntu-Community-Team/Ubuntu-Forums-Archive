---
title: "Blank screen if left for too long"
date: 2007-05-30
forum: General Help
---

### Post by rax_m on 2007-05-30
hi, 

I'm having an issue with my Ubuntu Edgy install at the moment.. 
If I leave my laptop running without doing anything for a few hours and come back, I can't get back to the wm. Basically I just get a blank screen. Trying to get to terminal with Ctrl-Alt-F# doesn't work. In fact the computer almost looks like it's frozen (except for numlock which does turn on/off). 

Some Info:
Toshiba P100-429
128 MB Nvidia 7600 Go
1.5GB Ram

Running XFCE desktop on an Ubuntu install BTW.  Though I'm fairly sure that it does happen in gnome as well.
I'm also running Beryl..  

I see the following in my user.log:

```

May 29 18:57:11 rmistry-laptop gnome-power-manager: (rmistry) DPMS blanking screen because the lid has been closed on ac power
May 29 21:15:59 rmistry-laptop gnome-power-manager: (rmistry) Turning LCD panel back on because laptop lid re-opened
May 29 21:19:48 rmistry-laptop hpiod: 1.6.9 accepting connections at 2208... 
May 29 21:19:55 rmistry-laptop dhcdbd: Started up.

```


Any ideas would help. 

Thanks
Rax

---

### Post by eggdeng on 2007-05-30
Could be a screensaver locking up, if you're running one.

---

### Post by rax_m on 2007-05-30
Thanks for the reply.. 

I am running xscreensaver.. but with a blank screen.

---

### Post by rillip on 2007-05-30
This sounds like return from suspend/hibernate not working.  IIRC, Aiysu, one of the mods, had a heck of a time with this on Edgy, but it worked when he went to Fiesty.  Is this a new issue for your or have you just noticed this?

---

### Post by rax_m on 2007-05-31
Hi 

I have noticed this before... but it's kind of irregular. 
Anyway.. after I rebooted yesterday, I left my computer on the entire night.. and it was fine this morning. 
I looked at the log and noticed that the gnome-power-manager debug msgs did not show up ( I am on Xfce on ubuntu).. 
I don't know how it appeared the other day... unless I was playing and did something stooopid.. 

I think I'm going to observe for a while and take it from there. 

Thanks for the replies

Rax

---

