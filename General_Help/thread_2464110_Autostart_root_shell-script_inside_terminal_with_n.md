---
title: "Autostart root shell-script inside terminal with no user interaction"
date: 2021-06-24
forum: General Help
---

### Post by kalladan on 2021-06-24
Hello dear Ubuntu-friends,


I have an application that I need to automatically start after the ubuntu desktop has launched and the user has successfully been logged on (also automatically). The problem is, that the application needs root privileges because it uses special low-level network capabilities and it also needs to be able to run at a high process and scheduling priority. For the application to work properly, I must start it in the following way:


```
sudo -E nice --19 APP_NAME
```


This of course requires manual input of the root password, which I need to avoid during startup as it blocks the whole automatism.  Also, the application must be started inside a terminal, because it generates logging output on stdout that I need to be able toi check with a remote desktop viewer at any time.


Finally, I need to wrap the command line above inside a shell-script app_launcher.sh for handling application crashes and restarting the application inside the script automatically.


My idea was to to add the script in /etc/sudoers and then set the owner to the script to root and give only him the rights for execute the script +rwx.


```
app_launcher ALL = NOPASSWD: /home/root/app_launcher.sh

```

The user that gets logged on automatically within the ubuntu desktop during startup is "app_launcher" and then I could use a xdg autostart script:

```
[Desktop Entry]
Type=Application
Exec=gnome-terminal --command "sudo -E nice --19 /home/app_launcher/app_launcher.sh"
Hidden=false
X-Gnome-Autostart-enabled=true
Name=Autostart app_launcher.sh
Comment=

```

to launch the script as root and pass the parameters along.

Do you think that this is the easiest way of doing this? I definitely need the terminal and live logging along with the desktop, so executing it as a background service or cron-job is not an option for me.

Philipp

---

### Post by TheFu on 2021-06-24
I would do the system start up stuff (the sudo part) in a systemd "unit file" and the part that needs to interact with the desktop with a script (not .desktop) launched using the autostart stuff.

No need to make this complex.

BTW, /home/root/ is incorrect. The HOME for the root userid is /root/ ... this is for a number of reasons.  The *Linux File System Hierarchy Standards* say what goes where and why.

Whenever scripting, use the entire, complete, full, path to any programs.  
sudo ---> /usr/bin/sudo

And there should be some output logs from the script or trying to figure out what bad thing happened will be difficult.

---

### Post by kalladan on 2021-06-26
Thank you for your answer, I will try that out.

---

### Post by TheFu on 2021-06-26
> **kalladan said:**
> Thank you for your answer, I will try that out.

Best to get it working. Somethings details get missed (my bad) or misunderstood.  And sometimes the suggested idea isn't workable.  In general, I don't want to have sudo inside any scripts.  I want to run the entire script with sudo so I really understand what it is doing or run it under the required userid with any environment necessary configured.

We really want you to get this working.  Normally, a SOLVED thread will make me 'unwatch', but I'll leave this one watched for a few more weeks so we can solve any issues together.

---

### Post by dragonfly41 on 2021-06-26
I suggest just one approach ..  look at Albert launcher to automate app launching at startup and auto return log files to remote administrator.
You can write custom python extensions. And it is easy for desktop user to refer to various apps and documents. I have set [Num+Enter] (right side of keyboard) as my hot key in Albert preferences to launch query popup..

---

