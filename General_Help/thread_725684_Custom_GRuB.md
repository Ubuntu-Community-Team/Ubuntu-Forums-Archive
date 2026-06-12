---
title: "Custom GRuB"
date: 2008-03-15
forum: General Help
---

### Post by madara_sama on 2008-03-15
By default, GRuB shown black screen with white text. I want to change my GRuB to graphical mode. Like ubuntu LiveCD menu when we boot it, which ubuntu logo on top and menu on bottom.(Most likely PCLinuxOS's GRuB). Any solution?

---

### Post by LeoSolaris on 2008-03-16
you can edit the menu.lst

its in /boot/grub/menu.lst

I have no idea how to make it as graphical as what your talking about though. You could duel boot with PCLinuxOS and just alter the that grub file with a png of ubuntu's logo

Leo

---

### Post by Diabolis on 2008-03-16
I added a background to my grub menu and my menu.lst has this:
```
#SPLASHIMAGE
splashimage=/home/gaston/misDocumentos/bin/grubSplashImage/grub_face.xpm.gz

```

your menu.lst file can be edited with this command:
```
sudo gedit /boot/grub/menu.lst
```

NOTE You can't use any image, it must be an image with at most 16 different colors. Thats enough for me, but if you want more, you might want to try super grub or lilo.

---

### Post by sandysandy on 2008-03-16
> **Diabolis said:**
>  You can't use any image, it must be an image with at most 16 different colors. Thats enough for me, but if you want more, you might want to try super grub or lilo.

is there any particular format / type of the splash image.

do u know any website which has those type which can be used as background to grub menu.

regards

---

### Post by zxscooby on 2008-03-16
look here

[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

---

### Post by Diabolis on 2008-03-16
You can convert any image to a 16 colors image with gimp, but it won't look really good if the base image has tons of colors. You can google more about this issue.

Some examples here: [http://schragehome.de/splash/](http://schragehome.de/splash/)

---

### Post by madara_sama on 2008-03-16
> look here

[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)
Thanks for this info.

---

### Post by madara_sama on 2008-03-16
> splashimage=/home/gaston/misDocumentos/bin/grubSplashImage/grub_face.xpm.gz
What type of this image file?

> I have no idea how to make it as graphical as what your talking about though. You could duel boot with PCLinuxOS and just alter the that grub file with a png of ubuntu's logo
So, I can't get graphical GRuB in ubuntu..?

I have edited my menu.lst, but how to move text menu like in ubuntu LiveCD? any idea?

---

### Post by mcsimon on 2008-03-16
[Here]("http://ubuntuforums.org/showthread.php?t=208855") is a nice tutorial on setting up gfxboot

---

### Post by LeoSolaris on 2008-03-17
> **madara_sama said:**
> What type of this image file?


So, I can't get graphical GRuB in ubuntu..?

I have edited my menu.lst, but how to move text menu like in ubuntu LiveCD? any idea?


Not exactly what I meant, I just meant that I did not know how to do it. After reading some of the other posts though, it looks like it is possible.

Try booting up the LiveCD and looking at it's menu.lst file. I bet it's different. You will have to edit it to take out the parts that you can't use, like the check CD for flaws, that sort of thing. Ya know... that's not a bad idea actually. I may try it myself. If I get it to work, I will post back here with how, then make a HowTo as a thread on it's own. (or just post a link to that HowTo thread)

---

### Post by forrestcupp on 2008-03-17
You can install grub2 which has graphical support.
```
sudo apt-get install grub-pc
```

You will probably have to set it up, and I've never done that before.

I wonder if Hardy will use grub2 by default.


there is also a package for splash images in the repos
```
sudo apt-get install grub-splashimages
```
I don't know how to use them, though.

---

### Post by madara_sama on 2008-03-20
> Try booting up the LiveCD and looking at it's menu.lst file. I bet it's different. You will have to edit it to take out the parts that you can't use, like the check CD for flaws, that sort of thing. Ya know... that's not a bad idea actually. I may try it myself. If I get it to work, I will post back here with how, then make a HowTo as a thread on it's own. (or just post a link to that HowTo thread)

Yes, I have tried the livecd before I post this thead. But, this really made me confuse. Okay, I'll wait for your HowTo thread, if there is...

---

### Post by madara_sama on 2008-03-20
> **forrestcupp said:**
> You can install grub2 which has graphical support.
```
sudo apt-get install grub-pc
```

You will probably have to set it up, and I've never done that before.

I wonder if Hardy will use grub2 by default.


there is also a package for splash images in the repos
```
sudo apt-get install grub-splashimages
```
I don't know how to use them, though.

Thanks, I'll check it. I don't know if grub2 is included into repos.

---

### Post by madara_sama on 2008-03-20
> **mcsimon said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=208855") is a nice tutorial on setting up gfxboot

Nice thread, I have to try it. Thanks.

---

