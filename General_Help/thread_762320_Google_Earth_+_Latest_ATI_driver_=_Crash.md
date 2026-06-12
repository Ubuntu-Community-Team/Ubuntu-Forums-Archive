---
title: "Google Earth + Latest ATI driver = Crash"
date: 2008-04-22
forum: General Help
---

### Post by yaknowwat on 2008-04-22
I noticed that the ATI driver wasn't set as a restricted driver anymore in this release.

But the issue i have is that the newer driver will cause X to restart if Google Earth is loaded.

What ATI driver version was in 7.10 i am currently using 8.04 so i can't just unistall the driver.

~Solved~
Needed to reconfigure Xorg Server so that Restricted Drivers would work.

to reconfigure Xorg Server use this command
```
$ sudo dpkg-reconfigure xserver-xorg
```

And I am sure : [http://ubuntuforums.org/showthread.php?t=758576](http://ubuntuforums.org/showthread.php?t=758576)
(linked to it by Tim sharitt)
helped a lot too.

After that i played a 3d game and I was asked if i wanted to enable restricted drivers (it wouldn't do this the other 5 times i tried the game).

---

### Post by em3raldxiii on 2008-04-22
Hey hey.  I don't think I can answer your question directly, but I can suggest you check out a very nice script by one of our Ubuntu regulars (Alberto Milone).  His script is called "Envy".

It basically allows you to uninstall exiting botched drivers and then re-install the correct ones.  It's an absolutely brilliant script.

Here's a link to his projects page:  [http://albertomilone.com/projects.html](http://albertomilone.com/projects.html)

---

### Post by yaknowwat on 2008-04-22
Yeah i know about installing drivers its just my issue is what drivers came with ubuntu linux 7.10 so that i can downgrade to those drivers to have support for Google Earth.

The newer drivers are indeed slightly better but losing support for something thats used every other day isn't worth it.

---

### Post by yaknowwat on 2008-04-22
sorry to bump this but i would be nice to know.

---

### Post by Tim Sharitt on 2008-04-22
I had the same problem when I upgraded to Hardy. I am now using xorg-driver-fglrx 8.4. and have had no problems at all, it actually seems to work better than the standard driver. See here [http://ubuntuforums.org/showthread.php?t=758576]("http://ubuntuforums.org/showthread.php?t=758576") for details.

---

### Post by yaknowwat on 2008-04-23
I just finished trying this several different ways and it hasn't worked 

My system specs are the ones in the signature.

---

### Post by imoatama on 2008-04-23
Off the top of my head I dont know what version came with gutsy  - the version in the hard repository appears to be 8.3 (ie from last month). What you could try doing is editing your sources.list to disable the hardy repository and enable the gutsy repo, and install whatever fglrx driver you find in the gutsy repo.

---

### Post by yaknowwat on 2008-04-23
I found out the problem i needed to reconfigure the xorg server for it to allow me to enable the restricted driver.

This is possibly an upgrade bug from Gutsy to Hardy with a Custom Xorg config which will make it impossible to enable restricted drivers without reconfiguring Xorg Server.

So i guess this is Solved and the system works beautifully now.

---

