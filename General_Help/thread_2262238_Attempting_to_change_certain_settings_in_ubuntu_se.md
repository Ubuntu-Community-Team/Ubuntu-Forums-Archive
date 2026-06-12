---
title: "Attempting to change certain settings in ubuntu server/ minimal gnome gui"
date: 2015-01-23
forum: General Help
---

### Post by brayden3 on 2015-01-23
Just recently installed Ubuntu Server 14.4 LTS and decided to put on a minimal gui because I'm new and the terminal gets confusing sometimes (though I'm learning). Everything has been working great execpt for two issues.

1. Any attempt I make to automatically log myself into my gui will not work.

2. I cannot setup any start up programs.

I'm running gnome minimal install

sudo apt-get install xorg gnome-core gnome-system-tools gnome-app-install

I also added gnome-tweak-tool to enable desktop shortcuts because every command I tried didn't work. I noticed tweak tools is supposed to be able to handle start up programs but the '+' symbol doesn't work for me.

I know it is probably not the most optimal set up, but I'd like to have it auto login for me and launch something like TeamViewer so I can have access to it while I'm away at college. In anycase I'm sure it's possible, I just haven't gotten anything to work for me.

Thanks.

---

### Post by TheFu on 2015-01-24
Forget the gnome settings. Go directly to the login program settings to address the auto login. BTW, this is terrible security in an environment with lots of other people - like a college apartment/dorm. So ... depending on what the login manager used is, that is the config file under /etc/ you need to modify. I don't use gnome, so I don't know what it is.

To control autostarting programs ... tweak the window manager, WM, settings.  Under openbox, those are in ~/.config/openbox/autostart.  Just figure out which WM is being used by your install.

For remote desktops ... there are lots of other options than teamviewer i.e. a windows program.  Setup ssh for remote access and verify that works.  From that point on, you'll be able to securely connect to the machine from anywhere in the world without having to trust some 3rd party. I'm always amazed when people do that.

---

