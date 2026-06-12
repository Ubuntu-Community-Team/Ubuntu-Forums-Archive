---
title: "Auto lock screen after 5 minutes"
date: 2022-06-15
forum: General Help
---

### Post by andrewcrawford131 on 2022-06-15
Hi all I am trying to afk on my game ie leave it running while I'm not there but I have ran into a problem everything 5 minutes is up it locks the screen I have tried a few things to try stop it but nothing has worked I'm on xubuntu 22 one thing I found to try I could do as there is no option to enter system settings

---

### Post by ajgreeny on 2022-06-15
The best way to system settings is, in my opinion,  to open **_Settings Manager_** from the menu.
In that you will find many places which can affect screen locking but the most likely are the **Screensaver** and **Power-Manager**.

---

### Post by mIk3_08 on 2022-06-15
> **andrewcrawford131 said:**
> Hi all I am trying to afk on my game ie leave it running while I'm not there but I have ran into a problem everything 5 minutes is up it locks the screen I have tried a few things to try stop it but nothing has worked I'm on xubuntu 22 one thing I found to try I could do as there is no option to enter system settings
Try to run command below using your terminal. To access terminal ctrl and alt + T or just look at it under the application software in your xubutu operating system
```
gnome-control-center
```
If you try to run gnome-control-center and get command not found, just try to install it with the command below:
```
sudo apt install gnome-control-center
```
Regards and cheers.

---

### Post by ajgreeny on 2022-06-15
> **mIk3_08 said:**
> Try to run command below using your terminal. To access terminal ctrl and alt + T or just look at it under the application software in your xubutu operating system
```
gnome-control-center
```
If you try to run gnome-control-center and get command not found, just try to install it with the command below:
```
sudo apt install gnome-control-center
```
Regards and cheers.
Don't bother with this if you're not using the default gnome DE of Ubuntu; Xubuntu has its own version, the **xfce4-settings-manager** as I mentioned above.

---

### Post by mIk3_08 on 2022-06-16
> **ajgreeny said:**
> Don't bother with this if you're not using the default gnome DE of Ubuntu; Xubuntu has its own version, the **xfce4-settings-manager** as I mentioned above. 
Thanks ajgreeny. I just thought that xubuntu can also use gnome settings as xubuntu is also one of the flavor of Ubuntu Operating System which gnome is the default DE. If xfce won't work then try to use gnome DE and run gnome setting. But thanks again for the correction. Glad to be corrected. Regards and cheers.

---

### Post by mIk3_08 on 2022-06-16
> **andrewcrawford131 said:**
> Hi all I am trying to afk on my game ie leave it running while I'm not there but I have ran into a problem everything 5 minutes is up it locks the screen I have tried a few things to try stop it but nothing has worked I'm on xubuntu 22 one thing I found to try I could do as there is no option to enter system settings
you can also run the command below for the direct access to the display setting
```
 xfce4-display-settings 
```
Regards and cheers.

---

