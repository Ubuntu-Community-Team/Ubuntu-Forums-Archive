---
title: "HELP!!! Upgrading To 18.10"
date: 2018-10-18
forum: General Help
---

### Post by sasafrass452 on 2018-10-18
I'm attempting to upgrade to 18.10. I currently have a large box on my screen asking "Do you want to start the upgrade?", however, the box is so large that the bottom is hidden below the bottom of my screen, so there is no visible button to click on & initiate the upgrade. What do I do?

---

### Post by coffeecat on 2018-10-18
Keep the alt key pressed, then left click and hold on anywhere within the window, and you will be able to move the whole window up as far as you need.

That is **if** the gnome desktop in 18.04 behaves in the sane/same way other desktops do. I have no experience of the recent versions of gnome so I don't know whether this works in gnome.

Of course, that is assuming you are using the standard version of Ubuntu with gnome - you don't specify which flavour/desktop you are using.

---

### Post by sasafrass452 on 2018-10-18
This didn't work. And yes, I'm using the standard Ubuntu 18.04 with gnome. Now what?

> **coffeecat said:**
> Keep the alt key pressed, then left click and hold on anywhere within the window, and you will be able to move the whole window up as far as you need.

That is **if** the gnome desktop in 18.04 behaves in the sane/same way other desktops do. I have no experience of the recent versions of gnome so I don't know whether this works in gnome.

Of course, that is assuming you are using the standard version of Ubuntu with gnome - you don't specify which flavour/desktop you are using.

---

### Post by sasafrass452 on 2018-10-18
That's fine. 19.04 is just 6 months away.... *wink*

If anyone can help, I'd really appreciate it! I'd hate to mess something up by cancelling & starting over. Please don't leave me hanging here.... LOL.... I need help ASAP!!!

> **monkeybrain20122 said:**
> Why do you want to do that? 18.10 is a interim release with only 9 months of support and it is just released, which means it is likely to be buggy. (at this point even 18.04 is not very stable IMO)

---

### Post by coffeecat on 2018-10-18
> **sasafrass452 said:**
> This didn't work. And yes, I'm using the standard Ubuntu 18.04 with gnome. Now what?

Sorry to hear that. Hopefully, someone with gnome experience will be along shortly.

---

### Post by sasafrass452 on 2018-10-18
Well, it looks like I'll just have to start over. I can't leave this on all night waiting for an answer that may never come.... Thanks anyway!

---

### Post by sp40140 on 2018-10-18
If you want to upgrade to 18.10. You can use terminal to do that. Don't have to use GUI.
```
 
sudo apt update && sudo apt dist-upgrade
```

---

### Post by oldos2er on 2018-10-18
> **sp40140 said:**
> If you want to upgrade to 18.10. You can use terminal to do that. Don't have to use GUI.
```
 
sudo apt update && sudo apt dist-upgrade
```

That's a start, but then you need  ```
do-release-upgrade
```

---

### Post by nlee2 on 2018-10-18
The default is Install Now so give the window focus and blindly press enter.

---

### Post by nameinuse on 2018-10-19
I've come late to this but same happened to me - I cancelled the upgrade and re-started. When the first box appeared, I moved it up and left to the top of the screen and when the big box opened, the buttons were visible.

---

### Post by deadflowr on 2018-10-19
> **sasafrass452 said:**
> I'm attempting to upgrade to 18.10. I currently have a large box on my screen asking "Do you want to start the upgrade?", however, the box is so large that the bottom is hidden below the bottom of my screen, so there is no visible button to click on & initiate the upgrade. What do I do?

Have you tried ctrl + alt + down ?
To see if it's overlapping workspaces.
**Edit:** nevermnd workspaces totally independent on gnome, so one does not bleed into the others like unity and compiz do.

Also what's the screen resolution you have set.
I ask because this goes back some time:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/40792]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/40792")

---

### Post by tea for one on 2018-10-19
> **sasafrass452 said:**
> I'm attempting to upgrade to 18.10. I currently have a large box on my screen asking "Do you want to start the upgrade?", however, the box is so large that the bottom is hidden below the bottom of my screen, so there is no visible button to click on & initiate the upgrade. What do I do?

Using Gnome Shell 3.28.3, to move a window or dialogue box so that you can access all the visible buttons:-

Hold down super key (or key with Windows logo) and simultaneously left click and move the mouse.

---

### Post by oldrocker99 on 2018-10-20
This looks like the best way to upgrade from a terminal, which will solve upgrade problems.

[https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver)

---

