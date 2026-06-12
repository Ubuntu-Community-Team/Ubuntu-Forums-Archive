---
title: "Panel to the bottom (Ubuntu 12.04)"
date: 2012-10-17
forum: General Help
---

### Post by jorgl on 2012-10-17
Hi there everybody!

I am new on Linux so I have a lot of questions about it. One of them is the following:

Is there any way to put the panel of the Ubuntu 12.04 to the bottom of the screen?

Thank you, buddies!

---

### Post by pompel9 on 2012-10-17
This is not possible as of yet. I don't know if they will add this option later on.

---

### Post by jorgl on 2012-10-17
> **pompel9 said:**
> This is not possible as of yet. I don't know if they will add this option later on.

That´s not good. Not good at all! :-( 

Thank you anyway!

---

### Post by Frogs Hair on 2012-10-17
The unofficial bottom launcher was never updated for 12.04 and is based on different version of Unity. [http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html](http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html)

---

### Post by offgridguy on 2012-10-17
With ubuntu you do have the option of using other desktop enviroments.  check out the threads in 
DE and you will probably find something there relative to your situation.:)

---

### Post by jorgl on 2012-10-17
> **Frogs Hair said:**
> The unofficial bottom launcher was never updated for 12.04 and is based on different version of Unity. [http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html](http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html)

Thank you! I am gonna be waiting look forward to the new version of this bottom launcher.

---

### Post by jorgl on 2012-10-17
> **offgridguy said:**
> With ubuntu you do have the option of using other desktop enviroments.  check out the threads in 
DE and you will probably find something there relative to your situation.:)

Alright. But what "DE" means?

---

### Post by quequotion on 2012-10-17
> **jorgl said:**
> Thank you! I am gonna be waiting look forward to the new version of this bottom launcher. It is highly unlikely that will ever happen, as there have been no updates for a year and unity has changed quite a lot. Furthermore, Canonical has made it clear that customization is *not* part of the unity design. If customization is important to you, it's time to consider another DE.
> **jorgl said:**
> Alright. But what "DE" means?"Desktop Environment", which is all the visible parts and pieces of your computer's graphical interface. Ubuntu's official DE is "Unity" (though perhaps it will be called "Ayatana" one day) which is actually *compiz* with a plugin called "unity" that provides a launcher bar, on the right edge, and a panel, across the top edge. Other features of this DE include the GNOME Project's software suite, the application indicator panel, a global menu, and hovering scrollbars.

Notable failures and often criticized points of this DE are it's lack of customization (which Canonical has expressed no interest in adding in the future), incompatibility of the indicator panel with older notification area icons (slowly being resolved by replacing icons with indicators and kludges for some, like WINE), incompatibility of certain programs with the global menu (notably Open Office), usability and functionality issues with hovering scrollbars (which are part of the touchscreen design), and being drawn in to the GNOME Project's reckless downsizing (no screensavers, less options, etc.).

Citing these, and other issues, some users have elected to install one of the myriad other desktop environments that are available: GNOME, KDE, XFCE, LXDE, OpenBox, Awesome, etc, etc. Other Ubuntu users have been using them all along, particularly the officially sanctioned Ubuntu derivatives Kubuntu (KDE), Xubuntu (XFCE), and Lubuntu (LXDE).

A more recent alternative that is gaining popularity is the "Cinnamon" DE from Linux Mint, which is also an Ubuntu derivative. Cinnamon is derived from GTK3, like GNOME, but designed to resemble GTK2  GNOME, since the GNOME Project has dedicated itself to their  controversial Gnome-Shell desktop.

Each DE has pros and cons and each DE is designed for a certain target audience.  Unity, Cinnamon, GNOME, and KDE are general-purpose. LXDE and XFCE are general-purpose, lightweight alternatives for users who don't need all the bells and whistles or have to conserve resources. Others target more specific users and use cases. OpenBox, for example, is very light and very flexible, but comes with few parts and pieces to work with (the basic desktop is a background and a mouse cursor)--it is also the basis of LXDE. Awesome is a whole other desktop metaphor that may be very effective for people who prefer to use their keyboard rather than their mouse.

As offgridguy pointed out, there is a[ subforum]("http://ubuntuforums.org/forumdisplay.php?f=329") for discussing this topic.

---

### Post by philinux on 2012-10-17
> **jorgl said:**
> Alright. But what "DE" means?

DE Desktop environment. Have a look at this.

[http://www.webupd8.org/2012/10/lightweight-qt-desktop-environment.html?m=1](http://www.webupd8.org/2012/10/lightweight-qt-desktop-environment.html?m=1)

---

### Post by quequotion on 2012-10-18
[Pantheon]("http://elementaryos.org/discover"), the DE of ElementaryOS, may be just what you're looking for. It has a horizontal launcher at the bottom of the screen and it's GTK3, so it supports Ubuntu's default software suite. 

This can be installed like so:

1. Open a terminal: [ctrl]+[alt]+[t]

2. Add the ElementaryOS Daily PPA source:```
sudo add-apt-repository ppa:elementary-os/daily
```This will give you a scary warning. Press [Enter] to continue.

3. Update sources and install pantheon-shell```
sudo apt-get update && sudo apt-get install pantheon-shell
```4. Log out.

5. Before you log back in, click the Ubuntu symbol next to your name and select "Pantheon".

6. Log in.
_________________________________________

If you like it, you may want to install the configuration addons:```
sudo apt-get install switchboard switchboard-gnome-control-center switchboard-plug-pantheon-shell
``` There are lots of other extras you may want to look into.
_________________________________________

If you don't like it, or it does something strange to your computer, you can remove it like so:

1. Install ppa-purge: ```
 sudo apt-get install ppa-purge 
```2. Purge the ElementaryOS Daily PPA:```
 ppa-purge ppa:elementary-os/daily
```

---

### Post by jorgl on 2012-10-18
> **quequotion said:**
> [Pantheon]("http://elementaryos.org/discover"), the DE of ElementaryOS, may be just what you're looking for. It has a horizontal launcher at the bottom of the screen and it's GTK3, so it supports Ubuntu's default software suite. 

This can be installed like so:

1. Open a terminal: [ctrl]+[alt]+[t]

2. Add the ElementaryOS Daily PPA source:```
sudo add-apt-repository ppa:elementary-os/daily
```This will give you a scary warning. Press [Enter] to continue.

3. Update sources and install pantheon-shell```
sudo apt-get update && sudo apt-get install pantheon-shell
```4. Log out.

5. Before you log back in, click the Ubuntu symbol next to your name and select "Pantheon".

6. Log in.
_________________________________________

If you like it, you may want to install the configuration addons:```
sudo apt-get install switchboard switchboard-gnome-control-center switchboard-plug-pantheon-shell
``` There are lots of other extras you may want to look into.
_________________________________________

If you don't like it, or it does something strange to your computer, you can remove it like so:

1. Install ppa-purge: ```
 sudo apt-get install ppa-purge 
```2. Purge the ElementaryOS Daily PPA:```
 ppa-purge ppa:elementary-os/daily
```

Wow! Thank's a lot for both messages! I am glad that I can find help from good people in this forum. 

Big hug man!

---

### Post by jorgl on 2012-10-18
> **philinux said:**
> DE Desktop environment. Have a look at this.

[http://www.webupd8.org/2012/10/lightweight-qt-desktop-environment.html?m=1](http://www.webupd8.org/2012/10/lightweight-qt-desktop-environment.html?m=1)


Thank you for the article, buddy! Big hug!

---

### Post by cmcanulty on 2012-10-18
try gnome classic put as many panels as you want wherever you want very similar to ubuntu before it was "improved" by unity

---

### Post by quequotion on 2012-10-19
> **jorgl said:**
> I am glad that I can find help from good people in this forum.That's what they're here for :)

I installed Pantheon myself while working on that post. It's not as feature-rich as Unity, but development is making progress and it should be really effective soon. As a down-to-basics DE it works well enough.

---

### Post by jorgl on 2012-10-19
> **cmcanulty said:**
> try gnome classic put as many panels as you want wherever you want very similar to ubuntu before it was "improved" by unity

I think gnome classic is not available anymore in Ubuntu 12.04. Saddly. But thank you for your attention anyway! :-)

---

### Post by jorgl on 2012-10-19
> **quequotion said:**
> That's what they're here for :)

I installed Pantheon myself while working on that post. It's not as feature-rich as Unity, but development is making progress and it should be really effective soon. As a down-to-basics DE it works well enough.

Well.. since I am too far away from being a Linux expert (this is the very first time I start using linux in my life) I think I would keep my ubuntu like it is.

All wanted was put the panel at the bottom so I would find ubuntu 12.04 a little bit closer from Windows 7 (which was the OS that I am used to). But now I think I am getting more confortable with linux.

Thank you very very much for you attention, quequotion! Be sure that are guys like you that make this forum be so fantastic like it is. And guys like you also make me even more confortable for using Linux for the first time. Thnk you again. Giant hug for u, dude!

---

### Post by cmcanulty on 2012-10-20
wrong. I have it and with long term support until 2017 you are set for a while, see the links below. Very easy to set up, email me with any questions. I run it on 5 machines at home and 11 at our local library.

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed")

[http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/")

---

### Post by jorgl on 2012-10-20
> **cmcanulty said:**
> wrong. I have it and with long term support until 2017 you are set for a while, see the links below. Very easy to set up, email me with any questions. I run it on 5 machines at home and 11 at our local library.

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed")

[http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/03/return-to-gnome-classic-in-ubuntu-12-04-precise-pangolin/")

Yeah! Sorry! You are completely right! It works. And I dont why, but I really like gnome classic for than unity. Thank you so much for you attention!

---

### Post by cmcanulty on 2012-10-20
I love classic and just think unity is very rigid and not workable

---

### Post by SantaFe on 2012-10-20
Nice post!  Learned a lot.  However: > **quequotion said:**
> Ubuntu's official DE is "Unity" (though perhaps it will be called "Ayatana" one day) Perhaps they should call it Ayatollah instead, as in "Ay-a-toll-ah we won't move the Unity Bar!" ;)

---

### Post by quequotion on 2012-10-20
> **SantaFe said:**
> Nice post!  Learned a lot.  However:  Perhaps they should call it Ayatollah instead, as in "Ay-a-toll-ah we won't move the Unity Bar!" ;) Nice!

---

### Post by lemonoid on 2012-10-21
you can just install Docky. It allows you to create a new dock (multiple themes as well) with various effects and preferences allowing you to move it to different sides of your desktop. And I really haven't tried to make many changes to my desktop in 12.04, but I know in previous versions you could hide the bar on the left side of your screen (auto-hide). SO technically, if that feature is still around you could just autohide and use Docky. I use Docky anyways. Its fairly efficient. That is also the dock that a previous post is referencing with ElementaryOS, they use Docky I believe.

---

### Post by goldshirt9 on 2012-10-21
> **jorgl said:**
> Well.. since I am too far away from being a Linux expert (this is the very first time I start using linux in my life) I think I would keep my ubuntu like it is.

[COLOR=DarkRed]All wanted was put the panel at the bottom so I would find ubuntu 12.04 a little bit closer from Windows 7 (which was the OS that I am used to). But now I think I am getting more confortable with linux.[/COLOR]

Thank you very very much for you attention, quequotion! Be sure that are guys like you that make this forum be so fantastic like it is. And guys like you also make me even more confortable for using Linux for the first time. Thnk you again. Giant hug for u, dude!

Have a look at Zorin OS .[http://zorin-os.com/#](http://zorin-os.com/#)

 a easy linux distro. started me out on the road to full linux os[]("http://zorin-os.com/#")

---

### Post by Redalien0304 on 2013-02-13
Try  Cinnamon out has start menu at bottom of the screen 
[http://www.noobslab.com/2012/10/install-latest-cinnamon-16-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-cinnamon-16-in-ubuntu.html)

---

