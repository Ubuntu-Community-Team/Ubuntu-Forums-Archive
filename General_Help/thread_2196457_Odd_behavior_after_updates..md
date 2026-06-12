---
title: "Odd behavior after updates."
date: 2013-12-29
forum: General Help
---

### Post by Tristan_Williams on 2013-12-29
I run a custom version of Ubuntu 13.10 Minimal
I have xfce4, numix gtk theme, and whiskermenu-plugin (those are the related software in this problem)

I update my system every day with the script shown below:
```

#!/bin/bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg --get-selections > ~/.pkg-backup
sudo cp /etc/apt/sources.list > ~/.source-backup

```

This morning I ran the script and everything went fine. 

There was an update for xfce4-whiskermenu-plugin.
First thing I notice is that now, there is a "switch users" button on the menu plugin. The button doesn't work because I don't have lightdm, gdm, xdm or any of those things, because I login through tty1 (that is irrelevant, I know...)

Anyways the problem...

I have the following notification settings:
Theme == Numix Daily
Default position == Bottom Right
Dissapear after [10] seconds
Opacity == 90%

For some reason, after the update, notifications appear in the top right, and are not of the right theme...
I have tried changing the settings and no matter what I set them to, it always pops up as Greybird theme in the top right corner...

What can I do to fix it?

---

### Post by Toz on 2013-12-29
This might mean that you have some other notification daemon running. Which notification daemon is running? xnotifyd (the one installed with xfce4) or possibly another one (notification-daemon, dunst). Also check to see which are installed.

Where do you go to change the notification settings? Settings Manager -> Notifications?

---

### Post by Tristan_Williams on 2013-12-29
To change the settings I go to Settings manager -> Notifications.
And as far as I know theres not any other notification daemons installed besides xfce4-notifyd

---

