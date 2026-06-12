---
title: "Xububtu vs Ubuntu"
date: 2012-12-22
forum: General Help
---

### Post by mcman56 on 2012-12-22
With my older laptop, what type of speed improvement would Xububtu have over Ubuntu?  Would this only be at boot up?

---

### Post by Autodave on 2012-12-22
> **mcman56 said:**
> With my older laptop, what type of speed improvement would Xububtu have over Ubuntu?  Would this only be at boot up?

I did not notice a big difference in boot speed, but with Xubuntu, everything seemed much quicker because of the lighter RAM usage.

---

### Post by sudodus on 2012-12-22
You should also consider Lubuntu with the ultra-light desktop environment LXDE, or if you want the tools of Xubuntu:

Lubuntu with the addition of xubuntu-desktop:

After installation of Lubuntu, run
```
sudo apt-get install xubuntu-desktop
``` and select desktop environment at the login screen :-)

If you watch video clips, you will see a big improvement with lighter desktop environments.

---

### Post by mcman56 on 2012-12-22
Can I "upgrade" to Xubuntu just like upgrading to a newer version of Ubuntu?  Will all of my data files and settings get pulled in?  Or would it be like starting from scratch?  Thanks

---

### Post by sudodus on 2012-12-22
I upgraded Ubuntu --> Ubuntu and then installed the Xubuntu desktop like any other program package:

```
sudo apt-get install xubuntu-desktop
```

There is information at [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index") how to remove the traces of the other desktop environments, but they only occupy some disk space, and some part of them might come in handy some time in the future.

---

### Post by mcman56 on 2012-12-22
> **sudodus said:**
> I upgraded Ubuntu --> Ubuntu and then installed the Xubuntu desktop like any other program package:

```
sudo apt-get install xubuntu-desktop
```There is information at [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) how to remove the traces of the other desktop environments, but they only occupy some disk space, and some part of them might come in handy some time in the future.


Can you clairify?  Did you upgrade Ubuntu to Lubuntu and then load the Xubuntu desktop? I'm no expert.  Is this something to easily get wrong?  Thanks

---

### Post by Frogs Hair on 2012-12-22
Installing multiple desktops won't make the most of system resources. Consider a clean installation of Lubuntu or Xubuntu depending on hardware. Lubuntu has lower ram requirements and less bling the Last time I checked.   

[http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce)

---

### Post by snowpine on 2012-12-22
Hi mcmann, the different desktops are simply interfaces or "skins" on top of the same core system. It's possible to install as many different desktop environments as you like and switch between them depending on your mood that day. I personally have Gnome, Xfce, and Fluxbox on my main machine; I use Gnome for when I want full-featured eye candy, Fluxbox when I just want to run one app fullscreen with good performance (like when I am doing music editing), and Xfce when I need a change of pace. :)

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-22
> **mcman56 said:**
> Can you clairify?  Did you upgrade Ubuntu to Lubuntu and then load the Xubuntu desktop? I'm no expert.  Is this something to easily get wrong?  Thanks

To clarify further...
Ubuntu = Unity Desktop
Xubuntu = XFCE4 Desktop
Lubuntu = LXDE Desktop
Kubuntu = KDE Desktop

different skins, however, Lubuntu has a different underlying core as well.  They allow for the Non-PAE kernel which means simply that it will work on REALLY old computers.  I use Ubuntu (Unity Desktop) on my fast new computer.  I use Lubuntu (LXDE Desktop) on my SLOW OLD computer.  My old computer runs at a very decent usable speed.  Lubuntu keeps getting better and better too.

To have a really pure experience just do a fresh install of Lubuntu.  For Xubuntu you can simply install the XFCE4 Desktop by installing the xubuntu-desktop package.

Upgrading is not necessary.  If you are using Ubuntu 12.04 (Precise Pangolin) you can stay with that same one for 5 years (or so..)  You can upgrade to 12.10, etc... but it is not the same as adding a desktop environment.

Open a terminal and type
```

sudo apt-get install xubuntu-dektop

```

or open the Ubuntu Software Center and search for Xubuntu-desktop
to install it.
I hope that is clear enough :)

---

### Post by sudodus on 2012-12-22
> **mcman56 said:**
> Can you clairify?  Did you upgrade Ubuntu to Lubuntu and then load the Xubuntu desktop? I'm no expert.  Is this something to easily get wrong?  Thanks

I upgraded my Ubuntu 10.04 LTS to Ubuntu 12.04 LTS and then installed several desktop environment to test them out in a couple of computers with different hardware, but in both cases nvidia graphics.

I have another system, a low-end computer with a fresh install of Lubuntu 12.04, where I have added xubuntu-desktop.

Edit: Snowpine's and Trees's explanations are good.

---

