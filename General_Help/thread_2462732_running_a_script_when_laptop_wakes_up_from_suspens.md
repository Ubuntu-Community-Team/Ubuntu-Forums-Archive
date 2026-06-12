---
title: "running a script when laptop wakes up from suspense"
date: 2021-05-26
forum: General Help
---

### Post by monkeybrain20122 on 2021-05-26
Hi, I have a script that enables both edge scrolling and two finger  scrolling on my touchpad (system settings' mouse and touchpad gui  doesn't have option for edge) I put in it startup applications and it  works as expected if I reboot or logout and then login. But it doesn't  activate when laptop wakes from suspense. I would like to call the script when the laptop wakes up with another script. This is the script I want to invoke.

```
#!/bin/bash     

#title          :touchpad.sh
#description    :Hook script to enable edge and two finger scrolling when waking from suspend 
#author         :monkeybrain20122  
#date           :20171216
#version        :1      
#usage          :./touchpad.sh
#notes          :Script gets called from /lib/systemd/system-sleep
#============================================================================================================================================================


sleep 5
declare -x DISPLAY=":0.0"
declare -x XAUTHORITY="/home/bernard/.Xauthority"


synclient VertEdgeScroll=1 VertTwoFingerScroll=1 HorizTwoFingerScroll=1 HorizEdgeScroll=1
```

I posted an identical thread on this forum before [https://ubuntuforums.org/showthread.php?t=2380045](https://ubuntuforums.org/showthread.php?t=2380045), the solution there by untrustytahr worked like a charm for Ubuntu16.04 but no longer works for 20.04, same laptop and a clean install.

Appreciate any help.

---

### Post by monkeybrain20122 on 2021-05-27
bump

---

### Post by &amp;KyT$0P# on 2021-05-28
Is your script not running at all on wake from suspend, or is it running but not working?

---

### Post by monkeybrain20122 on 2021-05-28
> **halogen2 said:**
> Is your script not running at all on wake from suspend, or is it running but not working?

I don't know if it is running at all, the effect doesn't show. But the script (touchpad.sh, the script that the wakeup script supposedly invokes) works on booting up and logging in and also right clicking it or running in terminal works.

---

### Post by &amp;KyT$0P# on 2021-05-28
> **monkeybrain20122 said:**
> I don't know if it is running at all, 

You can check this by using [FONT=Courier New]logger[/FONT] in your script to log an entry to [FONT=Courier New]/var/log/syslog[/FONT] -
```
logger 'touchpad.sh ran'
```
Refer to [FONT=Courier New]man logger[/FONT] for more info

If it is not running, does it make any difference if, to run it on wake from suspend, you instead use a systemd service like [this]("https://ubuntuforums.org/showthread.php?t=2372519&p=13690740&viewfull=1#post13690740")?

---

### Post by monkeybrain20122 on 2021-05-29
Hi, thanks, it works now, following your post in the link to create a systemd service.

To recap, I created a file called start_touchpad.service in /etc/systemd/system, made it executable, then run

```
sudo systemctl enable start_touchpad
```

Here is my start_touchpad.service 

```

[Unit]
Description=activate touchpad script when system awakens from suspense
Before=sleep.target
StopWhenUnneeded=yes

[Service]
Type=simple
RemainAfterExit=yes
ExecStart=-/home/monkeybrain/Scripts/touchpad.sh suspend
ExecStop=-/home/monkeybrain/Scripts/touchpad.sh resume

[Install]
WantedBy=sleep.target
```

touchpad.sh is as in my first post.

Thanks again!

---

### Post by monkeybrain20122 on 2021-05-29
Just curious why the old solution (putting a wakeup script in /lib/systemd/system-sleep, see my link in first post) has stopped working since the solution that does work from halogen2 is also from 2017.

---

