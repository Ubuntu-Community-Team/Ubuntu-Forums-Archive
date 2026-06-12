---
title: "booting into text mode &amp; starting X server manually"
date: 2008-01-29
forum: General Help
---

### Post by MystaMax on 2008-01-29
Hello, I've done some research on booting into text mode permanently, but wanted to get second opinion on doing it the "correct" or "most appropriate" way on ubuntu/debian. I want to start X server only when needed.

The [1st]("http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html") I saw was:

```

sudo update-rc.d -f gdm remove

```[Someone]("http://www.debianadmin.com/howto-boot-debian-in-text-mode-instead-of-graphical-mode-gui.html#comment-38086") argued that this was not the the best way for administrators to go about booting text mode. That, "update-rc" was for package maintainers scripts to install startup links.

They recommended:

```

mv /etc/rc2.d/S30gdm /etc/rc2.d/k70gdm

```The man pages for update-rc.d also state to rename a file to disable a service.

What do you think? What other options do I have? Also, how would manually I start X server again so I connect remotely, and then use VNC to connect.

I'm running 6.06.2 LTS Server.

Thanks.

---

### Post by taurus on 2008-01-29
Or you can just remove gdm

```
sudo apt-get remove gdm
```
And if you want to start Gnome, just run

```
startx
```

---

### Post by MystaMax on 2008-01-29
ok, I never thought about that. Seems simple enough. Can I run startx over ssh, and then VNC into the server?

---

### Post by MystaMax on 2008-01-30
Ok, I tried removing gdm on a test machine (inside VMware) and did as expected, lauched w/o a gui into text mode. That's what I wanted.

But, I would like  the ability to access the server via a GUI remotely from time to time. I cannot launch xserver (using the startx command) via ssh.

Here is a typical situation.

1. server boots into text mode
2. I somehow start the xserver processes remotely (probably via ssh)
3. I then use VNC to perform necessary tasks
4. I stop stop xserver remotely (clearing out unnecessary processes)

Right now, I'm thinking uninstalling GDM is not the way I want to go.

Any suggestions from anyone?

---

### Post by ~LoKe on 2008-01-30
```
sudo apt-get install sysv-rc-conf
```
```
sudo sysv-rc-conf
```
Disable GDM by removing the X from all runlevels (press space to remove the x).

GDM will not start when the system boots, but typing "sudo gdm" will start it.

---

### Post by MystaMax on 2008-01-30
Great! your suggestion has gotten me where I want to be. Now, all I have to test is VNC after starting GDM. Thanks, I'll reply w/ the results.

---

### Post by MystaMax on 2008-01-30
Ok, looks like I'll have to follow this [VNC w/ resumable sessions tutorial]("http://ubuntuforums.org/showthread.php?t=122402"), so that after I start GDM, I can use VNC to connect, and start a new session.

I'm headed down the right path, right?

---

