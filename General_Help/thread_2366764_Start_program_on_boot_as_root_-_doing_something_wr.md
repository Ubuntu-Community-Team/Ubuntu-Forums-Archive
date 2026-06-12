---
title: "Start program on boot as root - doing something wrong"
date: 2017-07-21
forum: General Help
---

### Post by Andrew_Benjamin on 2017-07-21
I'd like my server to start the program "sabnzbdplus" on boot prior to my logging in/taking any action.
For whatever reason, I have sabnzbdplus configured on my machine to require me to start it as root (sudo sabnzbdplus) - I think some storage area where it dumps stuff may be owned by root, but I'm not changing anything at this point.

I added the line

sabnzbdplus

to /etc/rc.local just before the exit 0 line.  This doesn't seem to do anything (ie it isn't running when I check from another machine).

I also added the line 'sudo sabnzbdplus' to the startup applications - again, no help there.


I'm running 16.04.02 LTS.

If sabnzbdplus isn't running, I need to open a window on my non-local machine, start the program as root and then leave the machine and window open while the operation takes place.  If it is running from the main machine, I can just trigger it with a file and not have a terminal window open.

Help on fixing what should be a simple issue?

Thanks.

Andrew

---

### Post by SeijiSensei on 2017-07-21
Try giving the full path to the program in rc.local.

---

### Post by deadflowr on 2017-07-21
[s]Put the full path of the sabnzbdplus in the rc.local file,[/s]
^Ninja'd

You can try and use whereis to get the location
```
whereis sabnzbdplus
```
It should return the full path location.
Use that

---

### Post by Andrew_Benjamin on 2017-07-21
> **deadflowr said:**
> [s]Put the full path of the sabnzbdplus in the rc.local file,[/s]
^Ninja'd

You can try and use whereis to get the location
```
whereis sabnzbdplus
```
It should return the full path location.
Use that


That command returns


sabnzbdplus: /usr/bin/sabnzbdplus /usr/share/sabnzbdplus /usr/share/man/man1/sabnzbdplus.1.gz


I'll go with /bin and /share (and the full path, of course) and by process of elimination, hope one of them works.

Andrew

---

### Post by deadflowr on 2017-07-21
Try the  /usr/bin/sabnzbdplus
Good luck

---

### Post by Andrew_Benjamin on 2017-07-21
So far, no joy.

I've used both the /bin file and the /share version

There is a website on starting as a service:
```
http://blog.itsux.com/2011/05/ubuntu-sabnzbd-auto-start-on-reboot.html
```
which says to edit the file
```
[COLOR=#666659][FONT=monospace]/etc/default/sabnzbdplus[/FONT][/COLOR]
```
and set USER=root (in my case)
HOST=0.0.0.0 and
PORT=8090 (in my case)

and to start with /etc/init.d/sabnzbdplus start

When I do this from the command line, it still asked me for a user and then a password.

So, this doesn't work, either.

I've tried all my options, and nothing starts at boot.

All I want is the equivalent of 'sudo sabnzbdplus' without asking for passwords, etc. to run at boot.


Help?

Andrew

---

### Post by steeldriver on 2017-07-21
Those instructions look applicable to an upstart-based init system - 16.04 uses systemd, so the procedure will likely be somewhat different

Depending how you installed it, the package may provide its own systemd service files - what does

```

systemctl list-unit-files sa*

```

return?

---

### Post by Andrew_Benjamin on 2017-07-21
> **steeldriver said:**
> Those instructions look applicable to an upstart-based init system - 16.04 uses systemd, so the procedure will likely be somewhat different

Depending how you installed it, the package may provide its own systemd service files - what does

```

systemctl list-unit-files sa*

```

return?

Unfortunately, nothing is returned for sabnzbd.

```
UNIT FILE      STATE
samba.service  masked
saned.service  masked
saned@.service indirect
saned.socket   disabled


4 unit files listed.

```

Is there anything I could do with sudoers to make this work?

Next?


Andrew

---

### Post by SeijiSensei on 2017-07-22
Enter this command in rc.local

```
/etc/init.d/sabnzbdplus start
```

You were prompted for a username and password before because you didn't use sudo.  Since rc.local runs with root privileges by default, it doesn't need sudo.

---

