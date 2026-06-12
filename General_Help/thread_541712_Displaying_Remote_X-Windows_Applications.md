---
title: "Displaying Remote X-Windows Applications"
date: 2007-09-03
forum: General Help
---

### Post by jonnymccullagh on 2007-09-03
I need to run an XWindows program from a server to my local desktop but using Ubuntu I am getting stuck. My colleagues are successfully doing it with Slackware.
I read [another post]("http://ubuntuforums.org/showthread.php?t=38497") which told me to set 

DisallowTCP=false
in
/etc/X11/gdm/gdm.conf 

which I did and added a rule to Firestarter for XWindows to allow access to ports 6000-6015. I did an nmap from another machine on the network which shows:
6000/tcp closed X11
6001/tcp closed X11:1
6002/tcp closed X11:2 ... etc

When I try running the X application on the server I get:
Error: Can't open display: thehostname:0

I get the feeling that X isn't listening on ports 6000+ ? Can anyone help me with that?
I have also checked /etc/ssh/sshd_config on the server and "X11Forwarding yes" is set,
Thanks inadvance,
jonny

---

### Post by aJayRoo on 2007-09-03
When I use X applications from a remote server all I have to do is include the '-X' option when I ssh into the machine:
```
ssh -X username@machine.ac.uk
```
I just wanted to make sure you were passing that option?

---

### Post by jonnymccullagh on 2007-09-03
Perfect, thankyou.
I had obviously misunderstood the previous posts I had read.
In my initial connection to the server specifying the -X option in the ssh command sorted me out.
Thanks again,
jonny

---

