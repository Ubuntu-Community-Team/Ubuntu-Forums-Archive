---
title: "logout freeze on edubuntu (ltsp) server after thin client login"
date: 2007-06-28
forum: General Help
---

### Post by clarknova on 2007-06-28
Hey,

I have a functioning Edubuntu 7.04 Feisty x86_64 server and I have i386 PXE clients booting from it. Overall it works well, but there seems to be one glaring bug. I can reproduce it every time with the following sequence:

1. Create user
2. Boot thin client and login with username
3. Log out of thin client
3. Login to server with username
4. Click the logout button
5. Click any of the logout options

At this point the sesion gets 'stuck'. By this I mean that the logout options window won't go away. Whatever logout button I pressed retains its depressed appearance and nothing more happens. The mouse pointer is still movable. If I am playing internet radio it continues to play. There doesn't appear to be any way to recover from this other than to kill the X session, either by ctrl-alt-backspace or /etc/init.d/gdm restart from tty1-6 or ssh.

Any ideas what is causing this or how to correct or work around it?

Here is some output, FWIW, having just caused the problem as user 'guest'

> $ ps -u guest
  PID TTY          TIME CMD
28730 ?        00:00:01 x-session-manag
28773 ?        00:00:00 ssh-agent
28776 ?        00:00:00 dbus-daemon
28777 ?        00:00:00 dbus-launch
28779 ?        00:00:00 gconfd-2
28782 ?        00:00:00 gnome-keyring-d
28784 ?        00:00:00 gnome-settings-
29552 ?        00:00:00 metacity
29553 ?        00:00:00 gnome-panel
29556 ?        00:00:00 nautilus
29564 ?        00:00:00 bonobo-activati
29567 ?        00:00:00 gnome-vfs-daemo
29568 ?        00:00:00 gnome-volume-ma
29578 ?        00:00:00 evolution-alarm
29593 ?        00:00:00 nm-applet
29602 ?        00:00:00 trashapplet
29614 ?        00:00:00 gnome-cups-icon
29617 ?        00:00:00 gnome-power-man
29637 ?        00:00:00 mixer_applet2
29642 ?        00:00:00 mapping-daemon
29713 ?        00:00:01 vlc
29741 ?        00:00:00 gnome-screensav
31271 ?        00:00:00 esd

---

### Post by clarknova on 2007-07-02
This appears to be related to esound settings. I have reported a bug on [launchpad.net ]("https://bugs.launchpad.net/ubuntu/+source/esound/+bug/122972")for anyone looking for the most up-to-date details and information.

db

---

### Post by clarknova on 2007-07-07
A fix has been posted for this on launchpad.net. Apparently it may involve a reinstall of your Edubuntu server.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/101946](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/101946)

---

### Post by benford on 2007-07-12
Your problem seems to match this bug: [HTML]https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/105709[/HTML]

I was experiencing GDM freezes just like yours, as far as I can tell from your description, and following the solution outlined in the comments fixed my problem.

---

