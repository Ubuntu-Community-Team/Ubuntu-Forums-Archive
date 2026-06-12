---
title: "Xubuntu 14.04 LTS, startx/gdm default logins fail"
date: 2017-03-29
forum: General Help
---

### Post by mathog on 2017-03-29
A 32 bit Xubuntu 14.04 LTS machine is set to boot to the text prompt.

After logging in at the console, it will start X11 and get into the xfce desktop normally
with 

```
startxfce

```
However, with this command

```
startx 

```
it just gets to a blank screen with a cursor icon.  It starts some pieces of xfce but does not make it all the way to a working desktop.  

Why???  This is what ps -ef shows 

```
root      3546  2542  0 12:00 tty1     00:00:00 /bin/sh /usr/bin/startx
root      3563  3546  0 12:00 tty1     00:00:00 xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc :0 -auth /tmp/serverauth.2hTaatU6zM
root      3564  3563  0 12:00 tty7     00:00:00 /usr/bin/X -nolisten tcp :0 -auth /tmp/serverauth.2hTaatU6zM
root      3566  3563  0 12:00 tty1     00:00:00 /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch x-session-manager
root      3625  3566  0 12:00 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch x-session-manager
root      3629  3566  0 12:00 tty1     00:00:00 xfwm4
root      3632     1  0 12:00 tty1     00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch x-session-manager
root      3633     1  0 12:00 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      3644     1  0 12:00 ?        00:00:00 /usr/bin/ibus-daemon --daemonize --xim
root      3656     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfsd
root      3660     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/0/gvfs -f -o big_writes
root      3670  3644  0 12:00 ?        00:00:00 /usr/lib/ibus/ibus-dconf
root      3671  3644  0 12:00 ?        00:00:00 /usr/lib/ibus/ibus-ui-gtk3
root      3673     1  0 12:00 ?        00:00:00 /usr/lib/ibus/ibus-x11 --kill-daemon
root      3678     1  0 12:00 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
root      3682  3678  0 12:00 ?        00:00:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
root      3687     1  0 12:00 ?        00:00:00 /usr/lib/i386-linux-gnu/xfce4/xfconf/xfconfd
root      3690     1  0 12:00 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
root      3697  3644  0 12:00 ?        00:00:00 /usr/lib/ibus/ibus-engine-simple
```

If X11 is not yet running, the command

```
service gdm start

```
puts up the login screen, and the one "normal" user is shown.  If the "system default" session is selected and the password supplied
it brings up a blank desktop, just like "startx" did.  Selecting instead "xfce session" allows a normal login to that desktop.  This account can login and out multiple times without problems.  This user's files are on the local disk.

I'm guessing that whatever is wrong with "startx" is also causing "system default" to fail.

"root" and the NIS users are not listed.  If "not listed" on the login screen is clicked and a NIS user's credentials are entered that name is added to the list, and then it can login successfully with "xfce session".  As before, "default session" is a dead end.  However
it only works ONCE.  Then it has the blank screen problem again.  Go to ~user and do

```
rm -rf .cache
rm -rf .config

```
and it will allow one more login, then it jams again.  Super annoying!  The NIS user's files are NFS mounted, but I'm not seeing anything to indicate a problem writing or reading the mounted directory.

Logging in through gdm doesn't ever work for root - enter the credentials and it goes to the blank desktop deadend, and root is never added to the login list.

So what do I need to change to make "startx" and "system default" work, and login to the xfce desktop?
Why are NIS users cursed???

(Not being able to login directly as root isn't that big a problem.)

Thanks

---

### Post by mathog on 2017-03-29
The display is using nouveau.  The nvidia driver was installed at one point but it was completely removed. lsmod shows that the nouveau driver is the one in use.

---

### Post by mörgæs on 2017-03-29
Xubuntu 14.04 has only a month left of support. Have you considered a fresh install of 16.04.2?

---

### Post by mathog on 2017-03-29
Actually I'm updating the machine now, but wanted to get the X11 server at least partially working again before doing that.  With any luck maybe after the upgrade the problem will automagically be fixed.  (I'm not holding my breath though, since the upgrade is having lots of problems.)

---

### Post by mörgæs on 2017-03-30
They often do. A fresh install every other year keeps the doctor away.

---

