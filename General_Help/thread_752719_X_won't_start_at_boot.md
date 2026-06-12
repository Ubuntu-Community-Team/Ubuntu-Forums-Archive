---
title: "X won't start at boot"
date: 2008-04-11
forum: General Help
---

### Post by Hegh on 2008-04-11
I don't remember what I did to cause this, but X no longer starts when I boot my machine. It is perfectly happy to start if I log in on the command line and type "startx", but for some reason I don't get the graphical login anymore. I tried starting KDM, but it said it is already started. Is there some other service that may have somehow disappeared?

I am quite comfortable with the command line (I'm a developer for embedded Linux systems), but I'm just not sure where to look for the solution to this problem. Feel free to suggest anything, I'll be able to follow it.

---

### Post by kyphi on 2008-04-11
Currently when you start X via the command line you are doing so as root and not as user.  The system interprets X as belonging to root.

The last time that happened to me I had to locate the Xauthority file (~/.Xauthority) and change the permissions.  After that everything was back to normal.

---

### Post by pointone on 2008-04-11
Does hitting Ctrl+Alt+F7 take you to the GUI?

What happens when you run "sudo /etc/init.d/kdm restart"?

---

### Post by Hegh on 2008-04-11
Virtual TTY 7 is not connected to a GUI (nor are 8-12, although not sure how many of those ever exist anyway). Restarting KDM didn't do anything.

As for .Xauthority, I have no idea how to deal with the file. It is owned by me and is rw for me only.

The problem is that X does not start until I run "startx". Is there some X-related service that might start it? The only X-related services listed by my machine are "x11-common" and "xserver-xorg-input-wacom". Are there any others that I am missing?

---

### Post by kyphi on 2008-04-12
Your Xauthority file's permissions are OK.

You could try as root:

1.  dpkg-reconfigure xserver-xorg

2.  go to /etc/X11 and compare your xorg.conf file with your backed up xorg.conf files.  Substitute the most recent one.

---

### Post by Hegh on 2008-04-12
Reconfiguring X didn't work. It only changed my xorg.conf file, which was fine (X is quite happy to start when I type startx, there are no errors and I even have Compiz Fusion running for some pretty desktop effects).

What starts the graphical boot system? I removed "splash" from the command line, but if I recall, putting it back in didn't solve the problem. I'll try again on my next reboot, but until then, more suggestions are quite welcome.

---

### Post by pointone on 2008-04-12
Make double sure KDM is started in the default runlevel. Check to see if "/etc/rc2.d/S##KDM" exists. If not, run:

```
sudo update-rc.d kdm defaults
```

---

### Post by kyphi on 2008-04-12
When you use "# dpkg-reconfigure xserver-xorg", to the question "Activate Kernel Framebuffer Device Interface" you need to select "No".   Then reboot.

---

### Post by Hegh on 2008-04-14
Pretty sure I did select 'No' for that, and I definitely rebooted to test. But I'm pretty sure that the problem is not in my xorg.conf file. And KDM is definitely starting in the default runlevel, since it is running when the machine finishes booting, there just isn't a graphical terminal anywhere (not sure how that works, since I thought KDM required X to be running...) :confused:

---

### Post by pointone on 2008-04-14
You could try simply reinstalling the kubuntu-desktop metapackage:

```
sudo apt-get install --reinstall kubuntu-desktop
```

---

### Post by forrestcupp on 2008-04-14
> **pointone said:**
> You could try simply reinstalling the kubuntu-desktop metapackage:

```
sudo apt-get install --reinstall kubuntu-desktop
```

Definitely try this next.

If you're still having trouble after that, post the results of
```
cat /boot/grub/menu.lst
```

---

### Post by Hegh on 2008-04-18
Before doing that, could someone send me a copy of their /etc/inittab file? I don't seem to have one, not sure what might have deleted it. I think that might be the cause, actually.

---

### Post by JohnFH on 2008-04-18
I don't have this file either, so that's unlikely to be the cause.

What's the permissions on /usr/bin/X11/xorg?
Try:
sudo chmod +s /usr/bin/X11/xorg 

Also check the X log files in /var/log/Xorg.*.log

---

### Post by pointone on 2008-04-18
inittab was replaced by [Upstart]("http://upstart.ubuntu.com/").

---

