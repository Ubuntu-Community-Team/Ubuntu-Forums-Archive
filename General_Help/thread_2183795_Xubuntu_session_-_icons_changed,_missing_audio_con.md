---
title: "Xubuntu session - icons changed, missing audio control"
date: 2013-10-26
forum: General Help
---

### Post by dannyboy79 on 2013-10-26
I don't know what happened, i logged into my Xubuntu 12.04.3 running ppa:xubuntu-dev/xfce-4.10 desktop just like I always do (Xubuntu session) chosen in lightdm and all my icons are different, I can't issue ctrl-alt-f2 to bring up the run command box, my speaker icon for controlling audio is gone and I am sure there are other things going on.

Here's the .xsession-errors file
[http://paste.ubuntu.com/6306680/](http://paste.ubuntu.com/6306680/)

I go into settings manager, then appearance and no matter what style I choose the icons don't change. I have already tried logging out, going to tty1, removing the ~/.cache/sessions folder but that didn't fix it.

---

### Post by dannyboy79 on 2013-10-26
ok, i first deleted this file as suggested by a blog I found which also lead to a redhat bug report, which also suggested reinstalling xfce4-settings. so i did both and everything is back to normal. all my icons are there, i can change themes, my sound mixer is back and all is well. Hope this helps others.
```
rm -rf ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
```
not sure if your session settings are stored when you log out but if they are, it may be necessary to log out, go to tty1, remove the file, then log back in. just a thought

```
sudo aptitude reinstall xfce4-settings
```

i did have to log out and back in again for this take effect.

---

