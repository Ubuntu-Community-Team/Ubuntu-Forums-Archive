---
title: "using freenx to remote the native X server?"
date: 2007-01-09
forum: General Help
---

### Post by Houman on 2007-01-09
Hi there;

After many , many... hours I was able to install freenx. Now that I used it for the first time I realized its not doing what i need it to do. It logs me in every time into a new session whereas I want to remote the native X server for the user that is logged in just like VNC does.

This is a problem because I want to for example start a download, then close my freenx and come back home and see that it is finished, but I cant do that with freenx. 

Is there anyways to achieve VNC-like behavior with freeNX? (please don't tell me to go back to using vnc because i spent so much time ](*,) setting up this freenx)

thanks for your help

Houman

---

### Post by Houman on 2007-01-09
Hi there

I found the solution, in order to login into an existing session instead of opening a new one (which is what freeNX does) you should start a VNC server on the remote machine and then use VNC from the freeNX client as the protocal, and choose the vnc server as localhost and screen number as 0, there was a thread about this [here]("http://mail.kde.org/pipermail/freenx-knx/2006-July/003684.html") [kde.org].

regards

Houman

---

