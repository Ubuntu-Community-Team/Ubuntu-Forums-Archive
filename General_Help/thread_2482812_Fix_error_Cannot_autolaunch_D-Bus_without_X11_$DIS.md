---
title: "Fix error: Cannot autolaunch D-Bus without X11 $DISPLAY on script to change wallpaper"
date: 2023-01-11
forum: General Help
---

### Post by Flame_Phoenix on 2023-01-11
[SIZE=4]Background[/SIZE]

I have created a script that changes my wallpaper periodically. The script works perfectly fine when I run it from bash, but having to manually run it on every startup is becoming annoying, so I decided I would automate the process using `systemd`. 

[SIZE=4]Scripts [/SIZE]

Following is the script that changes the wallpaper:

```

targetDir="/home/mypc/Pictures/Wallpapers"


function get_next_photo() {
    # Returns a random file form targetdir
    files=( "$targetDir"/* )
    echo "${files[RANDOM % ${#files[@]}]}"
}

function set_background() {
    # Takes an absolute file path as argument. Need * for spaces in path
    bg="$*"
    echo "Setting background to $bg"
    dconf write "/org/gnome/desktop/background/picture-uri" "'file://$bg'"

}


while :
do

	background=$(get_next_photo)
	echo "Next background is $background"
	set_background $background
	sleep 5m
done

```

And this is the [FONT=Century Gothic]***systemd***[/FONT] service I created for it, located in [FONT=Century Gothic]***/etc/systemd/system/background-changer.service***[/FONT]:

```

[Unit]
Description=Periodically changes the background wallpaper, taking random images from the Pictures/wallpapers folder

[Service]
ExecStart=/bin/bash /home/mypc/background_changer.sh

[Install]
WantedBy=default.target

```

[SIZE=4]Problem[/SIZE]

The problem is that once I start the job using [FONT=Century Gothic]***systemd***[/FONT] the wallpaper never changes.
After checking with [FONT=Century Gothic]***sudo systemd status background-changer.service***[/FONT], this is what I got:

```

$ sudo systemctl status background-changer.service 
&#9679; background-changer.service - Periodically changes the background wallpaper, taking random images from the Pictures/wallpapers folder
     Loaded: loaded (/etc/systemd/system/background-changer.service; disabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-01-09 13:17:32 CET; 7min ago
   Main PID: 14196 (bash)
      Tasks: 2 (limit: 18936)
     Memory: 596.0K
        CPU: 16ms
     CGroup: /system.slice/background-changer.service
             &#9500;&#9472;14196 /bin/bash /home/mypc/background_changer.sh
             &#9492;&#9472;17655 sleep 5m

ene 09 13:17:32  systemd[1]: Started Periodically changes the background wallpaper, taking random images from the Pictures/wallpapers folder.
ene 09 13:17:32 bash[14196]: Next background is /home/mypc/Pictures/Wallpapers/jonatan-pie-3l3RwQdHRHg-unsplash.jpg
ene 09 13:17:32 bash[14196]: Setting background to /home/mypc/Pictures/Wallpapers/jonatan-pie-3l3RwQdHRHg-unsplash.jpg
ene 09 13:17:32 bash[14198]: error: Cannot autolaunch D-Bus without X11 $DISPLAY
ene 09 13:22:32 bash[14196]: Next background is /home/mypc/Pictures/Wallpapers/jonatan-pie-3l3RwQdHRHg-unsplash.jpg
ene 09 13:22:32 bash[14196]: Setting background to /home/mypc/Pictures/Wallpapers/jonatan-pie-3l3RwQdHRHg-unsplash.jpg
ene 09 13:22:32 bash[17652]: error: Cannot autolaunch D-Bus without X11 $DISPLAY

```

The last line specifically caught my attention:

```

error: Cannot autolaunch D-Bus without X11 $DISPLAY

```

I have searched for some time now how to fix this, but every solution I find is widely different. I went from reinstalling graphic drivers, to password managers with stuff in between, but nothing works:

 - [https://anto.online/guides/cannot-autolaunch-d-bus-without-x11-display/](https://anto.online/guides/cannot-autolaunch-d-bus-without-x11-display/)
 - [https://askubuntu.com/questions/735898/cannot-autolaunch-d-bus-without-x11-display](https://askubuntu.com/questions/735898/cannot-autolaunch-d-bus-without-x11-display)
 - [https://github.com/zowe/zowe-cli/issues/1139](https://github.com/zowe/zowe-cli/issues/1139)
 - [https://ubuntu-mate.community/t/error-cannot-autolaunch-d-bus-without-x11-display/11928](https://ubuntu-mate.community/t/error-cannot-autolaunch-d-bus-without-x11-display/11928)
- [https://askubuntu.com/questions/645968/error-cannot-autolaunch-d-bus-without-x11-display/748046#748046](https://askubuntu.com/questions/645968/error-cannot-autolaunch-d-bus-without-x11-display/748046#748046)

Can someone help me understand why ?

---

### Post by Holger_Gehrke on 2023-01-11
At the point in time when your systemd service is started the desktop is not yet up and running (and even if it was, the DISPLAY variable would not be accessible to it; variables go from parent to child process, not the other way around). You basically need to start your script after you log in. Instead of using a systemd service I'd use a .desktop file in ~/.config/autostart or I'd look into a user instance of systemd with the services located in ~/.config/systemd/user/.

Holger

---

### Post by Flame_Phoenix on 2023-01-11
> **Holger_Gehrke said:**
> At the point in time when your systemd service is started the desktop is not yet up and running (and even if it was, the DISPLAY variable would not be accessible to it; variables go from parent to child process, not the other way around). You basically need to start your script after you log in. Instead of using a systemd service I'd use a .desktop file in ~/.config/autostart or I'd look into a user instance of systemd with the services located in ~/.config/systemd/user/.

Holger

I am manually starting the systemd job, so I know the issue has to be the DISPLAY variable not being accessible (because I am already logged in). 
I have taken you advice and I have created the following ***~/.config/autostart/.desktop*** file:

```

[Desktop Entry]
Version=1.0
Name=Wallpaper Changer
Comment=Periodically changes the background wallpaper, taking random images from the Pictures/wallpapers folder.
Exec=/home/mypc/background_changer.sh
Icon=/usr/share/icons/gnome-logo-text.svg
Terminal=false
Type=Application
Categories=Utility;

```

Other then repeatedly restarting my computer, how can I test if this works?

---

### Post by Flame_Phoenix on 2023-01-16
After changing to a desktop file, I still found some issues, but with the help of another forum I was able to make it work. Basically the code is fine, but there were some config issues:

- Script misses a shebang. 
- .desktop-file (not .dektop) should have a meaningful name like wallpaperchanger.desktop. 
- .desktop-file should be executable

With these fixed, the Desktop solution worked.

[https://askubuntu.com/questions/1449905/how-to-test-if-desktop-file-is-working](https://askubuntu.com/questions/1449905/how-to-test-if-desktop-file-is-working)

---

