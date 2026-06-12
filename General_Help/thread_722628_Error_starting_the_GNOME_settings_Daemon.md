---
title: "Error starting the GNOME settings Daemon"
date: 2008-03-12
forum: General Help
---

### Post by snkngshps on 2008-03-12
I'm running Hardy Heron 8.04 with GNOME 2.22

The other night I instaled Compiz. I started getting weird trails all over my screen, so I closed all of my programs and rebooted and I got this error on my next startup:
"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly."

I thought the problem might have been with compiz so I disabled and removed it, restarted and still the same problem. If I try to run "gnome-settings-daemon" from the terminal I get this:

"The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 89 error_code 1 request_code 151 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"


I've looked around multiple forums and tried many workarounds and fixes but nothing works.. Any ideas? Is there a way to completely uninstall and reinstall GNOME?

---

### Post by Suparious on 2008-03-13
as root from a command line, try to reconfigure the xserver:

```
dpkg-reconfigure xserver-xorg
```

it should go though your settings and once finished will create a new xorg.conf, install it and move your old config to something like xorg.conf.20080412.

Although messy, you could try removing the "ubuntu-desktop", gnome* gdm* compiz* like this:

```
apt-get remove *-desktop gnome* gdm* xserver-xorg compiz*
``` <-- this is very violent

and to be even more sure, before you reinstall those, do this:

```
dpkg --purge xserver-xorg
```

hopefully just rebuilding the xorg.conf will work for you!

---

### Post by smomanyi on 2008-03-31
The problem is the xserver-xgl. Just remove it with this command "apt-get remove xserver-xgl"

---

