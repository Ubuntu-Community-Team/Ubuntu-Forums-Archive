---
title: "desktop disappeared"
date: 2007-11-30
forum: General Help
---

### Post by cheaptrick on 2007-11-30
hi
i am using xubuntu 7.10, , recently i tried installing compiz fusion using the instructions from here [http://ubuntuforums.org/showthread.php?t=623752](http://ubuntuforums.org/showthread.php?t=623752) . It worked fine,
Then when i uninstall it, my desktop just disappeared, no more icons.
i went to desktop settings, checked 'allow xfce to manage desktop', but it didnt work.
i tried reinstalling compiz fusion, reinstalling xubuntu, but nothing changed.

appreciate some help here.. thanks

---

### Post by perixx on 2007-12-02
Hi cheaptrick,

does Xubuntu still boot into the X-server with your desktop-wallpaper, but no panels and symlinks are shown?

If so, try in the following order, this might help: 
1) re-opening X-server, if only closed (CTRL+ALT+F7)
2) type 'gksudo xfce4-panel' - if panel-bars + desktop re-appear,
    set 'save session at shutdown' in your Session-Manager and 
    reboot.
3) do 'sudo /etc/init.d/gdm restart'
3) if nothing helped so far, do 
    'sudo apt-get install xubuntu-desktop'
4) do 'dpkg-reconfigure -phigh xserver-xorg', but proceed 
    carefully!

I hope this solves your problem!


perixx

---

