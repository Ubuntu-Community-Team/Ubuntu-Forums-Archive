---
title: "Where/when is .Xauthority created? Problems starting X-apps via sytemd --user."
date: 2016-02-26
forum: General Help
---

### Post by makkus on 2016-02-26
Hiya,

I'm currently on 15.10, playing with systemd (--user), trying to get X-applications started after logging in via lightdm. I know I could also do it via .xinitrc/.xsession, or autostart them as "Startup applications", but would like to figure out how to do it with systemd. I'm having problems getting them to start (non-X-apps are fine), and it looks like that the issue is that the .Xauthority file is not created at the point when I try to start the application. My systemd unit files look like this:

    [Unit]
    Description=davmail: exchange <-> dav proxy server
    After=default.target

    [Service]
    EnvironmentFile=/home/makkus/.config/systemd/xenv
    ExecStart=/home/makkus/.nix-profile/bin/davmail.sh
    #Restart=always

    [Install]
    WantedBy=default.target


After doing a bit of debugging (using scripts to monitor the existence/content of ~/.Xauthority, it looks like the .Xauthority file is always created at some point after the default.target is reached. I've got no idea who/which script is responsible creating it though, it doesn't look like systemd has anything to do with it. If I do a 'systemctl --user start davmail.service manually it starts up fine. Could anybody on here maybe give me some pointers, would be much appreciated!

---

