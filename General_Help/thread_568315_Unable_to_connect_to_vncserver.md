---
title: "Unable to connect to vncserver"
date: 2007-10-05
forum: General Help
---

### Post by clos on 2007-10-05
I installed a vncserver via 
```
apt-get install vncserver
```

Then I tried to start the vncserver via 
```
vncserver
```

It didn't ask me for a password, but it returned with
```

New 'X' desktop is 89-xxx-xxx-81.internetserviceteam.com:1

Starting applications specified in /etc/X11/Xsession
Log file is /xxxxxx/.vnc/89-xxx-xxx-81.internetserviceteam.com:1.log

```

So then I go to Tight VNC on my windows box and try to connect to the server with **xx.xxx.xxx.xx:1**, but it returns that it can't connect to the server

This is a dedicated server that I'm renting, the only things installed on it so far are xterm, wine, vncserver and xfce.  A week ago I had Fedora 4 running on the box and vncserver was running fine, but I got my OS changed to Ubuntu because Fedora 4 isn't supported anymore.

Is it possibly a problem with SELinux or something? I know Ubuntu sometimes gets goofy with that kind of stuff...

When I try 
```
ps -ef | grep vnc
```

It returns
```

root     10736  8059  0 19:32 pts/0    00:00:00 man vncserver
root     10795  8059  0 19:37 pts/0    00:00:00 grep vnc

```


EDIT - Alright I installed the tightvncserver package and for some reason it works now, but it looks like *** how I can make it look better?
[IMG]http://img124.imageshack.us/img124/2774/sp3220071005172204rk2.png[/IMG]

---

