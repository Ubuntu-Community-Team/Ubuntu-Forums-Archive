---
title: "Launching a Bash Script Using a Desktop Icon and at Startup"
date: 2014-07-30
forum: General Help
---

### Post by daniel171 on 2014-07-30
Hi,

We are using a Lubuntu system for [XIBO]("http://xibo.org.uk/") signage clients. The Client app is written in python and is launched with this simple bash script.

```
cd /opt/xibo/pyclient/client/python
/usr/bin/python /opt/xibo/pyclient/client/python/XiboClient.py


```
What I've done is saved the bash script as "run.sh" on the desktop and created a desktop icon "launchXIBO.desktop" which contains the following


```
[Desktop Entry]
Version=1.0
Name=XIBO Launcher
Comment=LaunchXIBO
Exec=sh /home/xiboclient/Desktop/run.sh
Terminal=true
Type=Application

```


I then made the scrip and desktop icon executable and gave them full read and write access. Double clicking "run.sh" on the desktop works fine, however running the script by double clicking the desktop icon "launchXIBO.desktop" has thus far been to no avail. Nothing at all happens when I double click on "launchXIBO.desktop".  The reason this is a problem is because my ultimate goal is to launch the script at startup and the only way I know to make that happen is to place a copy of "launchXIBO.desktop" into the startup folder located at /etc/xdg/autostart. 

Is there another way to achieve this? I must have overlooked something in the method above. Any help would be much appreciated. I should also mention that I am using Lubuntu 12.04.

Thanks!
Daniel

---

### Post by linux_dream on 2014-07-30
I am also using Lubuntu and have a similar "problem" about the .desktop file.
What worked for me was that instead of ```
Exec=sh /home/xiboclient/Desktop/run.sh
```
I would put ```
Exec=lxterminal -e /home/xiboclient/Desktop/run.sh
```
Anyway keep us updated about if this works for you too.

---

### Post by daniel171 on 2014-07-31
Thanks for the reply.  Unfortunately I got the same result when I used [COLOR=#000000][FONT=Ubuntu Mono]Exec=lxterminal -e /home/xiboclient/Desktop/run.sh[/FONT][/COLOR]

---

### Post by linux_dream on 2014-07-31
> **daniel171 said:**
> Thanks for the reply.  Unfortunately I got the same result when I used [COLOR=#000000][FONT=Ubuntu Mono]Exec=lxterminal -e /home/xiboclient/Desktop/run.sh[/FONT][/COLOR]

Hmm so this doesn't even run lxterminal?
I forgot to mention that if you try ```
Exec=lxterminal -e /home/xiboclient/Desktop/run.sh
```
then change the line ```
Terminal=true
``` to ```
Terminal=false
```.

So that your file.desktop would look like ```
[Desktop Entry]
Version=1.0
Name=XIBO Launcher
Comment=LaunchXIBO
Exec=lxterminal -e /home/xiboclient/Desktop/run.sh
Terminal=false
Type=Application
```

If this fails too, I am out of ideas and I'll wait with you others suggestions. But I am slightly confident it will work...

---

### Post by daniel171 on 2014-07-31
It worked! Thanks!

---

