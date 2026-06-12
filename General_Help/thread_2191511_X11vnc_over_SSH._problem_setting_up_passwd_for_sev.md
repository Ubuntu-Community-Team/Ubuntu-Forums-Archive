---
title: "X11vnc over SSH. problem setting up passwd for several users"
date: 2013-12-03
forum: General Help
---

### Post by lavikl on 2013-12-03
Hi everyone
I am using ubuntu 12.04 server. I need to allow multiple users to log in simultaneously and each one should be able to use GUI in his own account.  
I've followed this thread [http://ubuntuforums.org/showthread.php?t=45565&page=8](http://ubuntuforums.org/showthread.php?t=45565&page=8) for installing x11vnc and autocutsel. although x11vnc was installed through the ubuntu software center and not manually. same goes for autocutsel.
I've set the passwd using the GUI of x11vnc because I got this error:

> $ vncpasswd ~/.vnc/passwd
No command 'vncpasswd' found, did you mean:
 Command 'vnc4passwd' from package 'vnc4server' (universe)
vncpasswd: command not found


My problem is that when I log into other user accounts I get the same error, that vncpasswd is not found so their password cannot be set up.

Any suggestions ?

---

### Post by Lars Noodén on 2013-12-03
Each user has to set up his or her own vnc password.  When you log in without one the warning message tells you how to create one on the remote host:

```

x11vnc -storepasswd

``` 

That will put the password in  ~/.vnc/passwd and has to be done for each user that plans to run x11vnc.

Be sure to use the -localhost and -usepw options when setting up tunneling on the local host.

```

ssh -L 5900:localhost:5900 *xx.yy.zz.aa* 'x11vnc -localhost -usepw -display :0' 

```

---

### Post by lavikl on 2013-12-03
Thank you!
I'll try it.
I Just to make sure I got it right (kind of a newbie here...)
I need to log in into evey user account I've set up, then use the code:
> x11vnc -storepasswd
which will store his passwd into the VNC file.
then the command:
> ssh -L 5900:localhost:5900 xx.yy.zz.aa 'x11vnc -localhost -usepw -display :0'
should be used by every user, on the client side, when he/she wishes to log in to VNC through the SSH tunnel. 
Did I get it right ?
and if so, how can it be set-up when using a Windows SSH-VNC terminal ? (for those users who for some reason stick to windows...)

---

### Post by Lars Noodén on 2013-12-03
Yes, that ssh works to get a VNC session but only if the user already is logged in graphically (in an X session) on the remote machine.   

So if you want a machine where no one is already logged in graphically and then they connect via ssh to start vnc that will need some more exploring.  I've looked around a bit but not found any obvious solution.  The -auth option for x11vnc  should do something but the help text is missing info about lightdm and it appears to need root as well, so I hope there is another way.

---

### Post by lavikl on 2013-12-03
I'll keep exploring and if I get something working I'l post it.
Thanks ! :)

---

### Post by Lars Noodén on 2013-12-03
Ok.  Here's a partial solution.  If you split that up into three parts instead of two, then it works.  If no one is logged in then you start the VNC server as root on the remote host, 

```

sudo x11vnc -localhost -usepw -auth /var/lib/lightdm/.Xauthority -display :0

```

Then on the local host make the tunnel.

```

ssh -L 5900:localhost:5900 *xx.yy.zz.aa*

```
 
Then also on the local host, run the vnc client.
```

 xtightvncviewer localhost:0

```

There is a big drawback to that.  When you do it that way, the remote machine is open and logged in just as if were sitting at it.  Anyone walking by can use the keyboard and mouse as well as see what's on the screen.  It's probably ok if the machine is in a physically secure and private location but, again, there should be a better way.

---

### Post by Lars Noodén on 2013-12-03
Actually, looking at the manual page for [xtightvncviewer](http://manpages.ubuntu.com/manpages/saucy/en/man1/xtightvncviewer.1.html), the ssh tunnel can be made by the vnc client itself and does not need a separate, extra step.

```

xtightvncviewer -via *xx.yy.zz.aa* localhost:0 

```

Apparently that calls the ssh client itself and makes the tunnel for you.  No need for a separate action any more

---

