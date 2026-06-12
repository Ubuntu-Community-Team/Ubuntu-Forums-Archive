---
title: "remote nomachine logins starting new session"
date: 2008-01-23
forum: General Help
---

### Post by vik.vaughn on 2008-01-23
I've got FreeNX/nomachine working great. The only problem is, when I login remotely, I'm not seeing my currently logged in session at the house. It looks like it starts up a new session.

So if I opened up firefox on my machine at home, and then logged in remotely with nomachine, I don't see my previously opened firefox session and I cannot open a new session since it is already running.

I am using the same username/password on nomachine as I do when I login locally. What can I do to login to the currently running session that was up when I left the house?

---

### Post by rdoolen on 2008-01-23
Thats what it is suposed to do. 

If you want to use the same sesion from different loacations, they both need to be started from NX. Even then it can be scetchy due to different video settings.

If you want to see your desktop, I would try VNC.

---

### Post by vik.vaughn on 2008-01-23
I didn't want to use VNC due to the insecure nature/slow response times compared to FreeNX
--
So I guess I'll just have to tunnel VNC through SSH and grin and bear it if I want to interact with any of the programs I opened while I was actually sitting at the computer, bummer

---

### Post by francky_51 on 2008-01-25
> **rdoolen said:**
> Thats what it is suposed to do. 

If you want to use the same sesion from different loacations, they both need to be started from NX. Even then it can be scetchy due to different video settings.

If you want to see your desktop, I would try VNC.

Is there really no way to use freeNX like VNC  ? :(

---

### Post by rdoolen on 2008-01-25
Hmmm, I think the NX client will act as a VNC client, but I don't know the details. If it does, I don't imagine it would be different than tunneling and using VNC.

Here is sort of an odd work around. From your desktop, run NX client and start a session. When you leave home, suspend the NX session. When you get to your remote location and run NX client, I think you will see the suspended session. If your video is compatable, you should be able to resume the session. I have done this, but it is flakey at best. I only do this in a pinch, and useually the oposite direction, I start something remotely and want to finish it at home.

By the way, I love NX machine. It does exactly what I want, so good luck finding your solution.

---

### Post by vik.vaughn on 2008-01-27
In the end I used both. VNC tunneled through SSH for anything that HAD to be taken care of from my currently running ubuntu session, and FreeNX for everything else since it is much faster. I wish that FreeNX had the option of "taking over" the currently running session like VNC does, but as previously stated, I'm sure there are some underlying technical limitations that make it much more difficult to implement than it would seem.

---

### Post by daflame on 2008-01-28
> **vik.vaughn said:**
> In the end I used both. VNC tunneled through SSH for anything that HAD to be taken care of from my currently running ubuntu session, and FreeNX for everything else since it is much faster. I wish that FreeNX had the option of "taking over" the currently running session like VNC does, but as previously stated, I'm sure there are some underlying technical limitations that make it much more difficult to implement than it would seem.

I am working on this currently, but it will act like you have opened an NX session and then run VNC full screen on the remote side (on a bare X session).

The current work around is to start an NX session to gain in compression and run VNC on the remote session to log into localhost.  This way all the VNC traffic overhead is negated, and only the NX transfer is sent.

Here is the forum that I set up for FreeNX on Gutsy:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by vik.vaughn on 2008-01-28
Thanks for the link.

---

