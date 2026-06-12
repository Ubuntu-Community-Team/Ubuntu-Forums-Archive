---
title: "Files View - Gnome Shell Extension NG with 21.04?"
date: 2021-08-11
forum: General Help
---

### Post by 2CV67 on 2021-08-11
I have been using Gnome Shell Extension "Files View" OK in Ubuntu 20.04 & 20.10 for over a year.

Following a recent upgrade to 21.04, Files View was still present & worked OK except the first time it was opened each session, when it showed no icons & failed to select anything.
After closing & opening Files View again, it worked OK for the rest of the session.

I tried switching it off & on again in the Gnome Extensions page - Installed Extensions, but with no effect.

I then deleted it on the Installed Extensions page & tried to install it again from the Extensions page, but with no success.
It never appears in my Installed Extensions page.
I tried that several times but no luck.
There is no error message.

Is Files View compatible with 21.04?

Any suggestions for getting it to work?

Thanks!

---

### Post by Dennis N on 2021-08-12
I tried to install this in Ubuntu 21.04 (from the shell extensions website) by going to the extension page and switching ON. But after that, it is not shown in the "Exensions" app or Tweaks or as an "Installed Extension" on the web page. There are files for it in ~/.local/share/gnome-shell/extensions. I would guess there must be something wrong with the packaging not to be recognized. The info within its folder indicates it's for shell 3.38, but it's no go here.

---

### Post by monkeybrain20122 on 2021-08-12
> **2CV67 said:**
> 

Is Files View compatible with 21.04?

Any suggestions for getting it to work?

Thanks!

I don't know if it is compatible with 21.04 but definitely not with gnome-shell 40 (at least at the moment, I think Ubuntu21.10 will be shipped with gnome-shell 40?) When you install these gs extensions keep in mind that they are third party hacks and every gnome update breaks a bunch of them (the much loved dash to dock still doesn't work with gnome 40), the internet is littered with broken and unmaintained extensions. So if you want a consistent experience you should stick with the 20.04 LTS instead of upgrading to a beta with only 9 months of support just because it is available.

---

### Post by monkeybrain20122 on 2021-08-12
So I just tested in a 21.04 vm. Indeed it doesn't work. Just as Dennis N said, installed it from the website but it is not shown in the extensions app. Check the website again it is "off". Tried a few times, it just turned off automatically. Doesn't work in both wayland and xorg sessions.

---

