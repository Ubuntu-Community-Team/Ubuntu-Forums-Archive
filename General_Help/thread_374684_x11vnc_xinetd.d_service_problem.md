---
title: "x11vnc xinetd.d service problem"
date: 2007-03-02
forum: General Help
---

### Post by Underpants on 2007-03-02
Alright...

I followed this: 
[http://ubuntuforums.org/showthread.php?p=771174#post771174](http://ubuntuforums.org/showthread.php?p=771174#post771174)

And everything goes well. I can connect at any time, but it doesn't prompt me for a password or anything of that nature. 

I'd like to add the option to use a password file, or only enable localhost connections for SSH tunneling...

I need help securing this thing...

This works
```
server_args     = -inetd -o /var/log/x11vnc.log -display :0 -auth /var/lib/gdm/:0.Xauth -many -bg
```

This does not. When I try to connect I get an "EndOfStream" error with the linux viewer, or the windows viewer will give me fits about protocol negotiation. 
```
server_args     = -inetd -o /var/log/x11vnc.log -display :0 -rfbauth /home/aaron/.vncpasswd -many -bg
```

Help

---

### Post by Cappy on 2007-03-02
[http://www.karlrunge.com/x11vnc/]("http://www.karlrunge.com/x11vnc/")
> One approximate method involves starting x11vnc with the -localhost option. This basically requires the viewer user to log into the workstation where x11vnc is running via their Unix username and password, and then somehow set up a port redirection of his vncviewer connection to make it appear to emanate from the local machine. As discussed above, ssh is useful for this: "ssh -L 5900:localhost:5900 user@hostname ..." See the ssh wrapper scripts mentioned elsewhere on this page. stunnel does this as well.

---

### Post by Underpants on 2007-03-03
/home/aaron/.vncpasswd

is a file that I created and put a password in....

---

### Post by krunge on 2007-03-03
You need *both*  the -rfbauth and -auth /var/lib/gdm/:0.Xauth  options.  The -auth ...
option allows x11vnc to connect to the X display :0  It has nothing to do with VNC 
authentication or passwords.

Also, the -many and -bg options are not needed for -inetd mode.  The -localhost
option (mentioned by another) does not apply either.  In -inetd mode there is 
always a single connection that inetd sets up and there is no listening for TCP
connections by x11vnc. 

To improve security even more, consider using SSH or SSL:

[http://www.karlrunge.com/x11vnc/#tunnelling]("http://www.karlrunge.com/x11vnc/#tunnelling")

[http://www.karlrunge.com/x11vnc/enhanced_tightvnc_viewer.html]("http://www.karlrunge.com/x11vnc/enhanced_tightvnc_viewer.html")

---

