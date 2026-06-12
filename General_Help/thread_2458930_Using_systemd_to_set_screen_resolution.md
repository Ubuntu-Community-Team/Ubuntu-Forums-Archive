---
title: "Using systemd to set screen resolution"
date: 2021-03-06
forum: General Help
---

### Post by DanR01 on 2021-03-06
[SIZE=2][FONT=arial]Following an upgrade my hidpi screen resolution has been downgraded to 800x600. 

I can set the proper screen resolution by running the following commands:

```
xrandr --newmode "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync;
xrandr --addmode eDP-1 3840x2160_60.00; xrandr --addmode eDP-1 3840x2160_60.00; exit
```

I would like to run this as a script at logon. 

I'm getting stuck trying to implement this as a systemd unit file. 

As I understand, this should be run as a user service from .config/systemd/user  

I would be grateful is anyone could suggest the correct format for a systemd unit file that interacts with the X server. What I have is incorrect: 

```
[Unit]
After=default.target

[Service]
Environment=DISPLAY=:0
ExecStart=/home/dan/hidpi.sh
Restart=always

[Install]
WantedBy=default.target



```[/FONT][/SIZE]

---

### Post by TheFu on 2021-03-06
I could be wrong, bu I don't believe this will work.
I'd just use one of the X/Windows session init files.  ~/.xprofile or ~/.xinitrc
Sorry, I don't remember which gets run after the x-server runs, but before the user's session is up.

---

### Post by DanR01 on 2021-03-07
Using .xprofile was the solution.
Thank you

---

