---
title: "2 Network Icons"
date: 2018-10-26
forum: General Help
---

### Post by linuxyogi on 2018-10-26
Hi,

I am using Lubuntu 18.04. I see 2 network icons in the notification area. How to stop duplicates from appearing ?

---

### Post by him610 on 2018-10-27
I had same issue several weeks ago. I verified which icon worked (they both did) then I deleted one. Issue has not reoccurred. What causes it? Beats me, I could not come up with a cause. A mystery at this point. Maybe someone else will come up at something.

---

### Post by missmoondog on 2018-10-28
> **him610 said:**
> I had same issue several weeks ago. I verified which icon worked (they both did) then I deleted one. Issue has not reoccurred. What causes it? Beats me, I could not come up with a cause. A mystery at this point. Maybe someone else will come up at something.

i get the same thing as far as 2 network icons just about every other time i start one of my machines that has lubuntu 18.04.1. how did you simply delete the icon as i can find no way to do that? i can go into network settings and edit connections and remove 1 of them from there and then log off and back on, and it will be gone, but comes back after next reboot or 2. some times there's only 1 wired connection showing up in settings, so if i delete that one, i get rid of second icon but have to go through setting up my static ip and stuff again.

thank you

---

### Post by linuxyogi on 2019-06-06
> **him610 said:**
> I had same issue several weeks ago. I verified which icon worked (they both did) then I deleted one. Issue has not reoccurred. What causes it? Beats me, I could not come up with a cause. A mystery at this point. Maybe someone else will come up at something.

How did you delete that one network icon ?

---

### Post by #&amp;thj^% on 2019-06-06
First try:
```
cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
lxpanelctl restart

```
_And sometimes this is enough:_
```
lxpanelctl restart
```
And **>>only<<** if the above dose not work>>>Try adding "X-GNOME-Autostart-Delay=10" in </etc/xdg/autostart/nm-applet>

---

### Post by linuxyogi on 2019-06-07
> **1fallen said:**
> First try:
```
cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
lxpanelctl restart

``` 

^^ This didn't work.

> **1fallen said:**
> 
And **>>only<<** if the above dose not work>>>Try adding "X-GNOME-Autostart-Delay=10" in </etc/xdg/autostart/nm-applet>

^^ This worked. Thanks a lot.

---

### Post by speartip on 2019-06-07
I used to have the same thing happen on my XFCE install. Since I changed the icon theme to Tela, the problem has gone. So it could be icon theme specific.

---

### Post by him610 on 2019-06-07
> How did you delete that one network icon ?
Be sure to backup your important data, and you have a Plan B in case something goes awry.
Make sure both of your identical icons link to the same program (networks, etc.)
On Xubuntu desktop (yours may be similar), left click top panel>panel preferences>tab items, highlight the item you no longer want, click the minus(-) widget.

---

### Post by linuxyogi on 2019-06-07
@[**[COLOR=#000000]1fallen[/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855")

I used your solution then I logged out and back in and the 2nd icon was gone but after a reboot the duplicate icon is back.

---

### Post by linuxyogi on 2019-06-07
@[**[COLOR=#000000]him610[/COLOR]**]("https://ubuntuforums.org/member.php?u=248298")

I am not using xfce. I am using lxde.

---

### Post by ajgreeny on 2019-06-07
In xfce4 there are both "Notification plugin" and "Notification area" applets available for the panel; I do not know if this is also the case with lxde (or lxqt in 18.10 and 19.04) but check what applets you have, and whether both are needed, if you already have the two of them.

You may also be able to right click on the applets and choose *Properties* then hide the network item in one of them.

---

