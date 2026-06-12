---
title: "How do you stop login screen showing wallpaper?"
date: 2013-01-14
forum: General Help
---

### Post by nezero on 2013-01-14
I'm using [Wallch]("https://apps.ubuntu.com/cat/applications/wallch/") to cycle through all my photo's and it works really well. However when i shutdown and come to login next, the login screen  shows the last photo that was being shown.

I don't want this to happen and [the only post]("http://ubuntuforums.org/showthread.php?t=1951539") i could find has a dirty solution, i don't want to change the permissions for 1000's of photo's.

I have also tried using scripts that run at [logout]("http://ubuntuforums.org/showthread.php?t=1969822&page=2") and although this works, the scripts run after logout. I set the desktop back to original using the following commands.

```
gsettings set org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/warty-final-ubuntu.png'
gsettings set org.gnome.desktop.background picture-options zoom
```

Next time i login my desktop is set back to the warty ubuntu wallpaper, however the login screen still shows the last picture that was on my wallpaper, so it must being set somewhere before logging out and it mustn't be being read from the gnome desktop settings. Does anyone know how to disable this or where the setting is likely to be stored so it edit it with my logout script?

---

### Post by nezero on 2013-01-14
Ok found the setting, though still had some trouble.

Read a [post]("http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594") that told me how do it. Though it didn't work for me.

The post suggest to switch to the lightdm user using the following commands.

```
sudo -i
xhost +SI:localuser:lightdm
su lightdm -s /bin/bash
```
Then change the setting with
```
gsettings set com.canonical.unity-greeter draw-user-backgrounds 'false'
```
How ever this did not seem to work for me as if i
```
cat /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
i still had
```
    <key name="draw-user-backgrounds" type="b">
      <default>true</default>
      <summary>Whether to draw user backgrounds</summary>
    </key>

```
in the configuration file.

So i just hacked it using 
```
sudo nano /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
to look like 
```
    <key name="draw-user-backgrounds" type="b">
      <default>false</default>
      <summary>Whether to draw user backgrounds</summary>
    </key>
```

This works and the problem is solved, though i would be interested in finding out why i couldn't change the setting using gsettings.

---

