---
title: "Lightdm-gtk-greeter persistent wallpaper"
date: 2014-07-01
forum: General Help
---

### Post by Tristan_Williams on 2014-07-01
I am running Xubuntu 14.04

By default, the wallpaper in the lightdm-gtk-greeter login changes according to which user is selected.

How do I change it so that the wallpaper completely ignores individual users wallpapers, and is set to its own persistent wallpaper.
I hate looking at other peoples wallpapers because most of them have ridiculous, unprofessional wallpapers, like on person who has
an entire screen of DIET WATER!

---

### Post by Kirboosy on 2014-07-02
It looks like you just need to is edit a schema file. So it should be rather straightforward.

[LightDM Ubuntu wiki]("https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper")

Hope that helps!
~Caboose

---

### Post by Dennis N on 2014-07-02
> **Caboose885 said:**
> It looks like you just need to is edit a schema file. So it should be rather straightforward.

[LightDM Ubuntu wiki]("https://wiki.ubuntu.com/LightDM#Changing_the_Wallpaper")

Hope that helps!
~Caboose

But, since Xubuntu 14.04 doesn't use Unity Greeter (it uses lightdm-gtk-greeter), it is not clear which (if any) schema could be edited. After looking, I didn't see any relevant file.

The reference to lightdm-gtk-greeter in the wiki section "Changing the Wallpaper" is specific for Lubuntu (which does not by default display the user wallpaper on the login screen). The lightdm-gtk-greeter.conf  in Xubuntu 14.04 also has a background= setting, but it is ignored.

Also looking for a solution Tristan_Williams' question.

---

### Post by ihoe3fze on 2014-07-02
This behavior was implemented in latest greeter version. You need version from daily ppa:
[https://launchpad.net/~lightdm-gtk-greeter-team/+archive/daily](https://launchpad.net/~lightdm-gtk-greeter-team/+archive/daily)

It's **unstable** and had some changes in configuration (***indicators*** option works in slightly different way now).

The key you need:
user-background=false

---

### Post by Dennis N on 2014-07-02
> **ihoe3fze said:**
> This behavior was implemented in latest greeter version. You need version from daily ppa:
[https://launchpad.net/~lightdm-gtk-greeter-team/+archive/daily](https://launchpad.net/~lightdm-gtk-greeter-team/+archive/daily)

It's **unstable** and had some changes in configuration (***indicators*** option works in slightly different way now).

The key you need:
user-background=false

Thanks for the info. You've tried this in Xubuntu 14.04? In what file will this key be found?

---

### Post by ihoe3fze on 2014-07-02
Yes, it must works. You need to edit this file: /etc/lightdm/lightdm-gtk-greeter.conf

```
[greeter]
...
background=your background
# true by default
user-background=false
...
```

As I said, it is unstable version so be ready for some bugs.

---

### Post by Dennis N on 2014-07-02
Thanks for the additional details!

---

