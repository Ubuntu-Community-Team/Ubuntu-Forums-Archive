---
title: "Problem getting applications to autostart at start up"
date: 2013-12-24
forum: General Help
---

### Post by rdh61 on 2013-12-24
Hi,


I'm running Lubuntu 13.10 on a desktop computer.


I want Wuala and Ubuntu One to launch automatically on start up. ("Connect automatically when computer starts" is checked in Ubuntu One client, but even so it does not start automatically).  I have dropped their desktop files from /usr/share/applications to .config/autostart, but this doesn't help. 


What else can I do to force them to start automatically?


Many thanks.

---

### Post by vasa1 on 2013-12-24
Things have changed in Lubuntu 13.10.

Edit ~/.config/lxsession/Lubuntu/autostart.
Add the appropriate command on a separate line to the end of the existing file. If such a file doesn't exist, create it with Leafpad or nano.

This is my autostart file:
```
/home/vasa1/.dropbox-dist/dropbox
/home/vasa1/bin/cpu-usage-alert.sh

```
Note that there's no need for the older way of dropping .desktop files into ~/.config/autostart. That doesn't work anymore.

---

### Post by rdh61 on 2013-12-24
Thanks, that's given me a clue. Unfortunately, I am unsure how to formulate the commands to open the applications I have mentioned. Can anyone tell me?

---

### Post by vasa1 on 2013-12-24
> **rdh61 said:**
> Thanks, that's given me a clue. Unfortunately, I am unsure how to formulate the commands to open the applications I have mentioned. Can anyone tell me?I don't use either. Let's hope someone who does comes this way!

---

### Post by Toz on 2013-12-24
For UbuntuOne, the command is:
```
/usr/bin/ubuntuone-launch
```
I don't use Wuala, but according to the [documentation]("https://www.wuala.com/en/download/linux"), this should work:
```
/usr/bin/wuala
```

---

### Post by rdh61 on 2013-12-30
Thank you. In the meantime I found the general answer here, and copied the Exec commands from the .desktop files:

[https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#How_I_can_autostart_a_program_when_logging_into_Desktop](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#How_I_can_autostart_a_program_when_logging_into_Desktop)

---

