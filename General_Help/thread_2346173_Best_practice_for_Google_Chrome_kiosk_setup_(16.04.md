---
title: "Best practice for Google Chrome kiosk setup (16.04 + Openbox)"
date: 2016-12-12
forum: General Help
---

### Post by Joost_Plas on 2016-12-12
I'm using Ubuntu 16.04.1 LTS to run Google Chrome in a kiosk setup with just running Openbox 3.6.1.
I'm having some troubles in my current setup with stability. On some boots Chrome and Openbox are loaded fine, but on some boots Chrome doesn't start or Openbox session doesn't start until I click with my mouse.

I'm hoping someone can point me at same flaws at my current setup and advice me how to improve this. 

This is my current setup.

1. Autologin user with /etc/systemd/system/getty@tty1.service.d/autologin.conf:

```
[Service]
ExecStart=
ExecStart=-/sbin/agetty --autologin USER --noclear %I 38400 linux

```

2. Autostart x and openbox-session with /home/USER/.bash_profile:

```
if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]]; then
exec sudo -u USER startx /usr/bin/openbox-session -- -nocursor
fi

```

3. Autostart compton, some settings and the Chrome script with .config/openbox/autostart:

```
xset -dpms &
xset s off &
sleep 3
xrandr --output HDMI-2 --mode 1920x1080 --rate 50 --rotate normal &
compton -b &
sleep 3
/home/USER/.loop_script_reboot.sh &

```

4. The script that starts Google-Chrome and restarts it on close/exit (I think this must be the weakest link in the setup) with /home/USER/.loop_script_reboot.sh:

```
#!/bin/sh
while :
do
google-chrome
done

```

I hope someone can help me optimize and stabilize this setup! Would be much appreciated!

---

