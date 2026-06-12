---
title: "vnc4server opening external ports? Why?"
date: 2008-01-14
forum: General Help
---

### Post by benblout on 2008-01-14
I want to run vnc4server and not open any external ports.
I am using 6.06, and my network interface eth0) is assigned 192.168.0.4

The vncserver I am running:
```
$ ls -l /usr/bin/vncserver
lrwxrwxrwx 1 root root 27 2007-05-13 21:31 /usr/bin/vncserver -> /etc/alternatives/vncserver
$ ls -l /etc/alternatives/vncserver
lrwxrwxrwx 1 root root 19 2007-05-13 21:31 /etc/alternatives/vncserver -> /usr/bin/vnc4server
```Starting the vncserver, note that I already have two  X servers running, so vnc4server picks  the display :2 
```
$ vncserver -nohttpd -localhost

Warning: chipmunk:1 is taken because of /tmp/.X1-lock
Remove this file if there is no X server chipmunk:1

New 'chipmunk:2 (*****)' desktop is chipmunk:2
```And look - it opens a port on 192.168.0.4:
```

$ nmap 192.168.0.4
Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2008-01-14 22:07 EST
Interesting ports on 192.168.0.4:
(The 1669 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
<snip>
6002/tcp open  X11:2

$ sudo netstat -l -n -p -t -u -w | grep 6002
tcp        0      0 0.0.0.0:6002            0.0.0.0:*               LISTEN     30473/Xvnc
tcp6       0      0 :::6002                 :::*                    LISTEN     30473/Xvnc
```Any Ideas?  I don't like this port being open to the world.

---

### Post by benblout on 2008-01-16
Is there a better forum to be asking this question in?

Should I just open a bug report?

---

### Post by bodhi.zazen on 2008-01-16
Not sure what you are asking. You are starting a server which accepts connections, so it opens ports.

-localhost , as an option, limits connections but does not keep a port from opening.

connect via localhost:6002

---

### Post by benblout on 2008-01-17
> **bodhi.zazen said:**
> Not sure what you are asking. You are starting a server which accepts connections, so it opens ports.

-localhost , as an option, limits connections but does not keep a port from opening.

Well sure, a server should open ports.  To be clear, here is what happens without the -localhost option.  I have snipped a bunch of extraneous lines

```
$ vncserver :2
$ nmap 127.0.0.1; nmap 192.168.0.4
Interesting ports on localhost.localdomain (127.0.0.1):
PORT     STATE SERVICE
<snip>
5902/tcp open  vnc-2
6002/tcp open  X11:2

Interesting ports on 192.168.0.4:
PORT     STATE SERVICE
<snip>
5902/tcp open  vnc-2
6002/tcp open  X11:2
```

So the above makes sense - the same ports are opened on my local and external interfaces.  Compare that to what happens when I use the -localhost option:
```
$ vncserver :2 -localhost
$ nmap 127.0.0.1; nmap 192.168.0.4

Interesting ports on localhost.localdomain (127.0.0.1):
<snip>
5902/tcp open  vnc-2
6002/tcp open  X11:2

Interesting ports on 192.168.0.4:
PORT     STATE SERVICE
<snip>
6002/tcp open  X11:2
```

So supplying the -localhost argument did prevent port 5902 from being opened on 192.168.0.4, as the -localhost argument would imply.  However, the X server is still
listening on the external port.

This doesn't seem to be a default behavior that is as secure as possible.  In general, Ubuntu is *very* conservative  when opening ports, something I appreciate.  But here an external port is being opened for no real reason that I can see.

Does that make more sense?

---

