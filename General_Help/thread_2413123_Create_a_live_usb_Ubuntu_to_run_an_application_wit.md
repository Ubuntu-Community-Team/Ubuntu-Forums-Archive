---
title: "Create a live usb Ubuntu to run an application without desktop environment"
date: 2019-02-21
forum: General Help
---

### Post by josescxavier-q on 2019-02-21
[COLOR=#242729][FONT=Arial]I need to create a USB live ubuntu to run an application. I want to open my application after the boot as fullscreen without any other option to the end user. [/FONT][/COLOR][COLOR=#242729][FONT=Arial]I read that I should use Gtk+ or Qt5 if I want to run an app without a desktop environment or display manager so I created my app using Gtk+.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]To be able to open the app without a desktop environment I added to .bashrc the following:[/FONT][/COLOR]
```
export DISPLAY=:0
while true; do ./myapp; done
```
[COLOR=#242729][FONT=Arial]I need to run it inside inside a while loop because sometimes I got the following error:[/FONT][/COLOR]
```
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
(myapp:4918): Gtk-WARNING **: cannot open display:
```

[COLOR=#242729][FONT=Arial]I suppose I was trying to run the application before the display manager is running.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Enable auto-login for the default user makes .bashrc on tty1 to be executed and my application is launched.[/FONT][/COLOR]
```
mkdir /etc/systemd/system/getty@tty1.service.d
nano /etc/systemd/system/getty@tty1.service.d/override.conf
    [Service]
    ExecStart=
    ExecStart=-/sbin/agetty --noissue --autologin ubuntu %I $TERM
    Type=idle
```

[COLOR=#242729][FONT=Arial]To make it work I also needed to edit /usr/share/xsessions/ubuntu.desktop so it doesn't launch the desktop environment.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm using Ubuntu 16.04.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It is working however there are some points that I don't understand.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]1 - Most of the answers to this problem say to edit ubuntu.desktop and change exec to my application however I wasn't able to make it work. It doesn't run Ubuntu desktop indeed but I wasn't able to make it run my app. I didn't find how I could debug why it was failing.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]2 - I read that Gtk+ and Qt5 can use Wayland so I didn't a desktop environment neither a display manager, how could I do that?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]3 - Which alternatives do you recommend to obtain the same result? The way I did it in .bashrc sounds a little bit hackish.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thank you[/FONT][/COLOR]

---

### Post by coffeecat on 2019-02-21
Support, not chat.

*Thread moved to **General Help**.*

---

