---
title: "Kiosk mode using lightdm on Ubuntu 20.04 is showing login screen sometimes"
date: 2024-09-07
forum: General Help
---

### Post by ravi_joshi on 2024-09-07
There are plenty of questions on kiosk mode in this forum, but none seems to discuss such abnormal behavior. In short, even after enabling auto-login, I sometimes see login screen in Ubuntu 20.04 which is configured to run on Kiosk mode. My requirements are similar to one posted [here]("https://ubuntuforums.org/showthread.php?t=2458626&p=14023557#post14023557").


Below are all the steps, I have done so far:


```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.6 LTS
Release:	20.04
Codename:	focal


$ whoami
user


$ sudo apt install lightdm
$ sudo dpkg-reconfigure lightdm
$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm


$ sudo nano /usr/share/xsessions/kiosk.desktop
[Desktop Entry]
Name=App Kiosk Mode
Comment=Kiosk Mode for App
Exec=/usr/local/bin/kiosk.sh
Type=Application


$ cat /usr/local/bin/kiosk.sh
#!/bin/bash
xset s off
xset -dpms
xset s noblank


$ sudo chmod +x /usr/local/bin/kiosk.sh
$ cat /etc/lightdm/lightdm.conf.d/20-autologin.conf
[Seat:*]
autologin-user=user
autologin-session=kiosk


$ mkdir -p ~/.config/systemd/user/
$ cp ~/app/ui.service ~/.config/systemd/user/
$ cat ~/app/ui.service 
[Unit]
Description=UI Service
After=graphical.target
[Service]
ExecStart=/home/user/app/ui.sh
Restart=always
RestartSec=1
[Install]
WantedBy=graphical.target


$ cat ~/app/ui.sh 
#!/bin/bash
until curl -s http://my_website.com:8080 > /dev/null; do # Wait until webpage is available
    echo "Waiting until webpage is available..."
    sleep 1
done
export DISPLAY=:0
export XAUTHORITY=/home/user/.Xauthority
while ! pgrep -x "Xorg" > /dev/null; do # Wait until the display is available
    echo "Waiting for X server to start..."
    sleep 1
done
while ! xset q &>/dev/null; do # Wait until the X server is fully ready
    echo "Waiting for X server to be ready..."
    sleep 1
done
echo "Starting chromium browser."
/usr/bin/chromium-browser --kiosk http://my_website.com:8080


$ chmod +x ~/app/ui.sh


$ systemctl --user daemon-reload
$ systemctl --user start ui.service
$ systemctl --user enable ui.service


$ sudo sed -i 's/^GRUB_CMDLINE_LINUX_DEFAULT="[^"]*"/GRUB_CMDLINE_LINUX_DEFAULT=""/' /etc/default/grub
$ sudo update-grub
$ reboot

```


The problem is that sometimes it shows the login screen though autologin is enabled. I suspect some issue with the way ui.service is set probably! How do debug and fix this issue?

---

### Post by TheFu on 2024-09-08
At this point, the only 20.04 releases with support are the Gnome and Server versions.  No others with any GUI, including any with LightDM are supported. Support for other DEs ended in 2023.

If you are working on a new kiosk deployment, look towards 24.04 releases and plan for OS upgrades every 2 yrs.  Set that expectation with your management, so they aren't surprised.

Of course, if the system will never connect to any network (especially wifi!!!!), then the security and updates don't matter. Run any release you like as long as you like.  Generally, it is networking and/or physical access by untrusted people that cause security problems.

For many situations, Ubuntu CORE is a good answer for embedded needs. It provides a central method of updating the applications and 10 yrs of security patch support.

If it were me tasked with creating a new kiosk, I'd not use Ubuntu. I'd use TinyCore with only the specific applications I needed and I'd produce 2 updates a year for security stuff (mainly new kernels).  But it depends on what you mean by "kiosk". The exact applications matter.  For many people, a Kiosk is just something like ChromeOS but locked to just a browser and no other applications available.

---

