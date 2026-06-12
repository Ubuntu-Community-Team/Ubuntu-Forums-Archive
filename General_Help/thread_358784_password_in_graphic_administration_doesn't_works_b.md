---
title: "password in graphic administration doesn't works but workds in konsole"
date: 2007-02-11
forum: General Help
---

### Post by bourgi220 on 2007-02-11
Hi everybody,

I have a very strange problem... I have it for a few months but it's the first time i make a post to explain it... I made a lot of searches over the net and found problems farly similar to mine but never exactly the same.

Here is it: when i connect myself in super-user in my console, i put my password and there is no problem...
But when i go to the administration menu (in graphic) and i go, for example, to the network administration, ubuntu ask me my password, i put just the same, and it say to me that it is wrong, it also say that maybe i've a problem with capital letters.... But what it is more strange, it is that some applications works correctly... For example, when i do the same things but i go to synaptic (in graphic), i put my password and there is no problem... Only some applications doesn't work...


This problem overcame after a serious error message at the start of ubuntu. I don't remeber exactly the message but it asked me to re-built something. I'm a newbie and said "yes" "yes" "yes" "yes" when it asked me something....
But in fact i'm not sure these problemes are in relation...

By the way, my version of ubuntu is 6.06 LTS Dapper Drake...


If someone have any idea to solve my problem i would be very happy :)
@+

---

### Post by aysiu on 2007-02-11
I'm not sure if you can do this in Dapper, but press Alt-F2 and type ```
alacarte
``` The menu editor should open up. Then go to System > Administration, and double-click Networking. See if the command for Networking is ```
gksu network-admin
``` If not, that could be your problem. If so, can you post the terminal output of this command? ```
gksu network-admin
``` especially after your password doesn't work?

---

### Post by bourgi220 on 2007-02-12
First of all, thank you for your response.

I checked this and this is the right command. So the problem doesn't come from this...

Any idea?
@+

---

### Post by aysiu on 2007-02-12
Okay. Can you post the output of that command, then? Any error messages from the terminal when you launch that command?

---

