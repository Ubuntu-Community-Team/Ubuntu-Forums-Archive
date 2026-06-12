---
title: "[SOLVED] Remote command line login?"
date: 2008-06-26
forum: General Help
---

### Post by Darkade on 2008-06-26
Hey, I've look around for remote desktops and the best thing I could find was definitely VNC. But I have a couple of doubts about it

1)I need to be loggedin in order to connect to my computer remotely?

2)how can I do to remote login in a command line instead of a desktop? I mean for things that I need to do remotely I don't need a desktop and it's kindda slow since I need to do it over the internet. I'd be glad just with the command line. thanks :lolflag:

---

### Post by justleen on 2008-06-26
1) yes, with VNC you need to be logged on

2) ssh will allow you to have a full remote console..

---

### Post by Trail on 2008-06-26
1) No. Well, there are two cases. If you set up VNC in a simple manner, it will display your normal desktop session ( :0 ). If you don't have one, it should show you gdm/kdm. You can configure it more complicated so that each VNC session opens a new X session as well (so each VNC connection starts on kdm/gdm).

2) Look up SSH. The ssh client should be already installed in your system. To use, "ssh <user>@<ip>" (append '-X' if you want to be able to open graphic programs as well). For the server, install openssh-server (iirc), then run /usr/sbin/sshd.

Other methods for 2) are telnet, rlogin etc, but are inferior to ssh.

---

### Post by ilrudie on 2008-06-26
ssh is the way to go.  for sessions that can survive disconnect add on screen.

---

### Post by Darkade on 2008-06-26
And if I want to use a windows machine as client? what could I use? Is there a VNC or SSH client you can recomend?

---

### Post by TheEndIsNear on 2008-06-26
> **Darkade said:**
> And if I want to use a windows machine as client? what could I use? Is there a VNC or SSH client you can recomend?

There is putty. [http://www.putty.org/](http://www.putty.org/)

Also there is cgywin. [http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by TJP on 2008-06-26
I have a question which is closely related to this thread. I often use ssh to login remotely. From time to time I'll find that my wife or kids has left themselves logged in, inadvertently. How do I log them out from my remote connection?

---

### Post by Darkade on 2008-06-26
Thanks I'll try putty and openssh-server :D

---

### Post by Trail on 2008-06-27
You could log in remotely with your wife's account do:

```

wall Metallica - Die die die my darling
kill -1 -9

```

wall is just sending a message. Nothing important, just for fun.

Manpage of kill mentions:
A PID of -1 is special; it indicates all processes except the kill process itself and init.
KILL       9   exit      this signal may not be blocked

---

