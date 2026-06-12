---
title: "Ubuntu dock only show applications icon"
date: 2022-04-24
forum: General Help
---

### Post by mickee384 on 2022-04-24
Hi!

After upgrading to Ubuntu 22.04 from 20.04, the Ubuntu Dock only shows the applications icon, not favourites or running apps. The whole dock shows up when viewing Activities. Is there any way to fix this? As a workaround I installed Plank and the dash to plank Gnome Shell extension, but I prefer the Ubuntu Dock. Here is a picture. 
[IMG]https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjDORLRvI1f0r2UEmlbRKdC1VZ15DRlRzLy7kkkcCVFcR0rID0b2NB1kNIvlHdRtiFV8c_etBFM69Z8iQbDS0xnC7D9e1RBupeFJrr_6OAf9rcmWAP1vcwdoMXMoFurHcm_GdiqPF-EXBuLvTWO-5W_nycjeBMzIqNSfJgy_juBlm3jZDB7LFk/s480/Screenshot%20from%202022-04-24%2011-51-14.png[/IMG]

---

### Post by mickee384 on 2022-04-30
Note this issue is happening on my main PC and also my laptop. Tried using Ubuntu Dock, and the dash to dock Gnome Shell extension, same issue.

---

### Post by vanadium on 2022-05-03
Something went wrong with your upgrade for sure, and .desktop launchers are not being picked up.

- As a test, create a new temporary account, log in there and see if the issue happens there. This allows to identify whether the issue is systemwide or related to that specific account.
- Unlikely the environmental variable would not be set, but check with the command "printenv XDG_DATA_DIRS".

---

### Post by mickee384 on 2022-05-03
Thanks for your reply! It indeed must be somthing in my profile (on 2 computers!) When I created a new user the dock and the gnome shell extension works fine. Is there a way to fix my profile without creating a new one or migrate the profile to a new one? Its quite involved and has a lot of data in it. Here is the output of printenv XDG_DATA_DIRS

```
/usr/share/ubuntu-xorg:/usr/share/gnome:/home/mickee/.local/share/flatpak/exports/share:/var/lib/flatpak/exports/share:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop:/var/lib/snapd/desktop

```

Thanks again for the  reply. I find it strange that this issue has happened on my laptop and desktop after upgrading 20.04 LTS to 22.04 LTS

---

### Post by mickee384 on 2022-05-03
If I create a new profile and copy the home directory to new profile using grsync, and also include the hidden files will the issue I'm having with the old profile show up in the new profile?

---

### Post by mickee384 on 2022-05-10
I am thinking it is because i used nemo-desktop to manage the desktop, prior to upgrade, as 20.04 did not allow for the use of the desktop as a working folder and the Gnome Shell extensions were not available at the time? I literally do not remember how to run the desktop without using nemo. I now have access to desktop after re enabling nemo. The Ubuntu dock however is still toast.  The system is working fine with plank and the dash to plank extension. Should I remove plank, create a new user and profile then use grsync to move ~/ to the new profile, hidden files as well? I actually prefer to use the built in dock over Plank, but if not I will get used to it as it works 99% the same as the Ubuntu dock.

---

### Post by sepehrbhl on 2022-08-23
change your "dash-to-dock" key with uncustomized data or default data.


1- create a .ini file:
```
$ touch ~/dconf-dock.ini
```

2- open file and paste values:
```
$ vim ~/dconf-dock.ini
``` 

```
[/]
dash-max-icon-size=40
dock-fixed=false
dock-position='BOTTOM'
extend-height=false
multi-monitor=true
show-mounts=false
show-mounts-network=false
show-mounts-only-mounted=true
show-trash=true

```

4- save 


5- load .ini file data to dconf key:
```
dconf load /org/gnome/shell/extensions/dash-to-dock/ < ~/dconf-dock.ini
```

6- you can delete ~/dconf-dock.ini  file at the end. ;)
```
rm dconf-dock.ini
```     



[COLOR=#33666b][FONT=Calibri]===-=-=-=-=-=-===-=-=-=-=-=-=-=== [/FONT]
[/COLOR]also you can check key before and after change:
```
dconf dump /org/gnome/shell/extensions/dash-to-dock/
```
[COLOR=#33666b][FONT=Calibri]===-=-=-=-=-=-===-=-=-=-=-=-=-=== [/FONT][/COLOR]

---

### Post by mickee384 on 2022-08-23
Thanks! I will try this

---

### Post by vanadium on 2022-08-23
An easier approach to reset the Ubuntu dock configuration data to factory defaults will be:

```

dconf reset -f /org/gnome/shell/extensions/dash-to-dock/

```

---

### Post by chuckasimov on 2022-08-31
Thanks, this worked fine for me :)

---

### Post by zack1119 on 2022-11-28
> **vanadium said:**
> An easier approach to reset the Ubuntu dock configuration data to factory defaults will be:

```

dconf reset -f /org/gnome/shell/extensions/dash-to-dock/

```

I know this thread is old, but just wanted to say thank you. I had same problem since installing a fresh copy of Ubuntu 22.04 this worked great for me though.

---

