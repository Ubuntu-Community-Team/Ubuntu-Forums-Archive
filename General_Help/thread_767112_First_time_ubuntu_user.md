---
title: "First time ubuntu user"
date: 2008-04-25
forum: General Help
---

### Post by immortal7792 on 2008-04-25
i just installed ubuntu for the first time and it is not particularly easy to me. if someone could answer these few questions it would be an enormous help.

1. I don't get how to install Beryl
2. I dont get how to install any packages for instance flashplayer(its a tar file)
3.Change the resolution of the screen?
4. if anyone could recomend the best media player. that would be very helpful too.

---

### Post by tompickles on 2008-04-25
ok - number 2 is easy. especially in hardy (8.04) point firefox to a [site with flash content]("http://www.addictinggames.com") and it will notify you to say you need to install missing plugins - so click on intall missing plugins - then pick one. i would (as i have myself on my hardy box) use the adobe one, as this, despite being not open source, just works. it will probably ask you for your password to authorise the administration action(installing stuff) really easy, and it will install it all nice and lovely for you, including refreshing the tab so it loads properly.

you can install a ton of applications sorted into categorys by hitting applications menu, the Add/Remove Applications.. at the bottom.

---

### Post by tompickles on 2008-04-25
3. - i think this is somewhere in the system menu (the third on along the top) then preferences and screen resoltion. what is it at the moment? and, if your wanted or expected resolution isnt available, im not the best person to ask, but that is where the easy to use graphical application is.

---

### Post by xaenyx on 2008-04-25
> **immortal7792 said:**
> i just installed ubuntu for the first time and it is not particularly easy to me. if someone could answer these few questions it would be an enormous help.

1. I don't get how to install Beryl
2. I dont get how to install any packages for instance flashplayer(its a tar file)
3.Change the resolution of the screen?
4. if anyone could recomend the best media player. that would be very helpful too.

2. It works the same way in ubuntu as in windows.  Go to a site that needs flash (e.g. addicting games) and click on the banner that appears on the top of firefox.  It will list several options, choose the non-free lash player.  For all other apps, go into the menu in the upper-left-hand corner and select add/remove.


4.) Rhythmbox and exaile are both good.  Amarok is nice but it is for kde (will work with gnome, but not as well).  Also look at elisa media player.

---

### Post by forestpixie on 2008-04-25
You have compiz installed, Beryl is finished I think, it's not active until you have a suitable driver for the graphics card. To get a driver firstly try Hardware Drivers in System Admin, once you've got that done open a terminal and paste this command in - you will need to enter your password but it will be invisible.

```
sudo apt-get install simple-ccsm compizconfig-settings-manager
```
 That will install the manager for the compiz setup.

Resolution is in System Preferences, but if you haven't got a driver installed you probably won't have much to choose from.

Asking for media players will get many different answers, for music I use exaile or amarok depending on my mood, I use mplayer and vlc for video. Open Add/Remove and have a look there. 

Welcome and good luck

---

### Post by Comhra on 2008-04-25
Ok, go to:System, Administration, Synaptic Package Manager

1. Search for: compizconfig-settings-manager, Click the Grey Square and Mark for Installation, if a Dialogue box pops up, mark any Additional required changes, the green apply mark will light up, click it and relax.  A Google will get the Cube working for you.


2. Tarballs are hard, stay away.  Go to Youtube, click any Video and install the plugin.


3. System, Preferences, Screen resolution,

4. The very, very best by a mile in my estimation is Amarok ( but you may not want to install it if you're using Gnome since it belongs to KDE which is another desktop manager)  Mind you, it always works as advertised in Gnome as well.

Banshee is a good Gnome player to try but there are plenty to choose from.

To install go to Applications>Add/Remove>Show (all available apps) Click Sound and Video or you can simply use the search bar.

Hope this is helpful.

---

### Post by immortal7792 on 2008-04-25
what about beryl i downloaded this: emerald-0.2.1.tar.bz2   i dont know what it is or what to do with it.

---

### Post by forestpixie on 2008-04-25
emerald is a window decorator - you'll need it in compiz to do window decoration. Before you start using tarballs check that the repos have it - you can do this easiest through synaptic.

Assuming you get the graphics working ok - the compiz settings manager has a window decoration plugin - you can use emerald from there.

Just go one step at a time - get the graphic driver sorted first and the rest will drop into place.

---

### Post by immortal7792 on 2008-04-25
i tried it but this is what happens
[IMG]http://i27.tinypic.com/3028cpv.png[/IMG]
it stays there for a long time.

---

### Post by immortal7792 on 2008-04-25
i tried it but this is what happens
[IMG]http://i27.tinypic.com/3028cpv.png[/IMG]
it stays there for a long time.

---

### Post by forestpixie on 2008-04-25
It's timing out then - everyman and his dog are on the servers at the moment - leave it alone and if it can connect it will. Do make sure that you have your sources setup correctly though. Open software sources in system > admin

enable main, universe and restricted on the 3rd party tab enable the ubuntu partner repo - don't enable sources, close and it will try to reload let it do it.

If that times out you'll need to do it again, but this time you can do it in a terminal with 

```
sudo apt-get update
```

If it's halfway through something to do with installing - don't turn it off if it looks like it's stopped, you'll get problems.

Patience is the key at the moment I'm afraid.

---

### Post by forestpixie on 2008-04-25
Just so that you know you cannot do more than one thing at a time with the apt system - that includes running apt-get or aptitude from the terminal, add/remove in the menu or synaptic.

---

### Post by immortal7792 on 2008-04-25
finally worked. what exactly is the thing. also how do install the emerald themes

---

### Post by forestpixie on 2008-04-25
You can get emerald themes from [here]("http://compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=3f978bade312858fed01a831ecba88d1")

Open emerald - it's in System > Preferences - use the import button and navigate to the emerald theme.

IF you're going to use it open the compiz config manager - in same menu as emerald, find the window decoration plugin - open that and in the command box put

```
emerald --replace
```

you might have that information but the servers are so slow I'm not going to try and go to the thread again. To enable compiz - go to appearances in the same preferences menu - visual effects - custom.

If when you restart you lose the terminal - it'll be a white box and you're running with an nvidia card try this command by Alt+F2 

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

