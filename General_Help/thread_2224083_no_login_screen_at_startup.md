---
title: "no login screen at startup"
date: 2014-05-14
forum: General Help
---

### Post by s9032g@comcast.net on 2014-05-14
Apparently I did something (if I knew what, then I would undo it) that caused me to lose the login screen at startup. I would prefer to have it function. How can I get it back?

I see some very complex suggestions on line. I prefer the simple solutions if possible (Occam's Razor).

Thanks

I have Ubuntu Tweak and Gnome Tweak. Running 14.04

---

### Post by HiImTye on 2014-05-14
what *do* you see at startup?

---

### Post by s9032g@comcast.net on 2014-05-14
Dell Logo
Grub menu (might be useful sometime. lasts 4 seconds)
A couple of quick flash bys of no significance
Then straight to the desktop (THE LOGIN SCREEN USED TO POP UP BEFORE THE DESKTOP CAME UP)
 
Then I can go into Chromium, or whatever, but, before I can do anything, for example a Google inquiry, it askes for my password

---

### Post by HiImTye on 2014-05-14
ok, so it's just lightdm, or gdm, or whatever running it's default session. do the opposite of the instructions here:
[http://askubuntu.com/questions/456766/how-to-set-default-session-in-ubuntu-14-04-lts](http://askubuntu.com/questions/456766/how-to-set-default-session-in-ubuntu-14-04-lts)

---

### Post by s9032g@comcast.net on 2014-05-15
Sorry but I am not adept enough to know how to do the OPPOSITE of this:

sudo nano /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf

and change line user-session to what session you want with session name as mentioned in /usr/share/xsessions/ with

ls /usr/share/xsessions/

---

### Post by HiImTye on 2014-05-15
in other words, set it to empty, so that there is no session name after user-session= or whatever format they use

---

### Post by s9032g@comcast.net on 2014-05-16
[SeatDefaults]
user-session=ubuntu
 The above what I get. I cannot change it. It just sits there and when I try to end the terminal session it says that something is "still running". Just goes on and on with nothing happening.

---

### Post by s9032g@comcast.net on 2014-05-18
I decided, after using Ubuntu since release 8.04, that Ubuntu had grown to be too bulky for my small travel laptop. I have switched to LBUNTU. We'll see how that goes.

---

