---
title: "gparted: Error executing command as another user: No authentication agent found."
date: 2023-11-22
forum: General Help
---

### Post by dieter-erich on 2023-11-22
Hi,
   I have two laptops with ubuntu mate 22.04 with the latest updates. On one gparted works as expected. On the other one it issues the error: "Error executing command as another user: No authentication agent found." I compared the relevant running processes with "ps -ealf | grep polk" yielding the identical output as seen below.

4 S root         651       1  0  80   0 - 61199 -      Nov13 ?        00:00:06 /usr/libexec/polkitd --no-debug
0 S me       1619    1076  0  80   0 - 201097 do_pol Nov13 ?       00:00:00 /usr/lib/x86_64-linux-gnu/polkit-mate/polkit-mate-authentication-agent-1
0 S me    1713620 1406124  0  80   0 -  2396 pipe_r 21:22 pts/2    00:00:00 grep --color=auto polk

what is wrong here?
thanks a lot, D-E

---

### Post by Rubi1200 on 2023-11-25
If you start gparted in the terminal do you get the same error?

---

### Post by yancek on 2023-11-26
How do you start Gparted on both machines?  From some GUI icon or from a terminal and as asked above, if you do it from a terminal, do you get any messages on screen?  Does the user you are trying to run Gparted with have sudo privileges?

---

### Post by dieter-erich on 2023-11-26
Thanks for the replies! When I start gparted from the terminal I get: "Error executing command as another user: No authentication agent found" When I start it from Menu / System Tools nothing happens. When I try to run it as sudo I receive the message: "No protocol specified

(gpartedbin:2069424): Gtk-WARNING **: 23:02:35.977: cannot open display: :2" On the other machine it works correctly under all the above three conditions. Of note, when using sudo I get the message: "sudo gparted GParted 1.3.1 configuration --enable-libparted-dmraid --enable-online-resize libparted 3.4" but this does not seem to impact on gparted's normal execution!

---

### Post by MAFoElffen on 2023-11-27
Are you using X11 or Wayland?
> 
Wayland forbids root graphical applications. Whilst there are workarounds for XWayland apps, you really cannot have XWayland-free graphical applications running as root

Those workarounds are written into the startup script of GParted.

Snip from file '/usr/sbin/gparted'
```

        # Interim workaround to allow GParted run by root access to the
        # X11 display server under Wayland.  If configured with
        # './configure --enable-xhost-root', the xhost command is
        # available and root has not been granted access to the X11
        # display via xhost, then grant access.
        #
        ENABLE_XHOST_ROOT=no
        GRANTED_XHOST_ROOT=no
        if test "x$ENABLE_XHOST_ROOT" = 'xyes' && xhost 1> /dev/null 2>&1; then
                if ! xhost | grep -qi 'SI:localuser:root$'; then
                        xhost +SI:localuser:root
                        GRANTED_XHOST_ROOT=yes
                fi
        fi
        #
        # Run gparted as root.
        #
        pkexec --disable-internal-agent '/usr/sbin/gparted' "$@"
        status=$?
        #
        # Revoke root access to the X11 display, only if we granted it.
        #
        if test "x$GRANTED_XHOST_ROOT" = 'xyes'; then
                xhost -SI:localuser:root
        fi

```
Test by doing this first... Logout and logback into an X11 session, try to start GParted...

---

### Post by dieter-erich on 2023-11-27
Thanx!!!!

When running your script I get; "Error executing command as another user: No authentication agent found."  

when trying to find out which windows manager runs on my machine with wmctrl I get:

wmctrl -m
**Name: Metacity (Marco)**
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A

**but the output of this command is the same on the machine on which gparted runs correctly!**

---

### Post by MAFoElffen on 2023-11-27
That was not a script I wrote! That was only a snippet (piece) of the script that starts GParted... To show you, that by default, GParted is suppose to run on Xorg, not Wayland. Wayland has to be given a workaround to use an X11 screen to run on X11.

Tell me what this returns:
```

printenv XDG_SESSION_TYPE XDG_SESSION_DESKTOP

```

I had asked you to logout, and log back in, in an Xorg Session, instead of Wayland.

When you logout, select your username. When the password dialog box appears, there will be a gear icon in the lower right. Select it. Select an Xorg session. Enter your password and go on...

Tell me how "that" goes.

---

### Post by dieter-erich on 2023-11-29
On the laptop where gparted iworks and where it does not work I get the same output:

printenv XDG_SESSION_TYPE XDG_SESSION_DESKTOP
x11
On  both I was unable to localize a gear icon, which has probably to do with the fact that I use mate?

---

### Post by MAFoElffen on 2023-11-29
Show this"
```

grep . /etc/X11/default-display-manager

```

---

### Post by dieter-erich on 2023-11-30
On the PC gparted does not work:
grep . /etc/X11/default-display-manager
/usr/sbin/lightdm

I get the same on another laptop running Ubuntu 20.04.06 (I do not have the other one at hand) where gparted works!

---

### Post by dieter-erich on 2023-12-07
I now run the above command on another laptop with ubuntu mate 22.04 and, again I receive the same response "/usr/bin/lightdm". So, I guess it cannot the fault of the display manager that gparted fails to run correctly.....

---

