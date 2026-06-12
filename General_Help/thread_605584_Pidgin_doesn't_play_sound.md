---
title: "Pidgin doesn't play sound"
date: 2007-11-07
forum: General Help
---

### Post by lord.toan on 2007-11-07
Pidgin isnt' playing sounds.  Period.  I've checked other forums for help on this and I've gotten tips to install bplay and use bplay %s (Didn't help), aplay %s (didn't help) switching sound from ALSA to other modes (didn't help), etc.

I got one that says to go into the terminal and type:

> ./configure --disable-doxygen --enable-cyrus-sasl && make && sudo make install

When I do that, I get:

> -cyrus-sasl && make && sudo make install
sudo: ./configure: command not found 

Maybe I'm in the wrong folder?  It said the Pidgin source folder.  I'm in /usr/lib/pidgin

---

### Post by lord.toan on 2007-11-07
Yep wrong folder. it's installing it now.  Just have to find SASL Library...

---

### Post by lord.toan on 2007-11-07
Anyone know how to fix this?

> checking for sasl_client_init in -lsasl2... no
configure: error: Cyrus SASL library not found

Do I need to download this on the internet somewhere or is there an apt-get or similar command to get it through the terminal?

---

### Post by lord.toan on 2007-11-07
Fixed that.  Did what the guide told me to do.  Sound STILL doesn't work....

Any ideas...?

---

### Post by lord.toan on 2007-11-07
Wow, don't I feel stupid.  Sound was muted for the last few things I tried, that's why it didn't work.  Iunno what happened but it works now. ^^;;

---

### Post by yowshi on 2008-01-13
how about a simple way to make it work for those of us new to linux. plus i dont like installing new **** taking up more space on my hard drive just to get a feature to work thats supposed to work with the programme that is using that feature

---

### Post by rmasci on 2008-03-05
What I did to fix this is:
[LIST=1]
[*]Install sox package, apt-get install sox.
[*]Open pidgin preferences. Under the Sound Tab change 'Method:' from 'Automatic' to 'Command'
[*]Enter in text box '/usr/bin/play %s'
[/LIST]

From there it worked.

---

### Post by D3M0L1$H3® on 2008-03-05
Yes. It always helps to unmute the sounds. On Just about anything, it works so much better than leaving them muted.
I love how you just replied to yourself throughout this whole thread pretty much. 
So much wonderful help came from the forum...
:lolflag:

---

### Post by MultipleSargasms on 2008-03-05
> **D3M0L1$H3® said:**
> Yes. It always helps to unmute the sounds. On Just about anything, it works so much better than leaving them muted.
I love how you just replied to yourself throughout this whole thread pretty much. 
So much wonderful help came from the forum...
:lolflag:

Haha! I was just thinking the same thing. Sometimes it helps to get your thoughts on "paper", I think. Helps you think more clearly. Very blog-like.

---

### Post by kramer65 on 2008-03-14
Hey Guys/Girls,

I have the same problem but with me its not the mute button. What can I try to fix this?

---

### Post by jvh100 on 2008-03-14
yeh I have a problem with sound as well, but my problem is that when I open pidgin up all the sound on my computer is disabled. it doesnt come back on until I reboot =(

---

