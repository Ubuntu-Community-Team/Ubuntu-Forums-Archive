---
title: "Login screen, dconf-editor"
date: 2014-10-26
forum: General Help
---

### Post by nickjanoyan on 2014-10-26
I'm running a fresh install of Ubuntu 14.10. I changed my desktop wallpaper and I wanted to change the login wallpaper too, so I was looking around for a tutorial. I read an article explaining that I need to install dconf-editor. I did everything explained in the tutorial and set the path to the picture I wanted (Pictures/Wallpapers/lain.jpg) and restarted my computer. When I restarted it I didn't see my wallpaper or even the default login screen wallpaper. All I saw was a dark purple wallpaper and whenever I log in the screen glitches and looks messed up for a few seconds and then logs me in. After that I ran this command hoping it would undo any changes I made.

```
sudo apt-get purge dconf-editor
```

I restarted my computer and I still had the same problem. Below is the tutorial I used to do this. I really just wanted to have my desktop wallpaper be the same as my login screen wallpaper instead of the default. If there's any way to fix what I screwed up and help me do this I would greatly appreciate it. Below is the tutorial I followed. 

> Want to **remove the white dots** and set your **log-in screen background image different to your desktop wallpaper**? Well, this simple tutorial will show you how.
 Below steps will give **lightdm** user access to the X-Server and open **dconf-Editor** to change the settings of Unity Greeter.
 **1.** Press Ctrl+Alt+T on keyboard to open the terminal. When it opens, run the command below to install dconf-editor:
 ```
sudo apt-get install dconf-editor 
```[B]
2.[/B] Run command to get the root user privilege:
 ```
sudo -i 
```[B]
3.[/B] Allow user **lightdm** to create a connection to the X server:
 ```
xhost +SI:localuser:lightdm 
```
**4.** Switch to user **lightdm** in this terminal window.
 ```
su lightdm -s /bin/bash 
```[B]
5.[/B] Now you can start the dconf-editor via this user by running:
 dconf-editor When the tool opens, navigate to **com –> canonical –> unity-greeter**. Then change the background value to your custom image and disable both **draw-grid** and **draw-user-backgrounds**



This is exactly what I did. Hopefully someone can help me. I really want to avoid re-installing Ubuntu right after I installed it.

---

### Post by grahammechanical on 2014-10-26
As far as I know dconf-editor has been part of the default installation for the last year. Old tutorials may not apply to new Ubuntu releases. If you had not removed dconf-editor you could have opened it and gone to com>canonical>unity-greeter and selected background and then simply clicked the button labelled "Set to default."

You need to undo the changes that you did. There must have been something wrong either with the image that you choose or the path that you gave to the image. The default value is

> /usr/share/backgrounds/warty-final-ubuntu.png


Regards.

---

### Post by nickjanoyan on 2014-10-26
I don't think it was installed by default. When I typed in ```
sudo apt-get install dconf-editor
``` it didn't give me a message saying it was already installed. Do you recommend I re-install dconf-editor and try it again? I didn't click on the set to default button, so maybe that's why it didn't work.

---

### Post by nickjanoyan on 2014-10-26
I re-installed it and did what you said and it's working fine again. Granted it's the default wallpaper, but at least it's not glitching anymore. I still can't seem to change the wallpaper though. Here's what I have. Maybe I'm doing something wrong.

[https://cdn.mediacru.sh/WBnOAkIaskQX.png](https://cdn.mediacru.sh/WBnOAkIaskQX.png) (I'm linking to the image because it's too big to fit into a post).

I've tried with and without quotes and I originally had it in my pictures folder, but then I moved it to /usr/share/backgrounds and I changed the permissions so they match the other wallpapers in that folder. It keeps showing the default wallpaper now though. Is there a button I'm supposed to click after I type in my image path or a setting I'm not enabling/disabling?

EDIT: I solved it. I was launching dconf-editor as my regular user account and that's why the wallpaper wasn't changing. I had to follow the steps that I mentioned in my first post. I think the reason it wasn't working before was because the permissions weren't correct. The picture has to be readable to all users. Now everything is working fine.

---

