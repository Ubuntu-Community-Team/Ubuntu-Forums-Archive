---
title: "Installing Gnome Vanilla on Ubuntu"
date: 2018-05-02
forum: General Help
---

### Post by lynx6 on 2018-05-02
Hello guys.
I wanted to install **Gnome Vanilla** on **Ubuntu**, but wanted to know the correct command:
*sudo apt install gnome-session*

or this command:
*sudo apt install vanilla-gnome-desktop*


There is a difference between the two facilities.
Thank you!

---

### Post by PaulW2U on 2018-05-02
> **lynx6 said:**
> There is a difference between the two facilities.
Installing vanilla-gnome-desktop will change much more than installing gnome-session.

If you want to change the Plymouth splash screens, remove the Ubuntu branding and install several GNOME utilities that wouldn't otherwise be installed then installing vanilla-gnome-desktop is the way to go. That's what I have done and it gives me something much closer to what the GNOME developers intended their desktop to look like. 

Edit: by installing vanilla-gnome-desktop you get what Ubuntu GNOME would have looked like had it still existed.

---

### Post by lynx6 on 2018-05-02
Thank you, for the explanations.

Have you installed Gnome Vanilla?
And what do you think of performance, is it better?

---

### Post by cruzer001 on 2018-05-02
I have not tried the vanilla-gnome package, but looking at the package list it is not meant to run on top of ubuntu or anyhing else.  Another words, its complete install in itself.

[https://packages.ubuntu.com/bionic/vanilla-gnome-desktop](https://packages.ubuntu.com/bionic/vanilla-gnome-desktop)

Installing gnome-session on top of ubuntu looks doable, I have not tried it.

[https://packages.ubuntu.com/source/bionic/gnome-session](https://packages.ubuntu.com/source/bionic/gnome-session)

---

### Post by PaulW2U on 2018-05-02
> **lynx6 said:**
> Have you installed Gnome Vanilla?
And what do you think of performance, is it better?
Yes, I have two such installations on the same laptop and they work very well but on a cheap laptop that I bought several years ago performance is not good. If you already have Ubuntu 18.04 then installing vanilla-gnome-desktop won't decrease the performance of your installation. You just remove Canonical's preferred customisations.

---

### Post by PaulW2U on 2018-05-02
> **cruzer001 said:**
> I have not tried the vanilla-gnome package, but looking at the package list it is not meant to run on top of ubuntu or anyhing else.  Another words, its complete install in itself
It's a metapackage like ubuntu-desktop.

Installing it will just add those packages that are not part of ubuntu-desktop and change the Plymouth splash screens and desktop themes.

---

### Post by cruzer001 on 2018-05-02
Just yesterday I installed Ubuntu Budgie on a 12 year old laptop that runs Lubuntu just fine and I'm impress.  It's as fast as Lubuntu.  May want to consider it.

---

### Post by lynx6 on 2018-05-02
Thank for the explanations.
I'm going to install *Vanilla Gnome* and check the performance on my computer.

---

### Post by lynx6 on 2018-05-02
> **cruzer001 said:**
> Just yesterday I installed Ubuntu Budgie on a 12 year old laptop that runs Lubuntu just fine and I'm impress.  It's as fast as Lubuntu.  May want to consider it.
*Budgie* is a good desktop choice.

---

### Post by PaulW2U on 2018-05-02
> **lynx6 said:**
> Thank for the explanations.
I'm going to install *Vanilla Gnome* and check the performance on my computer.
You will of course need to reboot to see the the changed Plymouth splash screens and if the Ambiance or Radiance theme is still present just use Tweaks to change the theme to Adwaita which will now be marked as being the default theme.

I've been using Ubuntu 18.04 this way since last November, as an early adopter, and much prefer it.

---

### Post by lynx6 on 2018-05-02
> **PaulW2U said:**
> Installing vanilla-gnome-desktop will change much more than installing gnome-session.

If you want to change the Plymouth splash screens, remove the Ubuntu branding and install several GNOME utilities that wouldn't otherwise be installed then installing vanilla-gnome-desktop is the way to go. That's what I have done and it gives me something much closer to what the GNOME developers intended their desktop to look like. 

Edit: by installing vanilla-gnome-desktop you get what Ubuntu GNOME would have looked like had it still existed.
One question I have, what is *Plymouth*?

---

### Post by PaulW2U on 2018-05-02
> **lynx6 said:**
> One question I have, what is *Plymouth*?
That's what you see when Ubuntu boots up and closes down. It can be customised for each of Ubuntu's flavours - name, colour etc.

---

### Post by lynx6 on 2018-05-02
> **PaulW2U said:**
> That's what you see when Ubuntu boots up and closes down. It can be customised for each of Ubuntu's flavours - name, colour etc.
Okay, now I understand.
I put the topic as resolved, thanks again.

---

