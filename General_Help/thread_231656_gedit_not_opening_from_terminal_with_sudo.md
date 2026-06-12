---
title: "gedit not opening from terminal with sudo"
date: 2006-08-07
forum: General Help
---

### Post by jordanau on 2006-08-07
Gedit will not open from the terminal win I use the sudo command. It will open without sudo. 

gedit file permissions -rwxr-xr-x

btw, no error message, the command "works" but gedit does not run graphically

---

### Post by jordilin on 2006-08-07
You should use gksudo instead of sudo

---

### Post by jordanau on 2006-08-07
When I do gksudo gedit

(gedit:15905): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by aysiu on 2006-08-07
> **jordanau said:**
> When I do gksudo gedit

(gedit:15905): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
That's fine. Does it actually open?
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jordanau on 2006-08-07
no it does not, it opened once a few hours ago that way and I had to force quit it. Doesn't open at all now

---

### Post by aysiu on 2006-08-07
What about if you do this? ```
sudo -s
gedit
```

---

### Post by jordanau on 2006-08-07
```
jordan@jordan-desktop:~$ sudo -s
groot@jordan-desktop:~# gedit
root@jordan-desktop:~#

```

nothing happened at all. And just double checked, it opens fine with non-root user

---

### Post by aysiu on 2006-08-07
Let me make sure I'm understanding this.

When you say "nothing happened at all," you mean not only did Gedit not launch, but there were no error messages, and the terminal just went to the next line (that's what appears to have happened).

That's really strange. When you're at the ```
root@jordan-desktop
``` prompt, can you launch any command successfully? I mean, can you launch something besides *gedit*, or do all commands fail? Try, for example, typing ```
gdmsetup
```

---

### Post by jordilin on 2006-08-07
> **aysiu said:**
> What about if you do this? ```
sudo -s
gedit
```

If I'm not wrong, you can't execute gedit being root. You must use it by means of gksudo.
If I do
```
sudo -i
```
I enter in a root console, then
```
gedit
```
nothing happens.

---

### Post by aysiu on 2006-08-07
You should be able to do all three of these methods:

1. ```
gksudo gedit
```
2. ```
sudo gedit
```
3. ```
sudo -i
gedit
```

1. Is the preferred method but it will give you an "error."
2. Is the most often recommended way, but it's not "correct."
3. Is the least often recommended way, but it should work as well.

---

### Post by jordanau on 2006-08-07
```
jordan@jordan-desktop:~$ sudo -s
Password:
root@jordan-desktop:~# gdmsetup


```

aha we are getting somewhere (and I am a bit ashamed to have not checked it) It just sat and blinked and I had to break it. I've had to do the same thing with gedit. 

sudo chmod worked a little earlier, so maybe it is only with graphical software from root?


```

 init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9472;&#9472;4*[{NetworkManager}]
     &#9500;&#9472;NetworkManagerD
     &#9500;&#9472;acpid
     &#9500;&#9472;at-spi-registry
     &#9500;&#9472;atd
     &#9500;&#9472;beagled&#9472;&#9516;&#9472;beagled-helper&#9472;&#9472;&#9472;5*[{beagled-helper}]
     &#9474;         &#9492;&#9472;7*[{beagled}]
     &#9500;&#9472;2*[bonobo-activati]
     &#9500;&#9472;clock-applet&#9472;&#9472;&#9472;{clock-applet}
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dd
     &#9500;&#9472;deskbar-applet&#9472;&#9472;&#9472;2*[{deskbar-applet}]
     &#9500;&#9472;dhcdbd&#9472;&#9472;&#9472;dhclient
     &#9500;&#9472;2*[esd]
     &#9500;&#9472;events/0
     &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;{evolution-alarm}
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;2*[{evolution-data-}]
     &#9500;&#9472;firefox-bin&#9472;&#9516;&#9472;mplayer&#9472;&#9472;&#9472;mplayer
     &#9474;             &#9492;&#9472;5*[{firefox-bin}]
     &#9500;&#9472;2*[gconfd-2]
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9472;&#9472;ssh-agent
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-cups-icon
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-netstatus
     &#9500;&#9472;gnome-panel&#9472;&#9472;&#9472;{gnome-panel}
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;2*[gedit]
     &#9474;                &#9500;&#9472;bash&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo
     &#9500;&#9472;gnome-vfs-daemo&#9472;&#9472;&#9472;{gnome-vfs-daemo}
     &#9500;&#9472;gnome-volume-ma
     &#9500;&#9472;gweather-applet
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-keyb
     &#9474;                    &#9492;&#9472;2*[hald-addon-stor]
     &#9500;&#9472;hcid
     &#9500;&#9472;hpiod
     &#9500;&#9472;khelper
     &#9500;&#9472;khpsbpkt
     &#9500;&#9472;kjournald
     &#9500;&#9472;klogd
     &#9500;&#9472;knodemgrd_0
     &#9500;&#9472;krfcommd
     &#9500;&#9472;ksoftirqd/0
     &#9500;&#9472;kswapd0
     &#9500;&#9472;kthread&#9472;&#9516;&#9472;aio/0
     &#9474;         &#9500;&#9472;ata/0
     &#9474;         &#9500;&#9472;ata_hotplug/0
     &#9474;         &#9500;&#9472;kacpid
     &#9474;         &#9500;&#9472;kblockd/0
     &#9474;         &#9500;&#9472;kgameportd
     &#9474;         &#9500;&#9472;khubd
     &#9474;         &#9500;&#9472;kseriod
     &#9474;         &#9500;&#9472;2*[pdflush]
     &#9474;         &#9500;&#9472;scsi_eh_0
     &#9474;         &#9492;&#9472;scsi_eh_1
     &#9500;&#9472;mapping-daemon
     &#9500;&#9472;mdadm
     &#9500;&#9472;metacity
     &#9500;&#9472;mixer_applet2
     &#9500;&#9472;3*[mplayer]
     &#9500;&#9472;nautilus&#9472;&#9472;&#9472;{nautilus}
     &#9500;&#9472;notification-da
     &#9500;&#9472;sdpd
     &#9500;&#9472;shpchpd_event
     &#9500;&#9472;syslogd
     &#9500;&#9472;trashapplet&#9472;&#9472;&#9472;{trashapplet}
     &#9500;&#9472;udevd
     &#9500;&#9472;watchdog/0
     &#9500;&#9472;wpa_supplicant
     &#9492;&#9472;xchat&#9472;&#9472;&#9472;{xchat}

```

anything funny there??

---

### Post by aysiu on 2006-08-07
Well, I think you've done a pretty good job at diagnosing the problem. If *sudo chmod* worked, it probably is a problem with graphical applications. Unfortunately, I don't know what the solution is.

---

### Post by jordanau on 2006-08-07
```

jordan@jordan-desktop:~$ sudo -i
root@jordan-desktop:~# gedit
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.
root@jordan-desktop:~#

```

hmmm that is a bit more information at least.

I agree about graphical applications, but why only when root user?

EDIT:

synaptic will open from gnome

---

### Post by aysiu on 2006-08-07
Well, [you're not alone](http://ubuntuforums.org/showthread.php?t=187912).

I'm not sure, but [this thread](http://ubuntuforums.org/showthread.php?t=197376) might help you.

---

### Post by JmSchanck on 2006-08-07
Hey I was able to replicate this same error by doing a force quit on a gedit session I had started as root. So to diagnose it I ran
```

$ sudo -s
$ strace gedit

```
and I noticed it hung right after trying to open a socket /tmp/gedit.root.*somenumber*. I cd'ed into /tmp and removed the file and then I was able to open gedit as root again. 

Hope that helps

-John

---

### Post by jordanau on 2006-08-07
That fixed the problem thank all of you for you help. Is that a bug?? Should I submit it?

---

