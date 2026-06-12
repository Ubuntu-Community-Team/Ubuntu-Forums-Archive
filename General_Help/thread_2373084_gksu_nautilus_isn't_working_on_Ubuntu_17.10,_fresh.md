---
title: "gksu nautilus isn't working on Ubuntu 17.10, fresh install."
date: 2017-10-02
forum: General Help
---

### Post by isaac20 on 2017-10-02
I need to access some system files with admin privileges so I ran gksu nautilus in the terminal and got a message saying gksu wasn't installed so I installed the necessary packages via command line and now here's what I get returned when I try to run gksu nautlius:


```
Failed to run nautilus as user root.(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",


(gksu:2979): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Error copying '/home/isaac/.Xauthority' to '/tmp/libgksu-nNo8DH': No such file or directory
```


As well as a popup window saying


Unable to copy the user's Xauthorization file because there's no such file or directory. I haven't touched linux in a couple of years so this threw me for a loop.

---

### Post by Frogs Hair on 2017-10-02
The gksu package has been depreciated and doesn't work in wayland. Try the following.

```
sudo -H nautilus 
```

The following will work in X sessions.

```
pkexec nautilus
```

---

### Post by mc4man on 2017-10-02
In 17.10 really the best way to get a root nautilus is to switch to a location based address bar (ctrl+l) and use
```
admin:// 
```

Otherwise you may get what's shown here, distracting at best, maybe worse...
[https://ubuntuforums.org/showthread.php?t=2367414&p=13671059&viewfull=1#post13671059](https://ubuntuforums.org/showthread.php?t=2367414&p=13671059&viewfull=1#post13671059)

---

### Post by isaac20 on 2017-10-02
It's a bit buggy and freezes the desktop when dragging and dropping files into the root browser but it works...I miss the old terminal method :( but thank you!

---

### Post by Frogs Hair on 2017-10-02
> **isaac20 said:**
> It's a bit buggy and freezes the desktop when dragging and dropping files into the root browser but it works...I miss the old terminal method :( but thank you!

My method for wayland is have non-root instance of nautilus running and drag the file from there into the root instance. I've had some folders actually get stuck on the desktop trying to drag them in wayland.

---

### Post by Morbius1 on 2017-10-16
So to recap instead of using gksu it appears I have the following options:

sudo -H nautilus
pkexec nautilus
nautilus admin:///

Or .... I could install Xubuntu 17.10 where gksu still works. Things like Samba ( the server configuration utility not the package ) also works because by default launching Samba runs "gksu system-config-samba". They must not have received the memo on gksu. And of course the default umask is set to 0002 as <fill in the name of your personal deity> intended instead of the 0022 in Ubuntu.

---

### Post by Cushie on 2018-01-14
Sudo -H  and gksu -H don't work for me.

error:-

"[I][B]No protocol specified
Unable to init server: Could not connect: Connection refused
[/B][/I]

---

### Post by cruzer001 on 2018-01-14
Seen this?

[https://ubuntuforums.org/showthread.php?t=2382238&p=13730472#post13730472](https://ubuntuforums.org/showthread.php?t=2382238&p=13730472#post13730472)

---

