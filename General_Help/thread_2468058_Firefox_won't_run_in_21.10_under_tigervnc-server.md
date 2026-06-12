---
title: "Firefox won't run in 21.10 under tigervnc-server"
date: 2021-10-17
forum: General Help
---

### Post by madbrain on 2021-10-17
This was working under 20.04 . Upgraded to 21.04, then 21.10. It is no longer working.
Other X programs such as xcalc or gnome-terminal do run.

madbrain@server10g:~/Desktop$ firefox
Error: cannot open display: :1.0
madbrain@server10g:~/Desktop$ xcalc
madbrain@server10g:~/Desktop$ gnome-terminal
madbrain@server10g:~/Desktop$ cat /etc/systemd/system/vncserver@.service 
[Unit]
Description=TigerVNC server
After=syslog.target network.target

[Service]
Type=forking
User=madbrain
PIDFile=/home/madbrain/.vnc/%H:5901.pid
ExecStartPre=-/usr/bin/vncserver -kill :1 > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -geometry 3840x2160 -localhost no :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
madbrain@server10g:~/Desktop$ cat ~/.vnc/xstartup
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
autocutsel -s CLIPBOARD -fork
dbus-launch xfce4-session
madbrain@server10g:~/Desktop$ apt list --installed | grep -i vnc

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

tigervnc-common/impish,now 1.11.0+dfsg-2ubuntu1 amd64 [installed,automatic]
tigervnc-standalone-server/impish,now 1.11.0+dfsg-2ubuntu1 amd64 [installed]
madbrain@server10g:~/Desktop$ 

Is there a workaround for this ? Not being able to run a browser is pretty bad.

Firefox does run fine on the local display. Just won't run on remote display anymore.

---

### Post by TheFu on 2021-10-17
Did you try to disable the default firefox setting that uses direct GPU access?

When I try to run firefox remotely using X11, I get this:
```
$ ssh -X u2110 firefox
/usr/bin/xauth:  file /home/jp/.Xauthority does not exist
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Unable to init server: Broadway display type not supported: localhost:10.0
Error: cannot open display: localhost:10.0
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
```
I think that is due to firefox being a snap package in 21.10.  I think I know a workaround. 

```
$ ssh -X u2110  "XAUTHORITY=$HOME/.Xauthority firefox "
```
That works here on my 21.10 play system from a remote system.

---

### Post by deadflowr on 2021-10-17
*Thread moved to** General Help***

The development phase of 21.10 is over.
It's now a stable release.

---

### Post by madbrain on 2021-10-17
> **TheFu said:**
> Did you try to disable the default firefox setting that uses direct GPU access?


I had to look up how to do that. Started firefox locally on the Windows host. Went to General/Advanced settings. Turned off GPU acceleration.
Exited, and then tried to restart firefox inside VNC client. Unfortunately, no change.

> 
When I try to run firefox remotely using X11, I get this:
```
$ ssh -X u2110 firefox
/usr/bin/xauth:  file /home/jp/.Xauthority does not exist
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Unable to init server: Broadway display type not supported: localhost:10.0
Error: cannot open display: localhost:10.0
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
```
I think that is due to firefox being a snap package in 21.10.  I think I know a workaround. 

```
$ ssh -X u2110  "XAUTHORITY=$HOME/.Xauthority firefox "
```
That works here on my 21.10 play system from a remote system.

I think that's a different problem you are running into. I am not using SSH, or an X11 remote connection. The client is a Windows host, without an X server.
I am using Tiger VNC server on the Linux host, and RealVNC client on the Windows host.

I typed the following inside of the terminal in the VNC client. Unfortunately, no change either.

madbrain@server10g:~$ export XAUTHORITY=$HOME/.Xauthority
madbrain@server10g:~$ firefox
Error: cannot open display: :1.0
madbrain@server10g:~$ 

I am not sure what to do at this point, besides revert to previous versions of Ubuntu.

---

### Post by madbrain on 2021-10-17
> **madbrain said:**
> 
I am not sure what to do at this point, besides revert to previous versions of Ubuntu.

I reverted to 21.04 from an Acronis backup. The browser works fine in VNC server now. This is a 21.10 regression.

---

### Post by guiverc on 2021-10-17
Are (or were?) you using the `firefox` as a *deb* or *snap* package?

If you run `update-manager`, or performed `do-release-upgrade` from mid-*beta* cycle or later (with Ubuntu Desktop; not *flavors*), the *deb* package of `firefox` gets removed and replaced by a *snap* package.

There are some known issues with the *snap* package; the reported ones are being worked on so issues get fixed (before 22.04/*jammy* at a minimum).

For *flavors* the firefox package remains a *deb* package; **however** it'll change to *snap* also if `update-manager` is run for any reason.  `update-manager` is not installed for all *flavors*; but tends to be there for GTK+ *flavors* (so it won't be found in Lubuntu, Kubuntu, Ubuntu Studio).

If using the *deb* package I'd not expect any changes.

FYI:   N0rbert has documented that you can stop `update-manager` from converting the *deb* package to snap if you mark the package as manually-installed, ie. `apt-mark manual`

---

### Post by madbrain on 2021-10-17
> **guiverc said:**
> Are (or were?) you using the `firefox` as a *deb* or *snap* package?

If you run `update-manager`, or performed `do-release-upgrade` from mid-*beta* cycle or later (with Ubuntu Desktop; not *flavors*), the *deb* package of `firefox` gets removed and replaced by a *snap* package.

There are some known issues with the *snap* package; the reported ones are being worked on so issues get fixed (before 22.04/*jammy* at a minimum).

For *flavors* the firefox package remains a *deb* package; **however** it'll change to *snap* also if `update-manager` is run for any reason.  `update-manager` is not installed for all *flavors*; but tends to be there for GTK+ *flavors* (so it won't be found in Lubuntu, Kubuntu, Ubuntu Studio).

If using the *deb* package I'd not expect any changes.

I performed do-release-upgrade many times. I went from 18.04 to 20.04 to 21.04 to 21.10 . It broke between 21.04 and 21.10 .
I believe firefox got installed as a snap package.

Is there a workaround, short of rolling back to 21.04 ?

---

### Post by TheFu on 2021-10-17
> **madbrain said:**
> I reverted to 21.04 from an Acronis backup. The browser works fine in VNC server now. This is a 21.10 regression.

Is your 21.10 using Wayland or X11?
[https://github.com/TigerVNC/tigervnc/issues/158](https://github.com/TigerVNC/tigervnc/issues/158)

Going beyond what I actually know .... 

Looks like Wayland users may have to use WayVNC - or am I misreading that?

My ssh -X test above was into a Wayland running 21.10, btw.

Firefox in 21.10 **is** using a snap package. I don't know if other versions will be possible or not from Canonical.  When they did the same with Chromium in 20.04, other people created a deb package and multiple PPAs became available.  I know the ~/.Xauthority file stuff worked in 20.04 for Chromium.

I don't use VNC here.  My normal remote desktop over the internet is x2go, which doesn't support Wayland at all.  On the LAN, I use ssh -X almost always, but for play, I'll use virt-viewer with QXL drivers.  I was unable to get virt-viewer working over the LAN into the 21.10 system, but it does work find on the same physical system.

Not sure how this is related, but [https://www.linuxquestions.org/questions/showthread.php?p=6286567](https://www.linuxquestions.org/questions/showthread.php?p=6286567) seems connected, somehow.

---

### Post by monkeybrain20122 on 2021-10-17
Firefox in 21.10 is a snap package though someone reported that both snap and deb versions are installed. So.. just uninstall the snap. I am sure that the .deb is still in the repository since the flavors (like xubuntu or kubuntu) have not switched to snap, now just install FF again with apt if it is not already installed, you should be good to go.

In general, it is super easy to just use the distro agnostic tar ball from Mozilla (to upgrade just click help > about firefox and it will seamlessly upgrade) I don't think it is such a big deal how Ubuntu's default FF is packaged.

---

### Post by madbrain on 2021-10-17
> **monkeybrain20122 said:**
> Firefox in 21.10 is a snap package though someone reported that both snap and deb versions are installed. So.. just uninstall the snap. I am sure that the .deb is still in the repository since the flavors (like xubuntu or kubuntu) have not switched to snap, now just install FF again with apt if it is not already installed, you should be good to go.

In general, it is super easy to just use the distro agnostic tar ball from Mozilla (to upgrade just click help > about firefox and it will seamlessly upgrade) I don't think it is such a big deal how Ubuntu's default FF is packaged.

Thanks. I'm going to stick with older Ubuntu though, since I just saw the release note in 21.10 about a ZFS corruption bug. I have 112TB I can't afford to lose.

---

### Post by guiverc on 2021-10-17
> **madbrain said:**
> I performed do-release-upgrade many times. I went from 18.04 to 20.04 to 21.04 to 21.10 . It broke between 21.04 and 21.10 .
I believe firefox got installed as a snap package.

Is there a workaround, short of rolling back to 21.04 ?

My upgraded systems (Ubuntu, Lubuntu & Xubuntu) all still have `firefox` only as a *deb* package. 

Flavors don't switch from *deb* to *snap*, only Ubuntu Desktop installs too.  However Desktop installs that upgraded pre-*beta* or in the first few days of the *beta* also didn't switch which is why my Ubuntu Desktop install doesn't have it.

Ubuntu 21.10 systems can use either; default is *snap* for Ubuntu Desktop, but default is *deb* package for *flavors*.

My prior comment also mentioned `update-manager`, which IF RUN will convert a *deb* package into a *snap* on 21.10/*impish* **UNLESS **the *firefox* deb package is marked as manually installed ; thus my prior `apt-mark manual` addition to my original post.

```
sudo apt-mark manual firefox
```

Note: I'm involved with a *flavor*, and  testing has largely been with *flavors* since some Ubuntu-MATE users reported their *deb* package of `firefox` being converted (*last friday*).. It was tested & found to prevent Ubuntu-MATE & Xubuntu from switching; I felt no need to test Lubuntu (we don't provide `update-manager` on a default install; and my own primary box which does have it installed has not uninstalled the *deb* package anyway so I've felt no need to test it, or document it on the Lubuntu discourse).

The [issue I'm talking about is this one]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1947501")

---

### Post by madbrain on 2021-10-17
> **guiverc said:**
> My upgraded systems (Ubuntu, Lubuntu & Xubuntu) all still have `firefox` only as a *deb* package. 

Flavors don't switch from *deb* to *snap*, only Ubuntu Desktop installs too.  However Desktop installs that upgraded pre-*beta* or in the first few days of the *beta* also didn't switch which is why my Ubuntu Desktop install doesn't have it.

Ubuntu 21.10 systems can use either; default is *snap* for Ubuntu Desktop, but default is *deb* package for *flavors*.

My prior comment also mentioned `update-manager`, which IF RUN will convert a *deb* package into a *snap* on 21.10/*impish* **UNLESS **the *firefox* deb package is marked as manually installed ; thus my prior `apt-mark manual` addition to my original post.

```
sudo apt-mark manual firefox
```

Note: I'm involved with a *flavor*, and  testing has largely been with *flavors* since some Ubuntu-MATE users reported their *deb* package of `firefox` being converted (*last friday*).. It was tested & found to prevent Ubuntu-MATE & Xubuntu from switching; I felt no need to test Lubuntu (we don't provide `update-manager` on a default install; and my own primary box which does have it installed has not uninstalled the *deb* package anyway so I've felt no need to test it, or document it on the Lubuntu discourse).

The [issue I'm talking about is this one]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1947501")

I am using Ubuntu Desktop. Not sure how firefox got switched from deb to snap, but it did. I never ran update-manager.
I know I ran do-release-upgrade, apt-get update, apt-get upgrade, apt-get dist-upgrade .
I have reverted to Ubuntu 20.04 now. Shouldn't have been playing with the 21 release at all. That'll teach me to use a non-LTS version. The VNC browser bug is annoying. But the known ZFS corruption bug is seriously scary. 21.10 should never have been released as-is. Either the release should have been delayed, or ZFS should have been removed from the release.

---

