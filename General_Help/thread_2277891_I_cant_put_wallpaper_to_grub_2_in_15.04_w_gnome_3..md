---
title: "I cant put wallpaper to grub 2 in 15.04 w gnome 3."
date: 2015-05-12
forum: General Help
---

### Post by i12 on 2015-05-12
I cant put wallpaper to grub 2 in 15.04 w gnome 3.
Send me working /etc/grub.d/05_debian_theme file please. If possible emphasize reference to picture with comment  in file.

---

### Post by dino99 on 2015-05-12
might help you  [http://www.members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#make_your_own_](http://www.members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#make_your_own_)

---

### Post by Bucky Ball on 2015-05-12
*Thread moved to **General Help**.*

You could also look at [Grub Customizer.]("http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/")

---

### Post by grahammechanical on 2015-05-12
Mt method is to put the image file into /boot/grub/ and run

```
sudo update-grub
```

I installed from the software centre grub2 splashimages. They end up in /usr/share/images/grub/. With administrator privileges I copy and paste one of the images into /boot/grub/ and then update grub. And that does it. The images are all tga format. I do not know if that makes a difference or not.

Regards

---

### Post by i12 on 2015-05-15
> Mt method is to put the image file into /boot/grub/ and run
Doesn't work

---

### Post by leunam12 on 2015-05-15
> **i12 said:**
> Doesn't work
I just did this and it worked. Maybe your image doesn't meet the requirements; check the link below for image specifications.

[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by i12 on 2015-06-07
Image was from 
grub2-splashimages

---

