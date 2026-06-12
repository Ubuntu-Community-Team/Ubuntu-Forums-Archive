---
title: "splash screen"
date: 2007-12-30
forum: General Help
---

### Post by wolf71 on 2007-12-30
sorry if this is double post but can't find the other one anywhere.lol   how can i change the distro name that shows up on startup? would like to change it to something else or just change it in the casper folder or something. any ideas would help alot.

---

### Post by Vixis on 2007-12-30
press alt+F2
type:
```
gksu gedit /boot/grub/menu.lst
```

at the files end there will be something like:
> 
title           Ubuntu Feisty, kernel 2.6.20-16-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=432118ad-10bc-42aa-83fe-fce6093caf51 ro vga=771
initrd          /boot/initrd.img-2.6.20-16-386
savedefault

change title

How to change the gnome splashimage.
> 1. Put the splash image you want in "png" format and store it in /usr/share/pixmaps/splash. (You can use Nautilus or the "cp" or the "mv" command from the terminal window if you want. Just remember to use "sudo" before your command. )
2. Press ALT-F2 then at the prompt type "gconf-editor" (without the quotes).
3. Click on "apps" then "gnome-session" then "options".
4. To the right of the Name "splash_image" double click on the Value "splash/ubuntu-splash.png".
5. Change "splash/ubuntu-splash.png" to reflect your new splash image: "splash/newsplash.png".
6. Click on "File" then "Quit".
7. Logout then login in again to see your new splashimage.

or you can install gnome-splashscreen-manager:
```
sudo apt-get install gnome-splashscreen-manager
```

---

### Post by wolf71 on 2007-12-30
thanks alot for the help  gonna try it in a few minutes

---

