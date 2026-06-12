---
title: "(Ubuntu 18.04) VNC Server no longer working, where did I go wrong?"
date: 2019-09-29
forum: General Help
---

### Post by blckassn on 2019-09-29
I had a VNC server setup on my machine just fine about a month ago, but for some reason it's not working anymore.  I even tried removing all packages and starting fresh but it's still not working.  I honestly don't know what to do, if you have any suggestions please let me know.

I'm running Ubuntu 18.04 Desktop with default gnome.

VNC server showing active on machine

```
$ ss -tulpn | egrep -i 'vnc|590'
```

[ATTACH=CONFIG]284104[/ATTACH]

Private IP address of machine

```
$ sudo ifconfig
```

[ATTACH=CONFIG]284102[/ATTACH]

Port forwarding enabled in router

[ATTACH=CONFIG]284101[/ATTACH]

Time out error in VNC Viewer

[ATTACH=CONFIG]284103[/ATTACH]

---

### Post by Skaperen on 2019-09-30
does it have a port open?  try this:  [COLOR=#0000cd][FONT=courier new]**sudo netstat -antp**[/FONT][/COLOR]

---

### Post by blckassn on 2019-09-30
Port is open.

[ATTACH=CONFIG]284105[/ATTACH]

Also, ufw is currently disabled.  And here are the two xstartup files I've tried to use:

[FONT=monospace]    #!/bin/sh
def
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
xrdb $HOME/.Xresources
xsetroot -solid grey    gnome-session &

and

[/FONT][FONT=monospace]    #!/bin/sh    # Start
Gnome 3 Desktop
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
vncconfig -iconic &
dbus-launch --exit-with-session gnome-session &[/FONT]

---

### Post by blckassn on 2019-09-30
I checked the log file and it says:

Unable to create /home/user/.dbus/session-bus

How come that is happening?

---

### Post by Skaperen on 2019-09-30
there could be many reasons, such as:

a permission setting does not allow it
something else already exists there
the filesystem is full

those are just some examples.  so what happens when you have a VNC client connect to the port?  does is complete the connection then freeze?

---

### Post by blckassn on 2019-09-30
The connection doesn't complete at all, it tries to connect and then gives me the error in my first post.  I enter something like 192.168.0.127:5901 and it continually tries to connect without success.

File systems aren't full, I hardly have anything on the computer.

[ATTACH=CONFIG]284106[/ATTACH]

---

### Post by blckassn on 2019-09-30
Update, now I'm able to connect but all I have is a blank, black screen.

---

### Post by blckassn on 2019-09-30
I found a fix that I don't like so if anyone has a better solution please let me know.

I used the fix from [this youtube video]("https://www.youtube.com/watch?v=_8YZst2x9GE").  it works, it has a weird desktop, but i guess its better than nothing right now.

---

### Post by stoughj on 2019-10-19
For starting a brand new gnome session on a remote VNC 18.04 server, I found an initial solution [here]("https://ubuntuforums.org/showthread.php?t=2399979"). I updated my server-side ~/.vnc/xstartup to read:
```

#!/bin/sh
export XKL_XMODMAP_DISABLE=1
export XDG_CURRENT_DESKTOP="ubuntu:GNOME"

gnome-session --session=ubuntu &

```

This gets a nice ubuntu desktop with the newer interface, but without the side dock. I add the dock manually through enabling gnome-tweaks->Extensions->Ubuntu dock. I know there must be a way to do this in the xstartup, but I've wasted enough time.

My client is an 18.04 laptop running Remmina, and I use tunneling (server-side ~/.vnc/config includes "localhost=yes"),

---

