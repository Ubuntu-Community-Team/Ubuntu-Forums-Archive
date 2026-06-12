---
title: "How To Install Gui"
date: 2008-01-26
forum: General Help
---

### Post by taimur on 2008-01-26
Hi
How To Install Gui In Linux Ubuntu Server
And Also How To Configure Vnc In It Through Terminal Commands

---

### Post by gvartser on 2008-01-26
To install GUI:
```
sudo apt-get install ubuntu-desktop
```

And for VNC:
Check out: [http://ubuntuforums.org/showthread.php?t=383053&highlight=configure+vnc](http://ubuntuforums.org/showthread.php?t=383053&highlight=configure+vnc)
Best regz,
/g

---

### Post by taimur on 2008-01-26
thanks for help to install gui
but 
still you didn't understand that how to configure vnc through terminal commands bec. i m using computer remotly it is possible to do it?

---

### Post by gvartser on 2008-01-27
1) log on to your server ussing ssh

2) Install VNC Server: (Need sudo / root access to do this)
```
sudo apt-get install vncserver

```

3) Start VNC Server: (Start it as the user you would like to login as. NOT AS ROOT)
```
vncserver
```

Then set a password, when asked for it:
```
You will require a password to access your desktops.

Password: 
Verify:   

New 'X' desktop is <host_name>:1
```


4) Connect to your vnc server using the info given in "New 'X' desktop is:"

Additional info regarding VNC:
To stop the vncserver:
```
vncserver -kill :<display number>
```

Further information:
```
vncserver --help
```

/g

---

### Post by taimur on 2008-01-27
when i m going to install 

this is coming



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by zvacet on 2008-01-27
```
sudo dpkg --configure -a
```

---

### Post by taimur on 2008-01-27
ok now i install vnc i set passowrd but still i can't access it by my computer

---

### Post by taimur on 2008-01-27
it is coming unabel to connect host: connection refused (10061) this messge is coming from my computer windows 
and
is there any thing should i do after installing vnc or want to start gui or something or directly connect vnc through my computer

---

### Post by gvartser on 2008-01-28
Hmm check the firewall settings in windows. Make sure that vnc is allowed.

/g

---

### Post by taimur on 2008-01-28
yeah it is alowed i can access other computers through but not that one

---

### Post by taimur on 2008-01-28
when i type vncserver this is coming

Warning: kickseed:1 is not taken because of /tmp/.X1-lock
Remove this file if there is no X server kickseed:1

New 'X' desktop is kickseed:2

Starting applications specified in /etc/X11/Xsession
Log file is /root/.vnc/kickseed:2.log

---

### Post by gvartser on 2008-01-28
> 
Warning: kickseed:1 is not taken because of /tmp/.X1-lock
Remove this file if there is no X server kickseed:1


This is because you did not stop the previous running vnc-server correctly or at all:
> 
Text taken from "man vncserver"
 -kill :display
              uses  kill(1) to send the TERM signal to the VNC server with the specified display number and
              removes the lockfile. This option should be used to cleanly shut down  a  server  started  by
              vncserver.  Only works when the server was started with the vncserver command.

       -clean This  option  can  be used in conjunction with -kill and will also remove the log file of the
              server process.


To remove (Manually):
```
rm /tmp/.X1-lock
```

If you feel uncomfortable with removing a a file, then rename it instead:
```
mv  /tmp/.X1-lock /tmp/.X1-lock.old
```

/g

---

### Post by taimur on 2008-02-04
New 'X' desktop is kickseed:1

Starting applications specified in /etc/X11/Xsession
Log file is /root/.vnc/kickseed:1.log



it is still not working and coming like this

---

### Post by taimur on 2008-02-04
do i need to run any thing or vnc server or anything through putty before accessing GUI through vnc ?

---

### Post by taimur on 2008-02-04
if i give you remote access of my computer can you configure it for me?

---

