---
title: "KDE lockup on boot"
date: 2015-05-11
forum: General Help
---

### Post by masstumor29 on 2015-05-11
I'm having an issue with the system locking up on boot, I can move the mouse around but I am unable to click anything. Same with the keyboard, I just got my new ssd drive in today did a fresh install ubuntu 14.04. After the install I did all the updates and upgrade. After that I installed KDE Via 

```
sudo apt-get install kde-full
```

Everything went well no problems, chose kdm as defaultdesktop environment. Once again everything was fine. Did the apt-get update after that was installed had no issues. I was making everything look how I wanted it to, went to edit the login screen and this is where my problem started. I could not get my login themes to show when I installed them so I closed the system settings and used

```
sudo systemsettings
```

When the system settings opened up I installed the one I wanted to use as my login screen. Everything seemed fine untill I restarted the computer. That is when everything locked up on me after login. I was able to get the default back by pressing CTRL + ALT + F1 this brought me to a text only login screen. I logged in with my info then used the command

```
startx
```

After that it showed the default wallpaper nothing else but I was able to bring up the terminal using CTRL + ALT + T. When the terminal opened back up I entered the command 

```
sudo dpkg-reconfigure kdm
```

clicked ok and chose lightdm, after that I entered

```
sudo startx
``` 

then typed reboot. This gave me back the original look and feel of a fresh install and everything was working fine again. So I went to the terminal and typed systemsettings went and changed the login splash back to the default thinking that was the issue because I used sudo to install the new one. After I swaped back to the default kde login splash I swapped my desktop environment back to kdm restarted logged in and still had the same issue. Mouse moves but unable to click on anything and unable to use the keyboard unless I hit CTRL + ALT + F1. Everything works fine with the lightdm. But I prefer the look of kde. Is there a way I can fix this issue, I know it has to do with the login splash because that's when the problem started.

Just don't want to end up having to uninstall kde and reinstall I have slow net that took a few hours to download.

---

### Post by masstumor29 on 2015-05-11
Problem solved, issue was in a config file changed when I installed the theme as sudo, uninstalled the theme and reverted the config no more issue.

---

### Post by Bucky Ball on 2015-05-11
Good news. Please mark the thread as solved to help others. See the second link in my signature.

---

### Post by mastablasta on 2015-05-11
> **masstumor29 said:**
> Problem solved, issue was in a config file changed when I installed the theme as sudo, uninstalled the theme and reverted the config no more issue.


use kdesudo when using graphical apps. 

sudo is for cli apps only.

---

