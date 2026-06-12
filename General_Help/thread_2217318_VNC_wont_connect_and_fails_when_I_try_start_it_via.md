---
title: "VNC wont connect and fails when I try start it via SSH"
date: 2014-04-16
forum: General Help
---

### Post by randypfau on 2014-04-16
I am attempting to get VNC working on my headless Mediasmart EX470 server. When I pull the hard drive and put it in a different pc and start it up, it works fine. When I move the hard drive back to the server I can SSH to it but i cannot connect to the server using VNC. So I manually tried to start the VNC server as shown below and I get the "Cannot open display" error. Is this because my server is headless and does not have a graphics card? Btw, I have Ubuntu desktop installed.

```
anonymous@SERVER-1:~$ sudo /usr/lib/vino/vino-server
[sudo] password for anonymous:
Cannot open display:
Run 'vino-server --help' to see a full list of available command line options
```

***I get the same error when i run the following...


```

anonymous@SERVER-1:~$ vino-preferences


(vino-preferences:22629): Gtk-WARNING **: cannot open display:


```



I ran netstat and this is what i get?


```

anonymous@SERVER-1:~$ netstat -an |more
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:49152           0.0.0.0:*               LISTEN
tcp        0     64 192.168.2.106:22        192.168.2.112:57178     ESTABLISHED
tcp        0      0 127.0.1.1:22            127.0.0.1:56243         ESTABLISHED
tcp        0      0 127.0.0.1:56243         127.0.1.1:22            ESTABLISHED
```

---

### Post by randypfau on 2014-04-16
^edited above

---

### Post by steeldriver on 2014-04-16
vino-server is a *desktop sharing* server - it sounds like you would be better off installing a traditional VNC server that runs its own display server

vnc4server and tightvncserver are both in the repos

---

### Post by HermanAB on 2014-04-17
Wait a moment...

You say it is a headless Server?  Just use SSH with X forwarding:
$ ssh -C -c blowfish -X user@server 'nautilus -g 600x400 /etc'

Then you can go all mousey clickety on the remote machine.

VNC is mostly a Windows thing.  If you need SSH on Windows, install Cygwin.

---

### Post by randypfau on 2014-04-23
> **HermanAB said:**
> Wait a moment...

You say it is a headless Server?  Just use SSH with X forwarding:
$ ssh -C -c blowfish -X user@server 'nautilus -g 600x400 /etc'

Then you can go all mousey clickety on the remote machine.

VNC is mostly a Windows thing.  If you need SSH on Windows, install Cygwin.


i am currently using Putty as a SSH client for windows. As far as the SSH server I am using the openSSH on the ubuntu machine. 

> **HermanAB said:**
> 
$ ssh -C -c blowfish -X user@server 'nautilus -g 600x400 /etc'
.

Is the above line all Id need to do to get X forwarding? Also is a Win7 client like putty able to support such tasks to where when I put in a command in the terminal to launch somthing with a GUI would it pop up i a seperate window on my windows machine?

---

### Post by steeldriver on 2014-04-23
Yes you can do it in Win7 - but you need an X server running on Windows (e.g. Xming, or you can do it via cygwin) and you need to check the 'Enable X11 forwarding' box in PuTTY

---

### Post by HermanAB on 2014-04-23
PuTTY is an SSH client.  To run X programs on Windows, you need to run a X server.  You can get that from Cygwin, or Xming and you got to run the X server first, before you start the SSH client.

---

