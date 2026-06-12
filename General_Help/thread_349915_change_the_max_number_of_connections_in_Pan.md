---
title: "change the max number of connections in Pan?"
date: 2007-01-30
forum: General Help
---

### Post by dalert0140 on 2007-01-30
I hope someone here can help me avoid running back to windows after I finally managed  to get it off my hard drive. I intstalled Pan newsreader. In windows I used GrabIt It's awesome but I can't find a way to change the Maximum number of connections to something higher than 4. Is there any way to change the settings other than from the GUI? Like from a preference file somewhere or am I stuck with the slow setting? GrabIt let's me select up to 20 connection and I do notice a speedup in downloads.

---

### Post by Theimon on 2007-01-31
I'm curious about this too, I saw this question and started fiddling around with the config.xml but it won't change a thing. However I don't experience any slow downloads. With 4 connections I still get full throttle downloads, which in my case is 8Mbs (=~1MB/s) without any dips or whatever.

---

### Post by dcstar on 2007-01-31
> **dalert0140 said:**
> I hope someone here can help me avoid running back to windows after I finally managed  to get it off my hard drive. I intstalled Pan newsreader. In windows I used GrabIt It's awesome but I can't find a way to change the Maximum number of connections to something higher than 4. Is there any way to change the settings other than from the GUI? Like from a preference file somewhere or am I stuck with the slow setting? GrabIt let's me select up to 20 connection and I do notice a speedup in downloads.

I don't know if the current version of PAN can be changed, but there is a totally new version (apparently) just about ready to be released.

You may want to go the PAN website and download the current beta version and give it a try.

---

### Post by hoppy on 2007-05-11
Hi Folks,

I know I'm a bit late on this. :) 

Pan has a default maximum of 4 connections hard coded as far as I can see. 

You can change the source and recompile if you like. The file you need to change is 'server-ui.cc' and the variable 'DEFAULT_MAX_PER_SERVER' needs to be changed from 4 to whatever you want  (I used 10).

Having more connections does seem to speed things up for me.

Hope that helps.

Hoppy

---

### Post by Theimon on 2007-05-11
You did bump an old thread but it's useful info so I don't mind ;)

I'll try your tip, hope it works. Thanx anyway :)

---

### Post by sgt.splatters on 2008-03-08
> **hoppy said:**
> 
You can change the source and recompile if you like. The file you need to change is 'server-ui.cc' and the variable 'DEFAULT_MAX_PER_SERVER' needs to be changed from 4 to whatever you want  (I used 10).


Although I am sure this way works, it may be a little troublesome for the newbies like me enjoying their first cup of Ubuntu. The easiest way as far as I can tell is this:

In terminal:
sudo gedit /home/*username*/.pan2/servers.xml

In <connection-limit>4</connection-limit> enter the number of desired connections and save.

Make sure Pan is not open whilst editing. When you start up Pan next, you should notice a significant increase in download speed.

---

### Post by s332ur3 on 2008-06-06
> **sgt.splatters said:**
> Although I am sure this way works, it may be a little troublesome for the newbies like me enjoying their first cup of Ubuntu. The easiest way as far as I can tell is this:

In terminal:
sudo gedit /home/*username*/.pan2/servers.xml

In <connection-limit>4</connection-limit> enter the number of desired connections and save.

Make sure Pan is not open whilst editing. When you start up Pan next, you should notice a significant increase in download speed.



it worked for me, sorry i know it's a bit of an old thread, but i am new to linux/ubuntu.   any way thanks for the tip

---

