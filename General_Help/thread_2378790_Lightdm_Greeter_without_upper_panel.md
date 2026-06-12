---
title: "Lightdm Greeter without upper panel"
date: 2017-11-27
forum: General Help
---

### Post by forneus2 on 2017-11-27
I am trying to find the way to remove the upper bar at the login. Just want to have a box with user-password in the center of the screen. I cannot find the line to edit in the config file - there is one about bottom panel, but which code configures the upper one?

---

### Post by vasa1 on 2017-11-27
> **forneus2 said:**
> I am trying to find the way to remove the upper bar at the login. Just want to have a box with user-password in the center of the screen. I cannot find the line to edit in the config file - there is one about bottom panel, but which code configures the upper one?Which is this config file? And please mention your distro and its version.

---

### Post by forneus2 on 2017-11-27
I was looking here:
```
user@edge:~$ cd /usr/share/lightdm/lightdm.conf.d
user@edge:/usr/share/lightdm/lightdm.conf.d$ ls
20-lubuntu.conf             50-guest-wrapper.conf
50-disable-log-backup.conf  50-xserver-command.conf
50-greeter-wrapper.conf     60-lightdm-gtk-greeter.conf
user@edge:/usr/share/lightdm/lightdm.conf.d$ 
```

but none of those files has an option to edit upper panel. Can't remember which file hides the bottom panel - I found one thread here but it was of no use since I don't have a bottom panel.

Lubuntu 16.04 is my distro.

---

### Post by forneus2 on 2017-11-30
Anything?

---

### Post by tea for one on 2017-11-30
There is a settings editor available via synaptic.

[https://launchpad.net/lightdm-gtk-greeter-settings](https://launchpad.net/lightdm-gtk-greeter-settings)

I'm not sure if you can completely remove the top panel but, with a bit of experimentation, you may be able to remove all the indicators.

Then, you could possibly merge the panel colour with a suitable background.

---

### Post by forneus2 on 2017-11-30
> **tea for one said:**
> There is a settings editor available via synaptic.

[https://launchpad.net/lightdm-gtk-greeter-settings](https://launchpad.net/lightdm-gtk-greeter-settings)

I'm not sure if you can completely remove the top panel but, with a bit of experimentation, you may be able to remove all the indicators.

Then, you could possibly merge the panel colour with a suitable background.

Yes I have the greeter settings installed but the option to hide the upper panel is not there :-(

Merging with custom solid color wallpaper is a smart workaround, but I would like to use it as a last resort... Thanks for the reply though!

---

