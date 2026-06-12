---
title: "x11vnc change port"
date: 2008-06-03
forum: General Help
---

### Post by DexterLB on 2008-06-03
the default port for x11vnc is 5901, but I want to change it to 5566. On the normal VNC this is done by editing /etc/xinetd.d/Xvnc, but how can I do it for x11vnc?

---

### Post by krunge on 2008-06-03
> **DexterLB said:**
> the default port for x11vnc is 5901, but I want to change it to 5566. On the normal VNC this is done by editing /etc/xinetd.d/Xvnc, but how can I do it for x11vnc?

I'm not sure what script is starting x11vnc for you (please post here the file location when you learn it), but once you find it (perhaps grep -rl x11vnc /usr /etc) it would be something like:

```
x11vnc -rfbport 5566 ...
```

---

### Post by DexterLB on 2008-06-04
IT WORKS!!!! Thanks a lot

P. S. How can I mark the thread as solved?

---

### Post by krunge on 2008-06-04
> **DexterLB said:**
> IT WORKS!!!! Thanks a lot


What is the full path of the file you had to modify?

---

### Post by DexterLB on 2008-06-05
I made a shellscript with the following content:
```
#!/bin/sh
x11vnc -many -rfbauth ~/.vnc/passwd -rfbport 5566
``` and I use it to run x11vnc

---

### Post by faustism on 2009-04-08
Does that work with ports below 5900? I tried it with port 80 and it didn't work.

---

### Post by krunge on 2009-04-09
> **faustism said:**
> Does that work with ports below 5900? I tried it with port 80 and it didn't work.

You have to be root/sudo to listen on ports less than 1024.  Did you run it as an ordinary user?

---

### Post by faustism on 2009-04-09
No. I didn't. thank you. that worked. but i have to put "-5820" as the port when i try to connect to port 80.

---

### Post by krunge on 2009-04-09
> **faustism said:**
> but i have to put "-5820" as the port when i try to connect to port 80.

You mean in the viewer, right?  Some vncviewers (e.g. tightvnc, ssvnc) support the double colon notation: ```
vncviewer hostname::80
```

---

### Post by Loan_Refi on 2009-04-10
Hi i have a machine at the office that I SSH into with Putty & x11vnc. Using x11vnc through terminal like this;

ssh -t -L 5900:localhost:5900 "WANIPxx.xx.xx.xx" 'x11vnc -localhost -display :1'

I changed the SSH port from 22 to 3022 for security purposes and my SSH works fine but x11vnc fails, it just won't connect and I already corrected the appropriate ports on my firewall.

Do you know where I need to change the port for x11vnc to work like before the port change?

Thanks!

---

### Post by soltanis on 2009-04-10
Arg arg arg I hate SSH tunnels

It might be as simple as turning X forwarding on though, option -X I think.

---

### Post by Loan_Refi on 2009-04-10
I found out what I need to do.  My reason for changing the port 22 to 22000 or 3022 or whatever you want it to be is for security reasons.

I tunnel SSH to use x11vnc and work remotely

All I have to do is add "-p PORT#" where port# is your port you change it to e.g. 22000 3022 or whatever port number you choose.

My set up is this;

Remote machine is running x11vncserver

I could have a user loged in or not it works either way.

A)
I tunnel thru SSH for secure connection like this;
ssh -t -L 5900:localhost:5900 -p 3022 WANIPXX.XX.XX.XX 'x11vnc -localhost -display :1'
B)
vncviewer -encodings "copyrect tight zrle hextile" localhost:0
:guitar:
Thanks!

---

### Post by krunge on 2009-04-10
> **Loan_Refi said:**
> 
I tunnel thru SSH for secure connection like this;
ssh -t -L 5900:localhost:5900 -p 3022 WANIPXX.XX.XX.XX 'x11vnc -localhost -display :1'


Yes, that's good, the -p option is needed to tell ssh which port to try to connect to.

Note that if you are doing router port redirections to an internal machine you **Only** need to redirect port 3022.

I have seen people trying this also redirect  port 5900 in addition to 3022.  I'm not claiming you did this, just mentioning it for others.  People who also redirect port 5900 have completely missed the point of what the ssh -L redirection is, and have lowered their security greatly (since anyone on the internet can now connect to the VNC server instead of only people who can ssh into the machine.)

Also, you might want to put '-rfbport 5900' on x11vnc's cmdline. By default x11vnc will autoprobe starting at port 5900 until it finds a free port. It prints out the port number it found.  E.g. if you accidentally have some other VNC server (say vino) on port 5900 then x11vnc will choose 5901. This causes confusion in troubleshooting problems. With the '-rfbport 5900' option x11vnc will exit immediately if it cannot get port 5900 and so hopefully that there is a problem will be more obvious.

---

### Post by faustism on 2009-04-10
yes, i was talking about the viewer. I had to put in "-5820" to connect to port 80. are you saying that i could use "::80"? i am using vinagre by the way.

---

### Post by krunge on 2009-04-10
> **faustism said:**
> yes, i was talking about the viewer. I had to put in "-5820" to connect to port 80. are you saying that i could use "::80"? i am using vinagre by the way.

I've never used vinagre. Tightvncviewer and ssvnc support ::80. Why don't you try it, and similar things, with vinagre, and check the vinagre documentation, then report back here what you find.

---

### Post by faustism on 2009-04-11
yes that does work in vinagre thanx

---

