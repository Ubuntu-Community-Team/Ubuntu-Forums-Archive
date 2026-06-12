---
title: "Remote control on an ARM-based device (other than VNC)?"
date: 2015-07-16
forum: General Help
---

### Post by timonoj on 2015-07-16
Hi guys, 

Do you know any desktop remote control tool I could use to handle an ARM-based device (a Banana Pi)? I can't use x2go or variants, neither teamviewer...
And I'd prefer if it wasn't VNC, as it's not very reliable and gets me a lot of issues.

Thanks a lot!

---

### Post by tgalati4 on 2015-07-16
This works with a raspberrypi, after installing *openssh-server *

```
ssh -2 -Y bananapi_user@bananapi_machine xeyes
```

Not sure what desktop environment, but if it is lxde then use *lxpanel* to bring up the panel in the remote graphical environment.

This only works on a LAN with port 22.  If you need access on the WAN, then set up port-knocking so that some random port (53887) gets mapped to 22 for 10 minutes.  Under no circumstances should you simply put a pinhole in port 22.  You will quickly get slammed with password jackhammers.  If this setup works, then you should consider ssh keys and passwordless logins.

The command above gets amended with -p 53887.

---

### Post by timonoj on 2015-07-21
Thank you! Forgot to subscribe to my own thread so I missed your reply! I'll try from a local network tonight, as it seems from WAN it's not doing much (it stays without returning the prompt for about a couple of minutes, then it finishes. no window pops up nor anything).

---

### Post by timonoj on 2015-10-05
Sorry for letting this wait forever...
Seems I'm having issues here. 
I tried these options:
> jizarzu@MAHKGWKS021:~$ ssh -pXXXXX -ltimonoj XXXX.yyyy.zzz -X
[email]timonoj@XXXX.yyyy.zzz[/email]'s password: 
Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.4.103 armv7l)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Mon Oct  5 15:43:17 2015 from 175.45.6.234
/usr/bin/xauth:  /home/timonoj/.Xauthority not writable, changes will be ignored
timonoj@TimoPi:~$ xcalc
X11 connection rejected because of wrong authentication.
Error: Can't open display: localhost:10.0

> 
jizarzu@MAHKGWKS021:~$ ssh -2 -y [email]timonoj@XXXXX.yyyy.zzz[/email] -pXXXXX xeyes
[email]timonoj@XXXXX.yyyy.zzz[/email]'s password: 

This last option just sits idling watching life go by without giving me a prompt nor drawing the xeyes window.

---

### Post by tgalati4 on 2015-10-05
Did you install xeyes on the RaspberryPi?

Open a terminal on the Pi:

```
sudo apt-get install xeyes
```

I can't remember if xeyes is installed by default.  The Pi has a slimmed-down version of Linux, so a lot of stuff is missing.

Your first command didn't work because you need the -X or -Y (must be capital letters!  Sorry, my mistake.) which allows X11 (graphical) packets to be forwarded.  

```
man ssh
```

The second command didn't work because you used "-y" instead of "-Y", which is my mistake. -y switch means send error messages to syslog instead of the terminal.

---

