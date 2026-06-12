---
title: "Headless VNC"
date: 2008-06-10
forum: General Help
---

### Post by Per Olav on 2008-06-10
I have a headless server which is far far away from me, so physical access to it is not very easy. (4600 miles)

I'd like to run a X server on it, _just_ for VNC, so I can access my stuff there. Probably through a SSH tunnel with a lightweight wm like fluxbox

Web interfaces, ftp, webdav and so on is not what I want.

How do I go about this? Is it possible to set this up without connecting a screen to it ? 

Thanks in advance

Per Olav

---

### Post by sizzam on 2008-06-11
Here's how I would do it:

1.  Tell GDM not to start when automatically when the machine starts:
```
$ sudo update-rc.d -f gdm remove
```

2.  Install Fluxbox and tightvncserver
```
$ sudo apt-get install fluxbox tightvncserver
```

3.  Create a VNC password for your account
```
$ vncpasswd

Using password file /home/<username>/.vnc/passwd
Password: 
Verify:
Would you like to enter a view-only password (y/n)? n
```

4.  Create the file **~/.vnc/xstartup** with the following config:
```
#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
fluxbox &
```

5.  Make **~/.vnc/xstartup** executable:
```
$ chmod +x ~/.vnc/xstartup
```

6.  Use **/etc/rc.local** to start the VNC session whenever the machine boots.  You can specify the display to use, I usually use something unusual like 20.  Mine looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

su myusername -c "tightvncserver :20"

exit 0
```

7.  Reboot.  After the machine comes up, you should be able to access the VNC session with:
```
$ vncviewer your.machine.ip:20
```

8.  To make it all happen via SSH, install SSH:
```
$ sudo apt-get install ssh
```

Then connect to the VNC session via an SSH tunnel like this:
```
vncviewer machine.ip.address:20 -via machine.ip.address
```

That should prompt you for your SSH password, then show you your VNC session, then ask for your VNC password.  Your SSH port (default is 22) is the only port that would need to be accessible in this scenario.

---

### Post by Per Olav on 2008-08-03
Thank you, very much appreciated! :)

---

