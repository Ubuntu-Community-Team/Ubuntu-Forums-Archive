---
title: "Plymouth Splash Manager"
date: 2016-08-30
forum: General Help
---

### Post by Quarkrad on 2016-08-30
I have looked and keep seeing links for a Plymouth Manager for 16.04.  However, when on the page it appears the managers are for versions prior to 16.04.  Is there such a thing (Plymouth Manager) for 16.04?  Thanks.

---

### Post by Dennis N on 2016-08-30
It appears the project became inactive several years ago. It probably would not install or not work in 16.04 if you tried it. A few years ago, I seem to recall seeing cautions given not to use it. That said, it is not too difficult to change the boot splash theme. Some Plymouth themes are available for installation in the current Ubuntu repos.

---

### Post by Quarkrad on 2016-08-30
Thanks for the response.  Do you know if is best to change these themes manually or if there something with a gui?

---

### Post by Dennis N on 2016-08-30
> **Quarkrad said:**
> Thanks for the response.  Do you know if is best to change these themes manually or if there something with a gui?

I am not aware of any other gui tool to do this. Once a theme is installed, just use the terminal and run:
```
dmn@Sydney ~ $ sudo /etc/alternatives/update-alternatives --config default.plymouth
```
and select your choice by number.

You can also use a variant of this command to install a Plymouth theme if it's not from the Ubuntu repos. When I used an alternate theme in the past, I found better themes (that's just my opinion of course) on [www.gnome-look.org](www.gnome-look.org). Look for 'Plymouth Themes' in the index on the left of their web page. Many of the theme pages there have instructions and commands how to do it.

EDIT:
Forgot this part:

After installing and selecting,  you need to run:
```
sudo update-initramfs -u
```

Then restart and it should change.

---

