---
title: "synaptic package manager"
date: 2017-10-22
forum: General Help
---

### Post by Johnny3 on 2017-10-22
synaptic package manager I install it from Ubuntu Software. IT shows up. But where I type in my pass word to open it. It just disappears. Any ideas. I am using 17.10 just installed Oct 21,2017
Thanks Johnny

---

### Post by wildmanne39 on 2017-10-22
The answer is here.

[https://ubuntuforums.org/showthread.php?t=2375077](https://ubuntuforums.org/showthread.php?t=2375077)

---

### Post by Frogs Hair on 2017-10-22
The following command will grant temporary permissions in the Wayland session. Synaptic should open normally in the Ubuntu on Xorg session.
 ```
  xhost +si:localuser:root
```

---

### Post by Johnny3 on 2017-10-22
I did this [https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10](https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10) Am I losing anything by using Xorg instead of Wayland? 
Thanks Johnny

---

### Post by wildmanne39 on 2017-10-22
No, it is okay to use x.org.

---

### Post by bobblex on 2017-10-24
> **Frogs Hair said:**
> The following command will grant temporary permissions in the Wayland session. Synaptic should open normally in the Ubuntu on Xorg session.
 ```
  xhost +si:localuser:root
```

This doesn't seem to work with Lubuntu 17.10.  I also am unable to find a way to start an Xorg session rather than whatever the Lubuntu 17.10 default is.

Any suggestions?

Thanks

---

### Post by wildmanne39 on 2017-10-24
I do not use lubuntu but you should be able to log out and then there should be a button to click to choose xserver session.

---

### Post by bobblex on 2017-10-24
> **wildmanne39 said:**
> I do not use lubuntu but you should be able to log out and then there should be a button to click to choose xserver session.

Nope. No selection, button, or menu to change sessions.


10/25/17
I now have Synaptic Package Manager running in Lubuntu 17.10. It's been an interesting trek. I did learn how to use the gpk-update-viewer and the gpk-application (Software on the menu), which are really both kind of clunky and slow (on my old Dell 2350) compared to Synaptic.  I also reviewed how to use aptitude and need to keep a hard-copy of the commands around for using it as I usually don't need it very often and tend to only remember about four of the most commonly used commands. There is a lot of information available from aptitude (apt) if one learns how to use it.

The solution for me was installing (actually re-installing) LXDE, after which Synaptic started working again. When I ran the apt command to install LXDE it showed a lot of things being installed that apparently were missing from my installation after I did the upgrade from Lubuntu 17.04 to 17.10.

---

### Post by wghammock on 2018-03-07
[HTML]xhost +si:localuser:root[/HTML]

Worked for me, Thanks!

---

