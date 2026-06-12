---
title: "how to set a unity session in VNC on ubuntu 13.10"
date: 2013-10-06
forum: General Help
---

### Post by odror on 2013-10-06
I have installed vnc4server. I am able to login to a virtual remote desktop.
I have been succssfull only with kde session. gnome-session or unity produced the gray window with no windows manager.

my ~/.vnc/xstartup is
> # Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
#gnome-session --session=ubuntu &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
vncconfig -iconic &
startkde &
#gnome-session  &
#xterm &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &

Thanks for any help

---

### Post by steeldriver on 2013-10-06
I've never found the 3d desktop to work well over VNC but if you want to try it then something like this should work - it may be very slow to draw the initial desktop though, during which you may see a black or gray screen and think it's not working

```

#!/bin/sh

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
    xrdb "$HOME/.Xresources"
fi

gnome-session --session=ubuntu &

```

If you just want the 'look' of the regular desktop I'd suggest using [FONT=courier new]gnome-session **--session=ubuntu-2d** &[/FONT] instead

---

### Post by odror on 2013-10-06
> **steeldriver said:**
> I've never found the 3d desktop to work well over VNC but if you want to try it then something like this should work - it may be very slow to draw the initial desktop though, during which you may see a black or gray screen and think it's not working



If you just want the 'look' of the regular desktop I'd suggest using [FONT=courier new]gnome-session **--session=ubuntu-2d** &[/FONT] instead
I have tried it with and without the -2d. I get only a grey screen

---

### Post by steeldriver on 2013-10-06
Hmm... in that case I don't know, perhaps it's something specific to 13.10? have you looked at the session log(s) in ~/.vnc/*xxxx*.log ?

---

### Post by fboecom on 2013-12-06
As I experienced and searched on different sites, 13.10 generates gnome errors which are shown in the VNC log file. So yes, it is a 13.10 problem.
gnome-session would already not work in 13.04 - you had to use gnome-session-fallback. Now in 13.10 all of gnome breaks.
I installed xfce4 and replaced the gnome call in xstartup with 
```
startxfce4 &
```
and the problem was fixed - be it I lost the well known gnome. But functionally Xfce is fine. Of course kde is an option too.

---

### Post by oid on 2014-01-18
Although the solution with the xfce is *not a unity session*, it is better to have this as a workaround than to have no solution at all!
Just a remark: for using ```
startxfce4 &
``` neither vnc-server, nor vnc-client is needed! Just:
[LIST=1]
[*] open a terminal in any X-server, make a secure connection to the host, e.g. ```
ssh -Y <your_login>@<your_host>
``` 
[*]authenticate with your password and 
[*]start a X-session with the host with the command ```
startxfce4&
``` 
[/LIST]
Just be careful, depending on your X-server you will most probably be able to interact with both computers and have icons/launchers pointing at either of them! If you don't close the terminal used for starting the xfce, you can terminate the session with ```
fg <number of the background job for startxfce>
``` and pressing Control+C.
Btw., this way it was even possible for me to make an ssh-connection from a mac-OS to an Ubuntu-server installation and use it via xfce4. I wish it would be possible to call gnome or unity this way, but I am getting the mentioned errors, too; my environment is vnc4server runnung under Ubuntu 13.10 server on the host side, Remmina Remote Desktop Client under Ubuntu 13.10 live CD on the user PC (with and without ssh)...

So back to the subject of this thread: is there really no way to start a unity (or gnome, or KDE, or X session) in Ubuntu 13.10?

Kind regards,
n.

---

### Post by kjdevocht on 2014-01-21
Could you post your xstartup file?  I can't quite get this to work.  I can get it to log in and display a terminal but when I uncomment the two lines 
[COLOR=#000000]*unset SESSION_MANAGER*[/COLOR]
[COLOR=#000000][I]exec /etc/X11/xinit/xinitrc

I still get the gray screen.  I am using vnc4server on 13.10

my xstartup looks like this.

[/I][/COLOR]#!/bin/sh


# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
 exec /etc/X11/xinit/xinitrc
 startxfce4 &


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

---

### Post by kjdevocht on 2014-01-21
Could you post your xstartup file?  I can't quite get this to work.  I can get it to log in and display a terminal but when I uncomment the two lines 
[COLOR=#000000]*unset SESSION_MANAGER*[/COLOR]
[COLOR=#000000][I]exec /etc/X11/xinit/xinitrc

I still get the gray screen.  I am using vnc4server on 13.10

my xstartup looks like this.

[/I][/COLOR]#!/bin/sh


# Uncomment the following two lines for normal desktop:
 unset SESSION_MANAGER
 exec /etc/X11/xinit/xinitrc
 startxfce4 &


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

---

### Post by kjdevocht on 2014-01-21
Thanks in advance for your help

---

