---
title: "XGL/Compiz...it did it on its own :S"
date: 2006-08-26
forum: General Help
---

### Post by viciouslime on 2006-08-26
I decided to follow one of the guides for xgl/compiz. From a fresh install i enabled the nvidia driver and the multiverse/universe and then ran:

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

And created sudo gedit /etc/gdm/gdm.conf-custom as instructed.

Then I restarted the computer, and voila, compiz just worked. I didn't have to do any of the stuff like making a script so a launcher could start compiz, or add compiz to my gnome session or anything else, it just worked...

I then realised compiz wa a little out of date in the ubuntu repos though, so I added:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

To my sources.list and ran an update. Great, now I have the latest compiz...the problem thoughst work" when all the guides I can find say thee are more steps, and how to I go about getting theme to work? I have installed cgwd and cgwd-themes as well as a gui themer which allows me to select a theme but it doesn't actually change.

---

### Post by yatt on 2006-08-26
To rain on your parade, the scripts are for the other method.

---

### Post by viciouslime on 2006-08-26
Thanks, i've fixed it now, here's how for anyone in same situation:

Firstly, change the repos to be

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

Even though I'm not using aiglx...then you can install, gnome-compiz-manager. Log out and back in and this will add an applet to your tray, click it and select preferences, then tick customisable window manager. Voila :D

---

### Post by someusernoob on 2006-08-26
Run 

```

cgwd --replace

```

It can look cool, but its kinda slow compared to the normal window decorator.

To switch back:
```

gnome-window-decorator --replace

```

Insert the codes by using alt+F2.

Otherwise add an & at the end of the line, so you can keep on using your terminal.

//edit, ow, i was too slow lol.

---

### Post by viciouslime on 2006-08-26
Lol thanks anyway! At least now I finally know what putting an & after a command does!

---

