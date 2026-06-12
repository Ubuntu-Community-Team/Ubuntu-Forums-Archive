---
title: "Blank screen during edgy bootup"
date: 2006-11-01
forum: General Help
---

### Post by Parksy on 2006-11-01
After upgrading to Edgy, I've lost my bootsplash screen.  When grub goes away, all I get is a black screen with a blinking hypen in the top left corner.  It stays like that until X loads.

The boot also seems to be really slow...lots of time when there's no hard drive noise.  Is there a fix for this?

---

### Post by autocrosser on 2006-11-02
Take a look at all the usplash threads--I think you have a problem with not having the right settings either in your /etc/usplach.conf file or you need to add the vga=<some number> into your /boot/grub/menu.lst line---take a look thru the last two hundred or so posts & you'll find several threads with the same general topic. You can also edit your kernel line & remove the "quiet" from quiet splash to get more information on what the system is doing.

---

### Post by tebibyte on 2006-11-03
I have the same problem. Can you please be a little more specific?:)

---

### Post by Parksy on 2006-11-10
I've had some success editing /etc/usplash.conf.  I changed it from 1280x1024 (my standard display resolution) to 800x600 and now usplash works.  I haven't tried playing with the vga= stuff yet.

---

