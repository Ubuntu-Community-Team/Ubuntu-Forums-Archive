---
title: "VNC options for Ubuntu MATE 20.04?"
date: 2020-08-26
forum: General Help
---

### Post by kentaylor2525 on 2020-08-26
I have been using various flavors of VNC for many years on and between various Linux distros/versions and even Windoze. Recently I installed Ubuntu Mate 20.04 on a couple of machines. On Ubuntu Mate 18.08 and CentOS 7 I am currently using Tigervnc with excellent results.  On 20.04... no go.  Some excellent instructions on TecMint show me what appears to be the root cause of my issues```
en@taylor30:~$ sudo apt install tigervnc-standalone-server tigervnc-common tigervnc-xorg-extension tigervnc-viewer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tigervnc-xorg-extension : Depends: xserver-xorg-core (>= 2:1.7.7)
E: Unable to correct problems, you have held broken packages.
```The version of xserver-xorg-core which is available in the repos would remove the Mate desktop if I tried to install it :mad: If I install tigervnc-standalone-server without the extension package the server will run but I am unable to start a desktop to which I can connect.

I have installed and run x11vnc. However, the numeric keyboard does not work/

I have installed and run vnc4server. It works reasonably well except that I cannot connect over vnc if I have the console on the machine logged in or I connect via vnc I cannot logon to the console. I have read that this is a known limitation.

Tigervnc is my preferred option. Does anyone have any ideas how to work around the issues I described above?

TIA,

Ken

---

### Post by scorp123 on 2020-08-27
I use the 'normal' Ubuntu 20.04 that comes with GNOME and I have these packages installed:

[LIST]
[*]tigervnc-common
[*]tigervnc-standalone-server
[*]tigervnc-viewer
[/LIST]

I am not installing ```
tigervnc-xorg-extension
```
I guess that it is that package that causes the dependency issues in your case? But you don't really need that package anyway. TigerVNC is perfectly usable without that.

And this is my ```
~/.vnc/xstartup
``` script:

```

#! /bin/sh

# Fix to make GNOME stuff work
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS

# exec /etc/X11/xinit/xinitrc
xrdb $HOME/.Xresources

# Set a plain grey desktop background for now.
xsetroot -solid grey

# before Ubuntu 18.04:
# gnome-settings-daemon &

# Ubuntu 18.04 and later:
/usr/lib/gnome-settings-daemon/gsd-xsettings &

# Set a nice wallpaper via 'nitrogen' package.
# If nothing is set yet the desktop background will be plain grey
# as defined above with the 'xsetroot' command.
# The wallpaper settings will be saved and restored the next time.
# This is optional.
nitrogen --restore &

# Set a taskbar via 'tint2' package
# This is optional.
tint2 &

# Start OpenBox session because it's resource-friendly and works great
# even when connecting with my mobile phone.
# Replace with whatever session you want to use, e.g. pick one:
# (may require some fiddling and tweaking to get it working correctly)
#
# xfce4-session &
# lxqt-session &
# gnome-session &
# kde-session &
#
openbox &

# Start other stuff in the session, e.g. Dropbox so files are synced
dropbox start -i &

```


On my remote computer e.g. at my office I can now trigger this SSH connection that forwards the right TCP ports to my computer where VNC will be running:
```

ssh -c aes128-ctr -C -X -p 2234 -L 5912:192.168.1.8:5902 myuser@my.ddns.network.address.at.home

```

What these parameters do:
[LIST]
[*]-c aes128-ctr  <== we pick AES 128-bit as crypto key so the connection is way faster
[*]-C  <== enable data compression so we get a bit more speed
[*]-X  <== enable X11 forwarding so we could execute GUI stuff remotely even without VNC
[*]-p 2234  <== Use this non-standard port 2234 for my SSH connection instead of the standard 22
[*]-L 5912:192.168.1.8:5902  <== open up port 5912 (VNC:12) on this side and forward it to VNC:2 on the remote side inside my home network
[/LIST]

To start that desktop I issue this command after I am logged in with the SSH command above:
```

vncserver :2 -depth 16 -geometry 1920x1080

```

And now I can open the local TigerVNC client and perform a VNC session with this target:
```
localhost:12
```

... and I get my VNC:2 session at home. And the speed is very decent.


I hope this helps you?

---

### Post by ActionParsnip on 2020-08-27
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

---

### Post by TheFu on 2020-08-27
Just a guess, but are you using Wayland?

I switched to **x2go** years ago and never had issues with secure, remote access from 5 continents. x2go feels 2-3x faster than any RDP/VNC solution and uses ssh tunnels for network encryption and connection authentication.  Much better than any of the other options, IMHO.

You can use synaptic to "fix broken packages" and to uncover any "held" packages. These are usually caused by admin error, installing a .deb file which has specific dependencies.

---

### Post by kentaylor2525 on 2020-08-27
Thanks  scorp123,

Perhaps the issue is with the Mate desktop. Let me take your xstartup script and compare it with mine and see if I can get something to work. This file has always been a mystery to me all the years I have been using VNC.  I have always taken various samples and tweaked something which worked. Sort of like JCL on MVS for those who remember such a thing. I only knew 3 people who could write JCL from scratch and only one who did. The standard practice was to take an existing JCL file as a starting point and modify it :p

Thanks          ActionParsnip,

I have looked at that page on DigitalOcean. However, it seems to be xfce centric. Again I need to tweak xstartup and see what I can do.

Thanks          TheFu,

I seem to be running x11 ```
ken@t29:~$ loginctl
SESSION  UID USER SEAT  TTY  
    705 1000 ken        pts/1
     c2 1000 ken  seat0      

2 sessions listed.
ken@t29:~$ loginctl show-session c2 -p Type
Type=x11
```

I have used x2go. As I recall the issue I had was working with multiple remote headless servers at the same time. The viewer interface was somewhat cumbersome.

I do not think I can fix the broken package as per the message the package I need does not exist for my environment.

Ken

---

