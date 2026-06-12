---
title: "i've tried to remove skype with no success"
date: 2020-07-10
forum: General Help
---

### Post by ronjjjg8885 on 2020-07-10
i typed ```
sudo apt-get --purge remove skype
```

anf got ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done

No apt package "skype", but there is a snap with that name.
Try "snap install skype"

E: Unable to locate package skype
```

and the icon of skype is still there.

what did i missed?

thank you!!

---

### Post by HermanAB on 2020-07-10
See what is there:
$ sudo find / -name *skype*

Then simply delete it.

---

### Post by ronjjjg8885 on 2020-07-10
hi thanks
this is what i got
[https://pastebin.com/HatVJEbq](https://pastebin.com/HatVJEbq)

should i type:
```
sudo apt-get --purge remove net-chat-skype
```

for removal?

---

### Post by HermanAB on 2020-07-10
You can try that.

There seems to be at least two copies: /usr/bin/skypeforlinux and /opt/skypeforlinux.

You could put the output of find in a text editor, add rm to it all and then run it as a script.

---

### Post by Impavidus on 2020-07-10
Chances are that the one in /usr/bin is a symlink to the one in /opt.

The output suggests that you installed skype from a PPA. There's a file named /etc/apt/sources.list.d/skype-stable.list. The files named /var/lib/dpkg/info/skypeforlinux.* indicate you've installed a package named skypeforlinux. Probably best to remove that using apt, else you risk confusing apt.

The files in /home/ron/.config/skypeforlinux won't be removed by that. You have to remove those manually.

---

### Post by ronjjjg8885 on 2020-07-10
sorry people but i'm still not sure which commands exactly i should use to remove the actual software.
why did skype made it comilicated btw?
thank you :)

---

### Post by ajgreeny on 2020-07-10
Try ```
sudo apt purge skypeforlinux
```
This assumes you did install it as a .deb package and not as a snap, so show us what you get from command ```
snap list
``` and if that shows a skype snap is installed remove it with ```
snap remove skype
```

---

### Post by ronjjjg8885 on 2020-07-11
i'm trying now
thank you...

i only tried the first two commands because it wanst in the list:
```
snap list
Name                 Version                     Rev   Tracking         Publisher   Notes
canonical-livepatch  9.5.5                       95    latest/stable    canonical*  -
code                 d5e9aa02                    36    latest/stable    vscode*     classic
core                 16-2.45.1                   9436  latest/stable    canonical*  core
core18               20200427                    1754  latest/stable    canonical*  base
gnome-3-28-1804      3.28.0-17-gde3d74c.de3d74c  128   latest/stable    canonical*  -
gnome-3-34-1804      0+git.3009fc7               36    latest/stable/…  canonical*  -
gtk-common-themes    0.1-36-gc75f853             1506  latest/stable/…  canonical*  -
snap-store           3.36.0-80-g208fd61          467   latest/stable/…  canonical*  -
snapd                2.45.1                      8140  latest/stable    canonical*  snapd


```

glad you could assist

---

### Post by ajgreeny on 2020-07-12
Did my ***sudo apt remove skypeforlinux*** suggestion work and have you now have managed to remove it?  
Please tell us if it worked and if so please mark as SOLVED from the Thread Tools menu up-top.

It is a great help to other users searching the forum.

---

### Post by T6&amp;sfpER35% on 2020-07-12
in terminal ```
ls -l /usr/share/applications
```
then look for skype.desktop , [COLOR=#0000ff]copy[/COLOR] that file name

in terminal ```
sudo rm /usr/share/applications/[COLOR=#0000ff]paste-the-filename-here[/COLOR]
```

---

