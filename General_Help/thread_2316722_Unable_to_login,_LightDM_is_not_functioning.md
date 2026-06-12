---
title: "Unable to login, LightDM is not functioning"
date: 2016-03-10
forum: General Help
---

### Post by mirul1996 on 2016-03-10
Hello, I have a problem regarding my Xubuntu laptop. It is an Acer Aspire TimelineX 4820TG running on Xubuntu 15.10. The laptop was fine until a few days ago when I was updating/installing some new packages when I restarted the machine. I was unable to access the login screen and it seems to be hanging at that stage. However I was fortunately can still access the system though the advanced options during boot and access the system using recovery. The system can boot perfectly and I can login although with limited drivers. Since I am still new to Ubuntu what logs should I attached and where to find it? I hope some body can help me. Thanks.

---

### Post by Le3eVolfoni on 2016-03-11
Write the following command to reconfigure your lightdm

```
sudo dpkg-reconfigure lightdm
```

If it does not work, try with theses lines

```
sudo update-rc.d lightdm remove
sudo update-rc.d lightdm defaults
sudo update-rc.d lightdm enable
```

Check your /etc/init.d/lightdm file as well

```
sudo gedit /etc/init.d/lightdm
```

You are supposed to find this (if not change what needs to be changed)

> HEED_DEFAULT_DISPLAY_MANAGER=false

And finally take a look to the /etc/X11/default-display-manager file

```
sudo gedit /etc/X11/default-display-manager
```

Copy/paste the following line in this file (it should be the only line in the whole file)

> /usr/sbin/lightdm

Did you start having this issue after you changed anything that would be linked with your graphic card, like nvidia drivers?
Anyway, I hope it helped.

---

