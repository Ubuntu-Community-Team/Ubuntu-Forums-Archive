---
title: "Need authentication for mounting thumb drives / reboot / shutdown etc."
date: 2014-08-08
forum: General Help
---

### Post by ladiko on 2014-08-08
Hello,

I installed a naked ubuntu server 14.04 x64, then xfce4 and some other packages:

alsa-base alsa-utils aptitude bc build-essential chromium-browser deborphan flip fortunes fortunes-de geany git gksu gnome-icon-theme-symbolic guake htop imagemagick libxml2-utils network-manager nginx nodejs npm p7zip-full p7zip-rar php5-cli php5-fpm php5-intl php5-sqlite pv ristretto rsync rungetty samba screen smartmontools software-properties-common ssh streamer usb-modeswitch v4l-utils x11vnc xarchiver xfce4 xfce4-power-manager xfce4-terminal xfce4-xkb-plugin xinput-calibrator yad zip

It's a kiosk system and since 12.04 i was using rungetty to autologin the only (unprivileged) user and in 12.04 i had some issues with the autologin using lxdm, gdm and xfwm. rungetty is just lightweight and always worked.

But because rungetty doesnt start a consolekit session, i had to use a workaroung in ubuntu 12.04 to get access to thumb drives, reboot and shutdown without entering the sudo password: [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130)

But this fix doesnt work anymore. I also noticed that consolekit isn't installed by default anymore, so i tried to install it by myself and reboot - but it didnt work. i also tried to execute sudo dpkg-reconfigure -f noninteractive libpam-runtime afterwards, but no success.

btw.: there are severall machines and all of them are installed from a script - so the machines are almost the same, except the switch from ubuntu precise to trusty.

ck-list-sessions looks exactly the same as on 12.04:

```
Session1:
    unix-user = '1000'
    realname = 'ladiko'
    seat = 'Seat1'
    session-type = ''
    active = FALSE
    x11-display = ''
    x11-display-device = ''
    display-device = '/dev/tty1'
    remote-host-name = ''
    is-local = TRUE
    on-since = '2014-08-08T19:27:35.358059Z'
    login-session-id = '1'
    idle-since-hint = '2014-08-08T19:28:05.890436Z'
Session2:
    unix-user = '1000'
    realname = 'ladiko'
    seat = 'Seat1'
    session-type = ''
    active = TRUE
    x11-display = ':0'
    x11-display-device = '/dev/tty7'
    display-device = '/dev/tty1'
    remote-host-name = ''
    is-local = TRUE
    on-since = '2014-08-08T19:27:35.864936Z'
    login-session-id = '1'

```

Could this help somehow? [http://unix.stackexchange.com/questions/35595/how-can-i-activate-the-current-session-in-consolekit](http://unix.stackexchange.com/questions/35595/how-can-i-activate-the-current-session-in-consolekit)

---

