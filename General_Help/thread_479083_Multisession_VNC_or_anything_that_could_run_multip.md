---
title: "Multisession VNC? or anything that could run multiple ie's...?"
date: 2007-06-19
forum: General Help
---

### Post by Elijah on 2007-06-19
Hi, 

I am from a web development company and a lot of the development pc's run Ubuntu. Sad part in web development is having to test in ie's & safari, we have a separate pc for that where we could use VNC and test. 

Problem is that many developers connect at the same time, struggling with the ownership of the mouse cursor :o 

Is there any way we could somehow have each user have a login for the vnc and each would have a separate session so that they won't have to argue on who goes first on using the test pc? Or maybe some other solution aside from VNC?

---

### Post by eldragon on 2007-06-20
why not use wine and install ie in all the pcs?

---

### Post by Elijah on 2007-06-20
we could do that but we won't have ie7, it's a bit tough getting that to work... Safari for windows won't install as well ... Also we might worry about licensing issues.

---

### Post by aDRENOcHROME on 2007-06-20
Just an idea ...

If you run a Windows Server 2003 on the testbed machine, you could connect via 'Remote Desktop' (rdesktop). It should support sessions up to the number of client licenses. The only downside might be the restricted color depth of 16bit via a remote session and the hefty licensing costs. This might also work on an older Windows 2000 Server using the Terminal Services. 

Please take my comments with a grain of salt. I'm far from being an expert in this area.

Edit: You could also run multiple windows sessions in i.e. VMware. This way you could run on cheap XP pro licenses, but will have to throw some RAM at the testbed machine.

cu..aC

---

### Post by atria on 2007-06-20
Basically the steps are: 
1) Enable XDMCP/Remote logins (Administration, Login window)
2) vncserver -query localhost -extension XFIXES

Start as many vnc instances as you want; connect to their respective ports using vncviewer.

I hope that works for you

---

### Post by Elijah on 2007-06-20
Hmm... we only have XP Home edition on that pc, can we use that xdmcp remote logins? (what is that anyway?)

Also that vmware thing... do you mean a Linux server with VMware server and run all the windows from it?

---

### Post by atria on 2007-06-20
Oh dear i'm sorry i misunderstood you. I take it that your development PC runs Windows? If that is so, only Windows server 2003 supports concurrent sessions (and you need a license for more than 2 connections too). There are ways to allow concurrent sessions for windows XP home but that is illegal, so i shan't talk about it here.

My suggestions are:
1) Download the windows server 2003 180-day trial from microsoft.com which allows 2 concurrent remote connections (and do a reinstallation every 180days) or
2) Run IE and Safari on Linux using wine, but that is going to be very complicated.
3) Install VMware on the host test computer and run several instances of Windows, but that is going to be very resource consuming and is not exactly feasible.

Regarding the XDMCP thing, i thought that you were going for method (2). XDMCP allows concurrent remote sessions for linux.

---

### Post by Elijah on 2007-06-21
Many thanks to everyone :) The windows server trial could be a good option until we have a budget ready for more connections.

---

### Post by atria on 2007-06-21
I'm glad that helped :)

---

### Post by Elijah on 2007-06-22
Oh, just a followup question: A friend suggested I should use Windows xp Professional , says it can also do concurrent connections.. is that true?

---

### Post by pickarooney on 2007-06-22
There's a patch for Win XP that allows you to connect from several remote machines simultaneously via RDC. I don't have the link to it on this PC, unfortunately.

Unless [this ](http://sig9.com/articles/concurrent-remote-desktop)helps...

---

### Post by Elijah on 2007-06-27
Many thanks for the link pickarooney, I now have 2 options to choose from. Use win2003 server trial or use the hack to Winxp pro, but I guess that'll still be limited to like 10(?) connected users before I break the license agreement (not sure about this though, can anyone confirm?)

---

