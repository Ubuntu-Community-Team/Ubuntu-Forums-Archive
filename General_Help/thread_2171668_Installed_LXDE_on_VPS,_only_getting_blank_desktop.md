---
title: "Installed LXDE on VPS, only getting blank desktop"
date: 2013-09-01
forum: General Help
---

### Post by james40 on 2013-09-01
Hello, 
I'm sorry if this has been covered but I have tried troubleshooting this myself for about a day and I'm about to give up so I hope someone here might be able to help me.

Ubuntu 13.04

I started off by following this guide: [https://panel.cinfu.com/knowledgebase/20/Grpahical-Desktop-LXDE-installation-in-VPS-with-Ubuntu-OS-for-a-low-RAM-VPS-plans.html](https://panel.cinfu.com/knowledgebase/20/Grpahical-Desktop-LXDE-installation-in-VPS-with-Ubuntu-OS-for-a-low-RAM-VPS-plans.html).

While everything seems to be fine, when I connect I only get a blank ubuntu desktop using tightVNC. I can add new folders and documents but ctrl+alt+T doesn't bring up the terminal.

I suspect there might be a problem with my xstartup file?

```


#!/bin/sh


xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
lxterminal &
/usr/bin/lxsession -s LXDE &
#unset SESSION_MANAGER
#exec /etc/X11/xinint/xinitrc



```

I've tried a few different strings like (startlubuntu) and some others I have found on other websites but I still get the same result.

This is from /root/.vnc/vps:1.log

```


01/09/13 01:26:04 Xvnc version TightVNC-1.3.9
01/09/13 01:26:04 Copyright (C) 2000-2007 TightVNC Group
01/09/13 01:26:04 Copyright (C) 1999 AT&T Laboratories Cambridge
01/09/13 01:26:04 All Rights Reserved.
01/09/13 01:26:04 See http://www.tightvnc.com/ for information on TightVNC
01/09/13 01:26:04 Desktop name 'X' (vps:1)
01/09/13 01:26:04 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
01/09/13 01:26:04 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/root/.Xresources'



```

Can anyone provide some insight for this newbie please?

My VNC screen looks like this (Taken from another user on the forums having a simliar problem with his ubuntu-desktop gnome installation)

 [IMG]http://i.stack.imgur.com/kigbj.jpg[/IMG]

---

### Post by TheFu on 2013-09-01
I use **/usr/bin/startlxde &**.
However, I don't use VNC - too slow.

Also, we need to remember that there isn't much of an environment when we connect, so it is a good idea to set that up.
```

source ~/.bashrc

if [ -f ~/.config/openbox/lxde-rc.xml ] ; then
   /usr/bin/startlxde &
   # openbox --config-file ~/.config/openbox/lxde-rc.xml &
else
   openbox &
fi
```

Clear as mud?

---

### Post by james40 on 2013-09-01
Thanks for your assistance TheFu, 
Unfortuantely repacing 
```
[COLOR=#000000][FONT=Ubuntu Mono]/usr/bin/lxsession -s LXDE &[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
with [/FONT][/COLOR]```
**/usr/bin/startlxde & **
```Didn't have any change on my end.

When I add the code you provided to my bashrc I still only get a blank desktop but I get this error when logging to SSH (I am assuming its attempting to start LXDE when I connect)\
```
** Message: main.vala:63: Session is LXDE** Message: main.vala:64: DE is LXDE


(lxsession:1259): Gtk-WARNING **: cannot open display:

```

May I ask what you use as opposed to VNC?

---

### Post by TheFu on 2013-09-01
I use FreeNX on the server and NoMachine's NX client on whatever client I'm on.

That "cannot open display" error is expected. You can't use plain ssh and expect a graphical environment.  Read up on X/Windows to understand why - the short answer is to open an xterm from a system running an X/Windows server - i.e. NOT MS-Windows, then use ssh -X userid@remote machine ... then you can start whatever window manager you like.
I wrote this article a few years ago trying to explain things. [http://www.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://www.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)  It is NOT a how-to.

---

### Post by james40 on 2013-09-02
Thanks TheFu,
Yes I am fully aware SSH is unable to load a graphical environment haha. I was just included the code to reassure you I implemented the code in my bashrc correctly. I still get the same result, however, on my tightVNC. Maybe it is tightVNC? Thanks for your help anyway I'll see if I can diagnose this further.

---

### Post by TheFu on 2013-09-02
> **james40 said:**
> Thanks TheFu,
Yes I am fully aware SSH is unable to load a graphical environment haha. I was just included the code to reassure you I implemented the code in my bashrc correctly. I still get the same result, however, on my tightVNC. Maybe it is tightVNC? Thanks for your help anyway I'll see if I can diagnose this further.

I don't htink you want to put that code in your ~/.bashrc. Sorry if that was implied. Create a new script - put all those lines into it.

VNC basically sucks. All of them. ultra/tight/generic/special/super-special ... if it says VNC, it sucks.  NX is about 2x more efficient and includes key-based ssh tunneling so you don't need anything network-wise except the ssh port you are using open. Works great from all over the world.

---

### Post by james40 on 2013-09-03
Thanks for you help TheFu

I tried FreeNX and found it extremely slow on my end. While I loved it's features and the program itself it just didn't work for me.

After a little bit of digging I realized that my xstartup config file had [COLOR=#000000][FONT=Ubuntu Mono]/etc/X11/Xsession [/FONT][/COLOR]but I don't even have an x11 folder #-o so i removed the line completely and everything works great. 
 
Thanks for you time and effort TheFu

PS. How do you mark the thread as solved? NVM Figured it out

---

