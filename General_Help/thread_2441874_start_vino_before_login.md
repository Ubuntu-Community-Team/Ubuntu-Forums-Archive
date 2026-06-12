---
title: "start vino before login"
date: 2020-04-27
forum: General Help
---

### Post by doorito on 2020-04-27
Hi,

Ubuntu 19.04 (I think Gnome, didn't really pick)
Converted by media computer from Windows 10 Ubuntu.  So far so good.
Computer is connected to TV.

Configured and using vnc/vino to connect to the computer.

Unfortunately vino starts after login to the desktop.  What I need is to have vino start on boot.  Currently I have to turn on the TV logon then I can connect and manage it remotely.  Is there a way to start vino before login?
I don't want to have to turn on the TV, login, just to remote to it.

I could enable auto login, but I don't like that risk.

When it was Windows, RDP started as soon as the computer booted up.  I can login at any time, also others can use my session, they have to login using their own session.

I checked the internet and this forum, there are many requests but no solutions.

Please help.

---

### Post by TheFu on 2020-04-27
Ubuntu 19.04 support ended last January.
Please move to a supported release.  20.04 was released last week and has 5 yrs of support.  19.10 support ends in July, so that wouldn't be a long term choice.

Please stay on supported releases.

---

### Post by doorito on 2020-04-28
19.04 was a typo.  I am on 19.10
So still supported.  Just not on latest.  When I installed Ubuntu 3 weeks ago I only had access to 19.10

---

### Post by TheFu on 2020-04-28
Excellent. Nothing wrong with 19.10, provided you upgrade to 20.04 in mid-June. Waiting would be smart, IMHO. Let the initial bugs in 20.04 get resolved over the next few months.

I've never used vino and avoid using RDP unless there's no other choice. Both seem to be tied to the desktop session, which cannot happen until someone logs in using a desktop session ON THE CONSOLE.

Another alternative ... to remotely connect to Linux systems with a full DE.

For about 10 yrs, I've been using NX for remote connections. Around 8 yrs ago, found x2go.  This provides a virtual desktop over a network connection.  Since it is virtual, no heavy-GUI DEs like gnome3 should be used.  LXDE, XFCE, Mate and plain openbox or fvwm all work well.  I don't know about KDE or LXQt, sorry. Avoid Gnome3.

People who switch from VNC/RDP to x2go are usually very happy.  Night vs Day.  x2go works over an ssh connection, so just ensure that ssh between your local device and the remote system are working. No other ports need to be setup.  There is an x2go-client and x2go-server.

X2go isn't perfect. There are some things certain users might not like/understand.  x2go is a VIRTUAL desktop, so if you are already using it and sit behind the console, login, then you won't see that desktop/session until you make an x2go connection to the virtual desktop.  Depending on the network speed and "server" performance, video playback my suck. Audio tends to work fine even over the internet.

x2go is very stable - months of uptime.
Changing active sessions to a different client machine is very nice. It is like reconnecting tmux, just with a desktop over a secure ssh session.

x2go ARM support is young. Mainly used by raspberry pi systems.
x2go-clients don't exist for non-computers - no Android/iOS that I'm aware, but I haven't looked in a few years.
While x2go is based on NX, most NX implementations have diverged from each other.

Start here: [https://wiki.x2go.org/doku.php/doc:installation:start](https://wiki.x2go.org/doku.php/doc:installation:start)

x2go is what I use for a full desktop, but most of the time, I just want to run a few programs on remote systems, but have the window displayed on the system where I'm working.  For that, especially on the same LAN, using ssh X11 forwarding is the easiest way. For example:
```
tf@hadar:~V$ ssh -X tf@lubuntu "firefox " &
```
Any GUI program should work, unless it requires direct GPU access or is tied to a specific session.  If you need help with setting up ssh, we can help. It is crazy simple to get key-based authentication.

If the username matches between the local and remote systems, then that can be left off.  If the remote system isn't known by DNS, then an IP address can be used above or put into the ~/.ssh/config file.

---

### Post by doorito on 2020-04-28
Hi,

That's a nice description of an alternative, thanks for providing that.
X2go seems like it will work and allows me to connect to the remote machine.

Just searched and read the information on it.

My media PC isn't very powerful and a bit old, generally I like to keep systems as lean as possible and tend to use only what is included with the install system -additional applications.
I'm not familiar with the Linux world as I am on Windows.  Sure I've dabble a bit but this is the first time I've fully embrace the system, so I'm new to the experience and welcome recommendations.

I'm asking for vino because it was pre-installed with Ubuntu.  I wanted to stay away from X11VNC server for example for this reason, just don't want the extra baggage.

I will try X2go, it looks neat.

For now I have (grudgingly) enable auto logon.  Within 10 minutes the system will automatically lock so the risk isn't as bad.  I was asking in case there was a simple way to configure existing application to start...

---

### Post by TheFu on 2020-04-28
You can use remote X11.  That is built into any Unix system that has a GUi.   Well, almost any w/ a GUi.  No need to setup auto-login either.

---

