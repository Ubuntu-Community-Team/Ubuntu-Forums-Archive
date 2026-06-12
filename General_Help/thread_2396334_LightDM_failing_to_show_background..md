---
title: "LightDM failing to show background."
date: 2018-07-13
forum: General Help
---

### Post by Furycd001 on 2018-07-13
HI Guys.

Recently LightDM has stopped showing any wallpapers & will only show a black background. I can set a background color, but not an image. LightDM GTK+ Greeter settings shows the following message below.

> LightDM do not have permission to read path: /home/jonny

I'm running xubuntu 16.04.4 which is fully updated....

---

### Post by #&amp;thj^% on 2018-07-14
> **jonny6 said:**
> HI Guys.

Recently LightDM has stopped showing any wallpapers & will only show a black background. I can set a background color, but not an image. LightDM GTK+ Greeter settings shows the following message below.



I'm running xubuntu 16.04.4 which is fully updated....

The image you wish to use will need to placed in "/usr/share/backgrounds"
More info found here: [https://ubuntuforums.org/showthread.php?t=2395279&p=13779801#post13779801](https://ubuntuforums.org/showthread.php?t=2395279&p=13779801#post13779801)

---

### Post by Furycd001 on 2018-07-14
Thanks for the heads up & for the link, but until recently I've always used pictures from /home/jonny/pictures/login. Did a recent update change something to only allow pictures from /usr/share/backgrounds ??

---

### Post by Holger_Gehrke on 2018-07-14
lightDM and the greeter do not run with your user-account (how could they ? Until they're done, the system does not know which user is going to use it ... ) and I don't think they run as root, so images you're going to use as background in the greeter must be readable by everyone and must reside in directories everyone can access. Have you recently changed the mode (chmod) of the image you're using as background ?

Holger

---

### Post by Furycd001 on 2018-07-15
Thank you for your comment, but I don't think that I have changed anything on my system recently. The only thing I can think of is that I temporarily connected via hdmi to a tv to give a demo of something. That was a one off though & my logon screen was working fine after. It's literally been within the past week or two when I booted my system one morning and my logon screen was displaying a black background instead of the usual one. Any background images that I use for logon are kept in /home/jonny/pictures/login/ & are set using LightDM GTK+ Greeter settings from within XFCE. Until now I've never had any problems using pictures from that folder....

---

### Post by #&amp;thj^% on 2018-07-15
I think you are possibly making this harder than it needs to be. :)
Holger_Gehrke is right the greeter dose not run with your user-account (/home/user) Maybe your thinking a Grub image.
By default, images are sourced from /usr/share/backgrounds. You can change the background images directory by editing lightdm/lightdm-gtk-greeter.conf.
I can't remember being able to use an image from any where inside the /home directory with out some kind of permission change.
For example only:

This is where it gets called "/etc/lightdm/lightdm-gtk-greeter.conf"
Mine shows:
```
[greeter]
background = /usr/share/backgrounds/greybird.svg

```
And
[branding]
background_images = /usr/share/backgrounds


More information here: [https://wiki.archlinux.org/index.php/LightDM#Greeter](https://wiki.archlinux.org/index.php/LightDM#Greeter)

---

### Post by Furycd001 on 2018-07-15
I'm definitely not thinking of grub. I've been using LightDM GTK+ Greeter settings from within XFCE for a few years now & have definitely been able to use pictures from /home/jonny/pictures/login/ before. I don't care so much as to how LightDM does or does not run, but more so why I can no longer use the folder I have used for ages now. I get everything that you are saying though....

---

### Post by #&amp;thj^% on 2018-07-15
> **jonny6 said:**
> I don't care so much as to how LightDM does or does not run, but more so why I can no longer use the folder I have used for ages now. I get everything that you are saying though....
I just don't have any clue why  LightDM GTK+ Greeter settings are not working for you at present, I'm just a CLI guy and use the terminal only for changes to "my" system.
And I have just always used "/usr/share/backgrounds" for my source to choose from.
For what it's worth I installed the "LightDM GTK+ Greeter settings" and tried to use an image from my /Pictures location and got the same error "**LightDM dose not have permission to read path: /home/me**" but if I moved that image to "/usr/share/backgrounds" it was then available to use. (The image format was also a .jpeg FWIW)
Any way just trying to help a fellow user out. ;)

---

### Post by ajgreeny on 2018-07-15
My chosen Xfce (Xubuntu) wallpaper image sits in my home and also in /boot/grub so I see it under my grub menu, it is not in the system folder backgrounds, but my lightdm login screen shows the same image before I have logged in, of course.  The permissions of both my images are -rw-r--r-- so can be read by anyone including lightdm; only the owner is different, and the grub image has been reduced to a usable size and 256 colours.

What permissions are set for the image you want to use for lightdm?

---

### Post by again? on 2018-07-15
Right click on your wallpaper folder > properties and give **Read only** permissions to "Others".
Then click yes to apply recursively.

---

### Post by Furycd001 on 2018-07-16
> **1fallen said:**
> I just don't have any clue why  LightDM GTK+ Greeter settings are not working for you at present, I'm just a CLI guy and use the terminal only for changes to "my" system.
And I have just always used "/usr/share/backgrounds" for my source to choose from.
For what it's worth I installed the "LightDM GTK+ Greeter settings" and tried to use an image from my /Pictures location and got the same error "**LightDM dose not have permission to read path: /home/me**" but if I moved that image to "/usr/share/backgrounds" it was then available to use. (The image format was also a .jpeg FWIW)
Any way just trying to help a fellow user out. ;)

Thank you very much for checking on your own system. I've moved the login folder into /usr/share/backgrounds/ & everything works again.

---

### Post by Furycd001 on 2018-07-16
> **ajgreeny said:**
> My chosen Xfce (Xubuntu) wallpaper image sits in my home and also in /boot/grub so I see it under my grub menu, it is not in the system folder backgrounds, but my lightdm login screen shows the same image before I have logged in, of course.  The permissions of both my images are -rw-r--r-- so can be read by anyone including lightdm; only the owner is different, and the grub image has been reduced to a usable size and 256 colours.

What permissions are set for the image you want to use for lightdm?

Permissions for the images I use are the same as what you listed above for yours.

---

### Post by again? on 2018-07-16
> **jonny6 said:**
> Permissions for the images I use are the same as what you listed above for yours.
Check your folder permissions.
When using a folder in $HOME for custom images, both the folder and file need to allow access to "Others".

---

### Post by Furycd001 on 2018-07-16
> **guber2 said:**
> Check your folder permissions.
When using a folder in $HOME for custom images, both the folder and file need to allow access to "Others".

Thanks for the heads up. Everything appears to have the correct permissions. I've moved the folder as per above so I think I can close this off as solved....

---

