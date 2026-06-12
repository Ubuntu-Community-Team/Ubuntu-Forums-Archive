---
title: "Xtightvnc won't allow graphical sudo commands [gparted] after 19.10 update"
date: 2019-10-21
forum: General Help
---

### Post by r0d3nt on 2019-10-21
Hi Everyone,

I updated my installation to Ubuntu 19.10, and I used to be able to do sudo gparted to launch gparted through the Xtightvnc instance that I have running on my server with 19.04, but after the 19.10 update I get the following.

[FONT=courier new]```
uquevedo@bigmac:~$ sudo gparted[sudo] password for uquevedo: 
Unit boot.mount does not exist, proceeding anyway.
Unit tmp.mount does not exist, proceeding anyway.
Client is not authorized to connect to Server
(gpartedbin:9038): Gtk-WARNING **: 16:18:49.100: cannot open display: :1
```[/FONT]

I've done some research and there was mention about making it so that root was an authorized user of the X session, but that doesn't seem to work.

Here's the contents of the systemd script I created for this VNC service:
```
uquevedo@bigmac:/etc/systemd/system$ cat vncserver@.service 
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target


[Service]
Type=forking
User=uquevedo
Group=uquevedo
WorkingDirectory=/home/uquevedo


PIDFile=/home/uquevedo/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1152x864 :%i
ExecStop=/usr/bin/vncserver -kill :%i


[Install]
WantedBy=multi-user.target
```
Things appear to be running properly:
```
uquevedo@bigmac:/etc/systemd/system$ sudo systemctl status vncserver@1 -l
&#9679; vncserver@1.service - Start TightVNC server at startup
   Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2019-10-21 16:04:34 PDT; 16min ago
 Main PID: 1277 (Xtightvnc)
    Tasks: 333 (limit: 4915)
   Memory: 1.7G
   CGroup: /system.slice/system-vncserver.slice/vncserver@1.service
           &#9500;&#9472;1277 Xtightvnc :1 -desktop X -auth /home/uquevedo/.Xauthority -geometry 1152x864 -depth 24 -rfbwait 120000 -rfbauth /home/uqueve
           &#9500;&#9472;1976 mate-session
           &#9500;&#9472;2004 dbus-launch --exit-with-session mate-session
           &#9500;&#9472;2014 /usr/bin/dbus-daemon --syslog --fork --print-pid 5 --print-address 7 --session
           &#9500;&#9472;2135 /usr/lib/at-spi2-core/at-spi-bus-launcher
           &#9500;&#9472;2190 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 3
           &#9500;&#9472;2207 /usr/lib/dconf/dconf-service
           &#9500;&#9472;2284 gnome-keyring-daemon --start
           &#9500;&#9472;2331 /usr/bin/mate-settings-daemon
           &#9500;&#9472;2334 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
           &#9500;&#9472;2418 marco
           &#9500;&#9472;2424 /usr/lib/gvfs/gvfsd
           &#9500;&#9472;2438 /usr/lib/gvfs/gvfsd-fuse /home/uquevedo/.cache/gvfs -f -o big_writes
           &#9500;&#9472;2541 mate-panel
           &#9500;&#9472;2632 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
           &#9500;&#9472;2654 caja
           &#9500;&#9472;2699 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
           &#9500;&#9472;2718 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
           &#9500;&#9472;2747 mate-maximus
           &#9500;&#9472;2764 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
           &#9500;&#9472;2787 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
           &#9500;&#9472;2790 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
           &#9500;&#9472;2801 /usr/bin/dyn_updater
           &#9500;&#9472;2823 /usr/libexec/evolution-data-server/evolution-alarm-notify
           &#9500;&#9472;2842 update-notifier
           &#9500;&#9472;2852 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
           &#9500;&#9472;2872 /usr/bin/python3 /usr/share/system-config-printer/applet.py
           &#9500;&#9472;2890 /usr/bin/xscreensaver -no-splash
           &#9500;&#9472;2898 nm-applet
           &#9500;&#9472;2946 /usr/libexec/evolution-source-registry
           &#9500;&#9472;3168 /usr/libexec/evolution-calendar-factory
           &#9500;&#9472;3176 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
           &#9500;&#9472;3196 /usr/lib/gvfs/gvfs-afc-volume-monitor
           &#9500;&#9472;3212 /usr/lib/gvfs/gvfs-goa-volume-monitor
           &#9500;&#9472;3221 /usr/lib/gvfs/gvfs-mtp-volume-monitor
           &#9500;&#9472;3274 /usr/lib/mate-panel/notification-area-applet
           &#9500;&#9472;3276 /usr/lib/mate-panel/clock-applet
           &#9500;&#9472;3278 /usr/lib/mate-panel/wnck-applet
           &#9500;&#9472;3295 /usr/libexec/evolution-addressbook-factory
           &#9500;&#9472;3344 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
           &#9500;&#9472;3810 /usr/bin/dyn_updater --daemon start
           &#9500;&#9472;4318 /usr/lib/gvfs/gvfsd-metadata
           &#9500;&#9472;7828 mate-terminal
           &#9500;&#9472;7836 bash
           &#9500;&#9472;7848 iperf3 -s -i 10
           &#9500;&#9472;7849 /opt/google/chrome/chrome
           &#9500;&#9472;7856 cat
           &#9500;&#9472;7857 cat
           &#9500;&#9472;7871 /opt/google/chrome/chrome --type=zygote --enable-crash-reporter=03bd33fe-1a45-4ab3-b688-9db6e9f543db,
           &#9500;&#9472;7874 /opt/google/chrome/nacl_helper
           &#9500;&#9472;7877 /opt/google/chrome/chrome --type=zygote --enable-crash-reporter=03bd33fe-1a45-4ab3-b688-9db6e9f543db,
           &#9500;&#9472;7899 /opt/google/chrome/chrome --type=utility --field-trial-handle=8591103244298123280,12816234845203334700,131072 --lang=en-US 
           &#9500;&#9472;7953 /opt/google/chrome/chrome --type=gpu-process --field-trial-handle=8591103244298123280,12816234845203334700,131072 --enable-
           &#9500;&#9472;7955 /opt/google/chrome/chrome --type=broker
           &#9500;&#9472;7976 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --lang=en-US
           &#9500;&#9472;7978 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --lang=en-US
           &#9500;&#9472;7990 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --lang=en-US
           &#9500;&#9472;7995 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --lang=en-US
           &#9500;&#9472;8014 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --lang=en-US
           &#9500;&#9472;8148 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --disable-gp
           &#9500;&#9472;8160 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --disable-gp
           &#9500;&#9472;8315 /opt/google/chrome/chrome --type=utility --field-trial-handle=8591103244298123280,12816234845203334700,131072 --lang=en-US 
           &#9500;&#9472;8554 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --disable-gp
           &#9500;&#9472;8640 /opt/google/chrome/chrome --type=renderer --field-trial-handle=8591103244298123280,12816234845203334700,131072 --disable-gp
           &#9500;&#9472;8741 bash
           &#9500;&#9472;8919 bash
           &#9500;&#9472;9309 sudo systemctl status vncserver@1 -l
           &#9500;&#9472;9310 systemctl status vncserver@1 -l
           &#9492;&#9472;9311 pager


Oct 21 16:15:30 bigmac sudo[8771]: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 21 16:15:41 bigmac sudo[8771]: pam_unix(sudo:session): session closed for user root
Oct 21 16:18:48 bigmac sudo[8928]: uquevedo : TTY=pts/3 ; PWD=/home/uquevedo ; USER=root ; COMMAND=/usr/sbin/gparted
Oct 21 16:18:48 bigmac sudo[8928]: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 21 16:18:49 bigmac sudo[8928]: pam_unix(sudo:session): session closed for user root
Oct 21 16:20:57 bigmac sudo[9305]: uquevedo : TTY=pts/2 ; PWD=/etc/systemd/system ; USER=root ; COMMAND=/bin/systemctl status vncserver@1
Oct 21 16:20:57 bigmac sudo[9305]: pam_unix(sudo:session): session opened for user root by (uid=0)
Oct 21 16:21:01 bigmac sudo[9305]: pam_unix(sudo:session): session closed for user root
Oct 21 16:21:07 bigmac sudo[9309]: uquevedo : TTY=pts/2 ; PWD=/etc/systemd/system ; USER=root ; COMMAND=/bin/systemctl status vncserver@1 -l
Oct 21 16:21:07 bigmac sudo[9309]: pam_unix(sudo:session): session opened for user root by (uid=0)
```

Here's the contents of my xstartup:
```
uquevedo@bigmac:~/.vnc$ cat xstartup
#!/bin/sh


# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#unset DBUS_SESSION_BUS_ADDRESS
#exec /etc/X11/xinit/xinitrc
#/usr/bin/mate-session &


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession
mate-session &
```

Any ideas on how I can get graphical type commands through sudo to work again?

---

### Post by Skaperen on 2019-10-21
try the command:  [COLOR=#0000cd][FONT=courier new]**xhost +root**[/FONT][/COLOR]

---

### Post by r0d3nt on 2019-10-22
Here's what I get:
```
uquevedo@bigmac:~$ xhost +root
xhost:  bad hostname "root"
```

---

### Post by r0d3nt on 2019-10-30
Does anyone have any suggestions on this?  This is a headless server that I access via VNC [Xtightvnc] occasionally to work with external hard drives from time to time and I'd really like to be able to use gparted again in a graphical way.

---

### Post by makem2 on 2019-11-09
I just tried and got a different error message:

```

makem@ubuntu:~$ sudo gparted
Unit boot.mount does not exist, proceeding anyway.
Unit tmp.mount does not exist, proceeding anyway.

(gpartedbin:5156): Gtk-WARNING **: 11:53:58.348: cannot open display: :1
makem@ubuntu:~$

```

Maybe that will give you another route to check out (I have other problems atm) Btw, are your wifi setting greyed out too?

I see you started the thread with this error :(

---

### Post by r0d3nt on 2019-11-09
I already did try running it with sudo:
```
uquevedo@bigmac:~$ sudo gparted[sudo] password for uquevedo: 
Unit boot.mount does not exist, proceeding anyway.
Unit tmp.mount does not exist, proceeding anyway.
Client is not authorized to connect to Server
(gpartedbin:27786): Gtk-WARNING **: 07:26:54.861: cannot open display: :1
```
This problem only started occurring after the upgrade to 19.10.

This worked properly in 19.04.

I don't have the Wi-Fi enabled on this system, it is hard wired.

The problem seems related to a permissions issue of some sort with the X session, I'm just not sure how.

I'm also running Mate as the desktop environment.

---

### Post by r0d3nt on 2019-12-27
Hi Everyone,

I finally got this resolved.

I added xhost + to my xstartup and restarted the vnc server, and I can launch gparted now.

---

