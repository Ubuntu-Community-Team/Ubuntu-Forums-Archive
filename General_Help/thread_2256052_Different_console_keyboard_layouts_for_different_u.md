---
title: "Different console keyboard layouts for different users"
date: 2014-12-09
forum: General Help
---

### Post by mark179 on 2014-12-09
I have a server that is administered by two different users. One is a standard QWERTY user and the other is a filthy Dvorak deviant (me). The Dvorak user is fine with hunting-and-pecking to log in, but then he wants to have a Dvorak layout loaded so he can touch-type on the console. This can be accomplished with _sudo loadkeys dvorak_. However, this permanently changes the console keyboard layout, and if he forgets to execute _[FONT=courier new]sudo loadkeys us [/FONT]_before he logs out, the QWERTY user is helpless and cannot log in at all (no Dvorak labels on the keyboard for him to hunt-and-peck with).

Is there a way to have different console keyboard layouts for different users, or to automatically change the console keyboard layout back on logout?

---

### Post by mark179 on 2014-12-09
Here's a solution, please let me know if you have a better one.

First, add the following using visudo so loadkeys can be run without demanding a password:
%sudo ALL=NOPASSWD:/usr/bin/loadkeys

In the Dvorak user's .profile (only run on an interactive login, not for sub-shells):

```

MYTTY=$(tty | sed -e "s:/dev/::")
if [ "$MYTTY" = "tty1" ]; then
    sudo loadkeys dvorak
fi

```

This will load a Dvorak layout, but only when he logs in on a console session (not SSH).

In his .bash_logout:
```

if [ "$SHLVL" = 1 ]; then
    MYTTY=$(tty | sed -e "s:/dev/::")
    if [ "$MYTTY" = "tty1" ]; then
        sudo loadkeys us
    fi
fi

```

This will switch the console to Dvorak layout when the Dvorak user logs in, but only on the console, and will switch it back to QWERTY when he logs out. That way it will always be QWERTY at the login prompt. Remote logins like SSH won't change the layout at all, since SSH sends characters, not keys, and thus the server's keyboard layout doesn't matter for a remote login.

Unfortunately, if the login shell is terminated externally, logout doesn't happen and .bash_logout doesn't get executed. This leaves the console keyboard layout in Dvorak mode. This can be fixed with a reboot, of course, but that's not a great answer for a server.

---

