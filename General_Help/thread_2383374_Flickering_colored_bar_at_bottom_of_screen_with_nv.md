---
title: "Flickering colored bar at bottom of screen with nvidia-340 driver"
date: 2018-01-24
forum: General Help
---

### Post by quenz on 2018-01-24
OS: Ubuntu Gnome 16.04 LTS
Computer: MacBook Pro (13-inch, Mid 2009)
GPU: Geforce 9400M

The open-source driver works fine, with no apparent graphical issues, but it's slow. I've installed the nvidia-340 driver, which is faster, but I have some graphical issues.

When clicking the "Activities" button in the top-left corner, bringing up the Activities Overview, there's a green bar (almost as thick as the top bar), that appears and disappears, and is especially flickery when moving the mouse over different GUI elements.

From the login/unlock screen, where you type your password, moving the mouse around makes a purple bar flicker.

I've tried to take a screenshot, but every time I do, it disappears. Here's a photo of the first one: [https://i.imgur.com/LO4YlIj.jpg](https://i.imgur.com/LO4YlIj.jpg)

Also, tatertots from #ubuntu on freenode told me to include these logs relevant to my system: [http://termbin.com/tk4e](http://termbin.com/tk4e) [http://termbin.com/g584](http://termbin.com/g584) [http://termbin.com/yjab](http://termbin.com/yjab) [http://termbin.com/oxt2](http://termbin.com/oxt2)

---

### Post by daoud-makram on 2018-01-24
I have the same exact problem, I tried changing the driver to nvidia-304 driver and I had trouble clicking on things...

My best results were with this driver 340.104-0ubuntu0.16.04.1  ,but still sometimes I would get a lot of flickering when using the laptop heavily...

---

### Post by daoud-makram on 2018-01-25
Try changing the shell theme to the default or none. Somehow that helps after you login, and during gnome-session... flickering stops completely. I wander if it is a gtk process that is a problem problem, the reason I think that is that the flickering is not consistent. :P

---

### Post by daoud-makram on 2018-01-25
Please keep in mind I am using the Dash to Panel Extension...

---

