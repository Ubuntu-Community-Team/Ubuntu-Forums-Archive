---
title: "Change color scheme on selected ap when doing alt/tab"
date: 2023-09-03
forum: General Help
---

### Post by Tom_Carr on 2023-09-03
When I press alt/tab it brings up a list of all the open apps.  Then by holding down the app key and pressing the tab key up and down I can move through all the open apps.  The problem is that on my computer the backgroud to the whole list is black and the background to the app selected is dark grey and it is hard to see which app is selected.  How can I get a different color scheme?

---

### Post by Dennis N on 2023-09-03
> **Tom_Carr said:**
> When I press alt/tab it brings up a list of all the open apps.  Then by holding down the app key and pressing the tab key up and down I can move through all the open apps.  The problem is that on my computer the backgroud to the whole list is black and the background to the app selected is dark grey and it is hard to see which app is selected.  How can I get a different color scheme?

The colors here are controlled by the gnome-shell theme. You would need to find a different theme. Attached is an image of Black Maia gnome shell theme. It has a light gray selector. You need to find a version made for your gnome shell version. The Black Maia version in the image is for gnome shell 3.38.

---

### Post by Tom_Carr on 2023-09-03
I am a light user, just using the GUI.  How do I change themes?

---

### Post by Dennis N on 2023-09-04
You will need a tutorial to cover the steps. Here is one that looks reasonably good and covers all the types of themes. I suggest you read it over. There is a section "Manually install a GNOME Shell theme" near the bottom.

[https://www.pragmaticlinux.com/2021/09/manually-install-a-gnome-theme/](https://www.pragmaticlinux.com/2021/09/manually-install-a-gnome-theme/)

You need to know your gnome-shell version in order to download the matching version from gnome-looks.org. You can use the terminal to find it. Example:
```
dmn@Tyana-vm:~$ gnome-shell --version
GNOME Shell 42.9

```
Use the whole number part only. So for this computer, I want version 42 of any theme I might want to try. You can install more than one theme and select among them with Gnome Tweaks as the tutorial shows. 

Note. I checked, but didn't see Black Maia on the gnome-look.org site, so it may no longer be maintained and available. You might have to test some others out to find one you want.

---

### Post by Tom_Carr on 2023-09-04
Thanks for your help Dennis.

---

