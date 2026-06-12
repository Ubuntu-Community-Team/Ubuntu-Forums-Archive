---
title: "Replace Plymouth"
date: 2016-10-13
forum: General Help
---

### Post by mickee384 on 2016-10-13
When I upgraded to 16.04, my Plymouth splash screen broke. It appears to be missing a file? I was hoping someone knows where I can get all the files required for Plymouth. Might be easier just to replace the files/folders? The exit splash works, but the starting splash is just generic plymouth ubuntu coloured wallpaper and a tiny ubuntu 16.04 in the centre.

---

### Post by mickee384 on 2016-12-02
bump

---

### Post by deadflowr on 2016-12-02
plymouth changed the location where the files it uses are stored.
previous versions (14.04 and down) set the installed plymouth files in the /lib/plymouth directory.
16.04 moved those to /usr/share/plymouth.

Not sure about where to get the files per se, but you can try reinstalling them
plymouth themes usually install two packages, outside of dependency packages:
plymouth-theme-*buntu-logo
plymouth-theme-*buntu-text
typically you only need to install one, the logo package runs on system that are capable of running graphically, and the text are systems that are not.
But installing both does not hurt.

(change *buntu to flavor name you want; for ubuntu change it from *buntu to ubuntu, or for ubuntu-mate change it from *buntu to ubuntu-mate,
if that makes sense.)

You might want to set it, to do so run
```
sudo update-alternatives --config default.plymouth
```
which will list the plymouth themes installed and allow you to set which ever theme you want as the theme.
If that makes sense.
 
For fun reading here:
[https://wiki.ubuntu.com/Plymouth]("https://wiki.ubuntu.com/Plymouth")

Hope it helps.
good luck

---

### Post by mickee384 on 2016-12-15
Thanks. I will try this

---

### Post by mickee384 on 2017-01-03
That didn't work, however, I used OMG! Ubuntu's article, Does Ubuntu Need More Tux?

Install Tux4Ubuntu and ran the Plymouth part.

[http://www.omgubuntu.co.uk/2016/12/tux-ubuntu-grub-plymouth-themes]("http://www.omgubuntu.co.uk/2016/12/tux-ubuntu-grub-plymouth-themes")

Fixed it.

---

