---
title: "USplash problems, color test screen?!"
date: 2006-11-14
forum: General Help
---

### Post by n0sferatu on 2006-11-14
I am trying to configure usplash to use a different image.  I've followed this guide: [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

However I always end up with this weird color-test screen!  I've searched the forums and google but I haven't found anyone else with this problem.  I'm not quite sure what to do.  I've tried reinstalling usplash, usplash-dev, and usplash-artwork.  This happens no matter what vga=xxx code I use in grub's menu.lst.  It simply changes the size of the color-test screen on shutdown and bootup.

Thanks in advance.

This is what I see when I bootup or shutdown.  The progress bar in the middle is working... :-k 

[IMG]http://i101.photobucket.com/albums/m77/n0sferatu_06/usplash-color.jpg[/IMG]

---

### Post by testube_babies on 2006-11-14
I had this problem too when I tried to change the usplash image.  Unfortunately, the only way I found to get rid of it was to reinstall Ubuntu.  Sorry I can't help.

---

### Post by n0sferatu on 2006-11-15
> **testube_babies said:**
> I had this problem too when I tried to change the usplash image.  Unfortunately, the only way I found to get rid of it was to reinstall Ubuntu.  Sorry I can't help.

There has to be a way to do it without reinstalling the whole OS. :confused: Thanks for the reply though, at least I know I'm not the only one who has had this problem.

---

### Post by Jeremiah478 on 2006-11-19
I don't know if this will help, although I hope it does:

[http://ubuntuforums.org/archive/index.php/t-30341.html](http://ubuntuforums.org/archive/index.php/t-30341.html)

The post the really note though is by dradul, and if goes:

"Nice how-to, but a bit more complicated than necessary :-)
Debian-based distros have a little utiity script called "update-grub" that will automagically detect and include any file called "splash.xpm.gz". The tip could go like this:

bash-$ sudo cp usplash.xpm.gz /boot/grub
bash-$ cd /boot/grub
bash-$ sudo ln -s usplash.xpm.gz splash.xpm.gz
bash-$ sudo update-grub

Why use a symbolic link? I have several splashscreens and change them whenever I feel like it. BTW, here is a small project for someone with determination: writing a small script that rotates through an splashscreen collection. Hint: use dash, and the @reboot feature of Vixie's cron, see crontab(5) for details ... :-)

On the other hand, if you don't have "update-grub" in your system, you need to do it by hand."

This has helped me out a few times and I always forget where to find it.

---

### Post by autocrosser on 2006-11-19
That's very interesting---The image is the EARLY Edgy test screen from Knot 1---If you do a bit of looking, look for Usplash-Switcher--it will allow you to change your splash very easily--The thread got buried in Edgy testing (the closed forum)--You also might try reinstalling the whole Usplash bit--If you want to know more about Usplash-Switcher---just ask;)

---

### Post by n0sferatu on 2006-11-19
I've tried using usplash-switcher, when I run it all the usplash images show up as invalid.  I'm using Ubuntu 6.10 Edgy 64-Bit by the way.  I've managed to get the usplash screen back to the default broken black and white ubuntu logo.  After I upgraded to edgy my nice orange usplash turned to an ugly broken black and white usplash logo.

---

### Post by autocrosser on 2006-11-19
Yes--I've heard that it's a problem on 64--I've got a dual that is 64-able & I am running it as 32--I don't see a performance hit & I stress the system by running Seti@Home---Unless you really need 64 for some reason, the recommendation is to run 32 until more 64 stuff is out there---(read Fiesty Fawn ;) )

---

### Post by ToonArmy on 2006-11-20
```
sudo apt-get install ubuntu-minimal
``` fixed it for me, this might reinstall some stuff you removed before.

---

### Post by gwi on 2006-11-27
> **autocrosser said:**
> That's very interesting---The image is the EARLY Edgy test screen from Knot 1

Interesting indeed. I upgraded from Dapper to Edgy two days ago, and I also get the test screen as usplash image. My LCD monitor has a 1280x1024 resolution. The test screen is something like 640x400, and is placed in the upper left corner of the screen instead of being centered.

Why do I get the test screen? The upgrade process did not report any errors.

---

