---
title: "virtualbox and guest installations"
date: 2007-09-15
forum: General Help
---

### Post by hellfried on 2007-09-15
i am trying to run pclinuxos from within ubuntu feisty using virtual box. how can i get the guest os to use the whole of my screen. right now it only occupies a small area of screen even if i select the full screen option. i know it has something to do with guest installation but when i click on devices > guest installations, nothing happens. can someone help?

---

### Post by Oki on 2007-09-15
If you hit Ctrl + F it should give you full screen. If you still only get a small screen within virtualbox program then you need to install "voboxGuestAdditions.iso" that comes with virtualbox. I have never done that myself, but it is explained in the downloadable pdf manual from here; [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) 

There is also guides out there, as this one; [http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)

Hope it works out for you:)

---

### Post by shad0w_walker on 2007-09-15
If your are still using only part of the screen when in fullscreen mode then your guest OS is using only the  area of screen needed to show its resolution. If you install the guest additions mentioned above (I haven't done this in months so won't try to help right now) and increase your guest OS' resolution to the same as your host OS' resolution then you should use the whole screen.

---

