---
title: "Bootsplash and wallpaper gone after fglrx uninstall"
date: 2012-12-09
forum: General Help
---

### Post by zenolijo on 2012-12-09
Hello!
As the title says, i installed and uninstalled fglrx a couple of days ago.
I have a AMD M780G with ATI Radeon HD 3200 chipset, but after the fglrx install, it went to 1024x768 resolution and when clicking the AMD Catalyst centre in settings manager it came warning message telling me drivers was either incompatible or invalid.
So i uninstalled it and by some reason the bootsplash is gone (just black screen) and desktop background gone too.
I updated to 12.10 a couple of weeks ago and don't know if it's still there, but it used to be a desktop section in the settings manager in 12.04 where i could change my background but it's gone...

I am pretty familiar with the console, if that will be necessary!

Thanks :)

---

### Post by zenolijo on 2012-12-10
Bump, still having this problem

---

### Post by Rebelli0us on 2012-12-10
Bootsplash and desktop wallpaper are different issues. Desktop wallpapers are just JPEG images.

If you install grub-customizer it will let you select boot resolution. Linux startup screen can be buggy so you're not alone.

---

### Post by Geezanansa on 2012-12-10
zenolijo try googling /searching for how to edit grub.cfg
 
I am sure, going by what you have asked, that all you have to do is open gedit with root priveleges by ```
gksu gedit /etc/default/grub.cfg
``` But as you can not see the desktop you have yet to log in. Allthough your computer looks like it is not doing anything and you can not see anything on screen. You could try waiting for the hdd led to stop flashing at boot time(may take 1-2mins)
1.Carefully type your Password to log in. Press enter OR if this does not work- 2.Try pressing alt+F1 to get to tty. Log in. Try alt+F7 to view desktop and open terminal to run gedit command.
 
Once in desktop session you can edit your etc/default/grub.cfg and remove # from the line that starts 800x600.Save and close gedit and reboot. Enjoy booting with being able to see grub/Plymouth and log in screen. To reinstall nouveau (Ubuntu default drivers) ```
sudo apt-get install --reinstall ubuntu-desktop
```  After which do a ```
sudo dpkg-reconfigure xserver-xorg
``` and then clean up by ```
sudo apt-get autoremove
``` and reboot

---

