---
title: "How to debug multiseat? Second seat turns off after login."
date: 2024-01-11
forum: General Help
---

### Post by OliW on 2024-01-11
I had been using multiseat on 22.04 with great success. Two nvidia cards and loginctrl to assign the PCI IDs of those, a USB controller, sound, etc, etc.

Then I upgraded to 23.10 and it stopped working. You get a login screen on both displays. Seat0 works as expected but the secondary seat monitor turns off when I log in, as any user.

The session seems to start though, I just can't see anything.

```
systemd&#9472;&#9516;&#9472;(sd-pam)
        &#9500;&#9472;dbus-daemon
        &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;4*[{gnome-keyring-d}]
        &#9500;&#9472;goa-daemon&#9472;&#9472;&#9472;4*[{goa-daemon}]
        &#9500;&#9472;goa-identity-se&#9472;&#9472;&#9472;3*[{goa-identity-se}]
        &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;4*[{gvfs-afc-volume}]
        &#9500;&#9472;gvfs-goa-volume&#9472;&#9472;&#9472;3*[{gvfs-goa-volume}]
        &#9500;&#9472;gvfs-gphoto2-vo&#9472;&#9472;&#9472;3*[{gvfs-gphoto2-vo}]
        &#9500;&#9472;gvfs-mtp-volume&#9472;&#9472;&#9472;3*[{gvfs-mtp-volume}]
        &#9500;&#9472;gvfs-udisks2-vo&#9472;&#9472;&#9472;4*[{gvfs-udisks2-vo}]
        &#9500;&#9472;gvfsd&#9472;&#9472;&#9472;3*[{gvfsd}]
        &#9500;&#9472;gvfsd-fuse&#9472;&#9472;&#9472;6*[{gvfsd-fuse}]
        &#9500;&#9472;2*[pipewire&#9472;&#9472;&#9472;2*[{pipewire}]]
        &#9500;&#9472;pipewire-pulse&#9472;&#9472;&#9472;2*[{pipewire-pulse}]
        &#9500;&#9472;tracker-miner-f&#9472;&#9472;&#9472;6*[{tracker-miner-f}]
        &#9492;&#9472;wireplumber&#9472;&#9472;&#9472;5*[{wireplumber}]
```

I've tried:

[LIST]
[*]Several versions of the Nvidia driver
[*]Forcing Wayland through /etc/gdm3/custom.conf
[*]Forcing Xorg through /etc/gdm3/custom.conf
[/LIST]

One oddity is that the login session remains running after login. It's c14 here. If I kill it, a new one is spawned and the screen switches to it.

```
SESSION  UID USER  SEAT       TTY 
    261 1000 oli   seat0      tty2
    262 1002 katie seat-katie 
    c14  120 gdm   seat-katie 
```

I'm usually pretty resourceful when it comes to fixing my own things but I can't even find logs for the second display server. I'm getting pretty desperate. Any help appreciated.

---

