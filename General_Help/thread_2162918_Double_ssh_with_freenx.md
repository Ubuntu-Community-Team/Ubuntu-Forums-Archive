---
title: "Double ssh with freenx"
date: 2013-07-16
forum: General Help
---

### Post by crysis405 on 2013-07-16
I want to use freenx on my workstation from home. To do this I need to first login into the general servers and then navigate to my workstation from there. So I need to login twice, first to the work server, second to my workstation. How can I do this through freenx?

---

### Post by Lars Noodén on 2013-07-16
I haven't used freenx, but guess that it might work something like vnc.  But there are several ways to pass through a gateway.  If all you need is to forward a port, you could do it something like this:

```

ssh -L 8888:desktop.example.org:8888 gateway.example.org

```

Then to connect, you would connect to port 8888 on the local host.  Obviously, substitute the actual port that freenx uses.

---

### Post by crysis405 on 2013-07-16
I'm new to freenx. Where would you used that command? What about the login credentials?

---

### Post by _0R10N on 2013-07-16
What Lars proposes is that you don't use freenx at all, use plain ssh, instead.

Btw, do you need to execute graphic applications?

---

### Post by Lars Noodén on 2013-07-16
Actually you could go either way.  But as new as you are to freenx, I am newer, having not used it at all.  I have in the past used vnc and based the connection method on that.  It does similar things as freenx, and thus *might* work in a similar manner.  Basically, you make a tunnel using the ssh method above and then point your freenx client at the localhost instead of a remote machine.  The tunnel takes care of the rest.

---

### Post by crysis405 on 2013-07-16
Thank you Lars, it seems your idea will work. The only problem is I'm having trouble figuring out how to create the tunnel with putty. I'm using the method described here: [http://www.cs.wcupa.edu/~rkline/linux/ssh-remote.html](http://www.cs.wcupa.edu/~rkline/linux/ssh-remote.html) When I try opening the second instance of putty and opening the session as localhost I get an error: server unexpectedly closed network connection. I'm not sure what I'm doing wrong.

---

### Post by Lars Noodén on 2013-07-17
Interesting, I hadn't seen PuTTY in the repositories.  I guess I hadn't looked for it on Ubuntu.  

For port forwarding with PuTTY on Ubuntu, you need to enter the the tunnel info (-L) into the right box.  The following page shows where to enter it:

[http://www.electrictoolbox.com/putty-create-ssh-port-tunnel/](http://www.electrictoolbox.com/putty-create-ssh-port-tunnel/)

---

