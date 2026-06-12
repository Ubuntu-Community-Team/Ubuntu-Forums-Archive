---
title: "run graphical programs from ssh"
date: 2013-09-09
forum: General Help
---

### Post by conradin on 2013-09-09
Hi all,
I have an ssh server on my desktop where soe users login and run programs. One of the programs is XMOLVIEW. 
in the sshd_config i have specified that X11 Forwarding is allowed. 
But I get a variety of errors depending on what i try to open. 

I know there is a way to make it so my remote users can run graphical programs, but i dont recall how. 
I am using Ubuntu 13.04, and my desktop is running on tty7, just to specify that its not a pure ssh server.

The graphical programs I want to run are on the server.
users login with ssh -X -l user <IP>
 
 
```

:~$ xmolview
Can't open display:

:~$ gedit

** (gedit:6986): WARNING **: Could not open X display
Cannot open display:
Run 'gedit --help' to see a full list of available command line options.

:~$ firefox

(process:6987): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Error: no display specified

```

can anyone point me in the right direction?

---

### Post by pqwoerituytrueiwoq on 2013-09-10
IIRC:
[FONT=courier new]firefox --display=:0.0[/FONT]
still requires ssh -X
also run [FONT=courier new]DISPLAY=:0.0[/FONT] so you don't have to use --display

---

### Post by steeldriver on 2013-09-10
What client are you connecting from (another *nix? Windows? Mac?) what X server is running on it?

---

### Post by gnusci on 2013-11-11
What about the instructions in the following page:

[http://vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by den_ on 2013-11-11
> **conradin said:**
> Hi all,
I have an ssh server on my desktop where soe users login and run programs. One of the programs is XMOLVIEW. 
in the sshd_config i have specified that X11 Forwarding is allowed. 
But I get a variety of errors depending on what i try to open. 

I know there is a way to make it so my remote users can run graphical programs, but i dont recall how. 
I am using Ubuntu 13.04, and my desktop is running on tty7, just to specify that its not a pure ssh server.

The graphical programs I want to run are on the server.
users login with ssh -X -l user <IP>
 
 
```

:~$ xmolview
Can't open display:

:~$ gedit

** (gedit:6986): WARNING **: Could not open X display
Cannot open display:
Run 'gedit --help' to see a full list of available command line options.

:~$ firefox

(process:6987): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Error: no display specified

```

can anyone point me in the right direction?

I had the same problem when I was trying to connect to my 12.04 server from my 13.04 workstation. However, my old machine, whose disk I now use in VirtualBox, and which still runs 12.04, was able to connect without problems.

I haven't investigate further, but it looks like there are some compatibility problems between version of X libraries being used on those systems.

---

### Post by efflandt on 2013-11-12
Note that is **ForwardX11 yes** is included in your ~/.ssh/config for that host (or in general for Host *) or -X is included in the command line, DISPLAY should automatically be set in the environment to forward X program output back through ssh unless disallowed by sshd_config or some other issue.

For example this is ssh from Ubuntu 12.04 to a very old SuSE 8.2 server (Celeron 300 cpu w/158 MB RAM):```
efflandt@xps8100-1204:~$ ssh mainpc
Last login: Sat Oct 26 17:13:04 2013 from unknown78e40026b8ac.domain_not_set.invalid
Have a lot of fun...
efflandt@realhost:~> echo $DISPLAY
localhost:10.0
``` DISPLAY=:0.0 would certainly be incorrect for a forwarded display.

While most things work as expected, when I run mozilla on the remote, for some reason it runs my local firefox with its settings (defaulting to Ubuntu Google page).```
efflandt@realhost:~> which mozilla
/usr/X11R6/bin/mozilla
efflandt@realhost:~> mozilla &
[1] 14583
efflandt@realhost:~>
```

---

