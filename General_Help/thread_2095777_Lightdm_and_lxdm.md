---
title: "Lightdm and lxdm"
date: 2012-12-17
forum: General Help
---

### Post by Mopar1973Man on 2012-12-17
Ok. I need a bit of help gang. I managed to install and fire up Lxdm on Ubuntu 12.04 but now I want to switch back to Lightdm but when I use...

```
sudo dpkg-reconfigure lightdm
```

I get the menu to select the DM I wish I select Lightdm and then reboot. Now I get a text login into terminal. But if I type...

```
sudo lightdm
```

I get the normal Ubuntu login again. 

So how do I re-hook the Lightdm back to Ubuntu again?

---

### Post by slixz85 on 2012-12-17
did you check out this website. I believe this is all you need you might of missed out on the greeter gtk [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)
that also tells you how to configure the lightdm.conf file

---

### Post by Mopar1973Man on 2012-12-17
> **slixz85 said:**
> did you check out this website. I believe this is all you need you might of missed out on the greeter gtk [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)
that also tells you how to configure the lightdm.conf file

LighDM configuration is governed by the **lightdm.conf** file, _**however it's not suppose to be directly edited**_, instead use: 

```
lightdm-set-defaults
```Results...

```
michael@mopar1973man:~$ lightdm-set-defaults
lightdm-set-defaults: command not found
```Still lost...

Also I re-ran...

```
sudo dpkg-reconfigure lightdm
```

...and selected lxdm and it now went back to lxdm just fine. But will not go back to lightdm? (Shrug smiley)

---

### Post by slixz85 on 2012-12-18
sorry man. gotta leave for work i pasted this try these right fast and then sudo dpkg --configure -a in case you got any broken packages then sudo dpkg-reconfigure lightdm. if no one says anything i be back tomorrow and oh yeah if u dont need two lxdm and lightdm then sudo apt-get purge lxdm before all those other commands i just said.

peppermint@TGIL7 ~ $  /usr/lib/lightdm/lightdm-set-defaults
Wrong usage of the command
Usage:
  lightdm-set-defaults [OPTION...] - set lightdm default values

Help Options:
  -h, --help                  Show help options

Application Options:
  -d, --debug                 Enable debugging
  -k, --keep-old              Only update if no default already set
  -r, --remove                Remove default value if it's the current one
  -s, --session               Set default session
  -g, --greeter               Set default greeter
  -a, --autologin             Set autologin user
  -i, --hide-users            Set greeter-hide-users to true or false
  -m, --show-manual-login     Set show-manual-login to true or false
  -l, --allow-guest           Set allow-guest to true or false

---

### Post by Mopar1973Man on 2012-12-18
Give me a bit of time and I'll be back to this project really soon I'm busy re-working my laptop right now with Ubuntu... ;)

---

### Post by Mopar1973Man on 2012-12-25
Solved...

I figured it out. Now I'm not a wizard to the terminal box yet but through Webmin 1.610 I manage to figure it out. 

Say your on lxdm and want to switch back to lightdm. So what I did was gone into [Webmin]("http://www.webmin.com/") in the bootup and shutdown section of the system. Changed lightdm to be booted at next bootup and then disabled lxdm. Then ran.

```
sudo dpkg-reconfigure lightdm
```Then selected Lightdm from the screen menu.

Then...

```
sudo reboot now
```Presto. Back to Lightdm... ;)

---

