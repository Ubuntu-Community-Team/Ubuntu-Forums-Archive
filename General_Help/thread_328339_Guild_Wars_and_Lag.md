---
title: "Guild Wars and Lag"
date: 2006-12-30
forum: General Help
---

### Post by FFfanatic on 2006-12-30
I have Guild Wars working in Wine except it's majorly laggy. I have an ATI Xpress 1100 which is found as a 200M that runs at 1500 fps using glxgears so I'm not sure why it's lagging so bad. I also have run it in XP and it runs perfectly so I don't know where I'm losing the speed. Something I think may be related to this is that Ubuntu isn't recognizing my dual core anymore so that may be causing me to lose performance, is there any way to get it to recognize this/fix my lag. Any help is appreciated.

---

### Post by der_joachim on 2006-12-31
Hmmm... My GW setup works quite well in Wine, even if I have an old Geforce 5600. You said that your second core is not recognized anymore. That means that you are not running the generic kernel, right (or the i686-SMP kernel if you are running Dapper)?

Open up a console and run the following command: *uname -r*. It should say something like this: *2.6.17-10-generic*. This is for Edgy! The Dapper kernel should be something like *2.6.15-i686-SMP* or something, but I run neither Intel nor Dapper, so I am not sure. If your output is something like *2.6.XX.i386* (again: I am not sure!), you are running the wrong kernel. 

If you are running the wrong kernel, and after installing the right one you still have performance issues, you'd better head over to the gaming subforum. In that case your problem is probably wine-related. There is quite a major thread on running GW in wine, so there may  be some answers there.

---

