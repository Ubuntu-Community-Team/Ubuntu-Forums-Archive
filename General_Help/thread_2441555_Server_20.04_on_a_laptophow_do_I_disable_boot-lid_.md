---
title: "Server 20.04 on a laptop:how do I disable boot-lid actions but console power save."
date: 2020-04-24
forum: General Help
---

### Post by alexdodd on 2020-04-24
Moving on from my [last disaster]("https://ubuntuforums.org/showthread.php?t=2441139").

I have start a fresh, and installed Ubuntu Server 20.04 on a Dell laptop which will server some dockers on my network

I've installed the GUI because i'd like it there, for my own personal peace of mind although as ever it'll probably cause me more trouble than necessary.

I'm now back asking exactly the same previous questions I guess:

[LIST=1]
[*]How do I disable the fresh installed GUI booting automatically, so it just boots to console?
[*]How do I disable the boot lid actions, make the do nothing?
[*]How do i enable console blanking and display power saving features.  So the display actually turns off.
[*]
[/LIST]

I think I have an extra question:
It looks like i'm ok booting up conneted to Ethernet, but if I unplug the eno1 check fails and the boot hangs for quite a while, because it doesn't connect to wifi?  When the GUI loads up it connects to wifi instantly so that's saved somewhere, but boot isnt checking there.

In the spirit of *not* breaking it first and asking questions later, or copying other things I've seen written elsewhere on the internet, I hope someone can help me up front first!

Cheers :)

---

### Post by alexdodd on 2020-04-24
Ok, methodically I've worked through this.

Not exactly sure about netplan config?  I just set my eno1 to optional, so it fails quickly at boot (if unplugged), and the wifi seems to connect later with some other settings, probably pulled from the GUI?

setterm fixes console blanking, but i'm very nervous about adding it anywhere to make the change persistent in a "proper" way.  Any clues?

---

### Post by drx-eng on 2020-05-23
1. I just do ( or gdm3, what ever display manager you use)
```
sudo systemctl disable lightdm
```
I also uncomment ( but the result is ugly, low resolution, so I just settle with systemctl)
```
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"
```
When I need GUI, i just do (at tty1)
```
startx
```
In the past, I start display manager manually, so I guess now the command will be
```
sudo systemctl start lightdm &
```

2. In gnome-tweak there is setup "Suspend when laptop lid is closed" creating "Startup application" ignore-lid-switch-tweak. I'm using laptop with broken screen (can't be closed anyway) so I have not explore more. Soon I might need to set it this up, on text mode Ubuntu, I'll try to google "disable lid switch ubuntu server laptop" or something.

> 
sudo nano /etc/systemd/logind.conf
Uncomment this line [#HandleLidSwitch]("https://www.youtube.com/results?search_query=%23HandleLidSwitch")=suspend
And change it to HandleLidSwitch=ignore
Save, then do sudo service systemd-logind restart or  sudo systemctl restart systemd-logind

[URL="https://tipsonubuntu.com/2018/04/28/change-lid-close-action-ubuntu-18-04-lts/"]https://www.youtube.com/watch?v=NEpoh89MYnc
https://tipsonubuntu.com/2018/04/28/change-lid-close-action-ubuntu-18-04-lts/[/URL]

3.Old threat suggest to pass value consoleblank to kernel via grub
```
GRUB_CMDLINE_LINUX_DEFAULT="consoleblank=1"
```
in  /etc/default/grub. But it's seems not working anymore with newer Ubuntu  version, and it's still on-going discussion for what happen and why.  I also consider to use ```
GRUB_CMDLINE_LINUX_DEFAULT="consoleblank=1 text"
``` for combo use with question (1)

After login I can do 
```

setterm --blank 1
cat /sys/module/kernel/parameters/consoleblank 

```
to check the result.

It's working, but now I need to setup as service.

I create /etc/systemd/system/consoleblank.service 

```
[Unit]
Description=Enable consoleblank=1 after boot by executing setterm

[Service]
Type=oneshot
Environment=Term=linux
StandardOutput=tty
TTYPath=/dev/console
ExecStart=/usr/bin/setterm -blank 1

[Install]
WantedBy=multi-user.target
```

Then do ```
sudo chmod +x /etc/systemd/system/consoleblank.service 
sudo systemctl enable consoleblank.service

```

But no luck, It's not working.
I don't want to start new post, so I hope by answering your post, it will go up and got more respond.

---

