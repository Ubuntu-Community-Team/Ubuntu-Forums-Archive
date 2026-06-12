---
title: "xubuntu, need something faster, check the apps"
date: 2007-08-24
forum: General Help
---

### Post by phillips321 on 2007-08-24
Hi guys,

Currently got xubuntu on my laptop, how could i make the laptop faster still?

It's only a Transmeta 1GHz, 256MB and a really really slow 1.8" 20GB HDD.

I was thinking of installing ubuntu-server (without LAMP) and then adding flux/black box to it? Are there any lighter window managers. The laptop is used for nothing more than the following:

Web Browsing--> Firefox runs crap, any other alternatives?
DIVX Playing --> mplayer seems to work best with the gfx card
SSH to desktop --> what's the fastest terminal/console/shell to use?

Cheers in advance

---

### Post by K.Mandla on 2007-08-24
> **phillips321 said:**
> It's only a Transmeta 1GHz, 256MB and a really really slow 1.8" 20GB HDD.
That is about what I run. 

> **phillips321 said:**
> I was thinking of installing ubuntu-server (without LAMP) and then adding flux/black box to it? Are there any lighter window managers. 
Fluxbox is definitely a contender; I am partial to Openbox because it is easy to configure and set up. IceWM might interest you; I do not really care for the Windows-esque layout, and I find it a bit more tricky to set up how I like.

There are a lot of suggestions in the wiki.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

That page describes systems with "low memory," but the idea is the same -- slower but not obsolete systems.

---

### Post by kerry_s on 2007-08-24
yeap, you should go custom to get the best performance. You got better specs than mine, but mine ain't slow. before you do anything, try the other wm's and see what you like, play with them see what's easier for you to get the hang of. then just wipe the whole thing and build it with what you like.

---

### Post by Seisen on 2007-08-24
> **K.Mandla said:**
> That is about what I run. 


Fluxbox is definitely a contender; I am partial to Openbox because it is easy to configure and set up. IceWM might interest you; I do not really care for the Windows-esque layout, and I find it a bit more tricky to set up how I like.

There are a lot of suggestions in the wiki.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

That page describes systems with "low memory," but the idea is the same -- slower but not obsolete systems.

I agree with about using Openbox, I used to use Fluxbox before. The only thing is that Openbox has a slight learning curve compared to Fluxbox.

---

### Post by trippinnik on 2007-08-24
You could try Enlightenment e17.  It's fast, but looks really good and has some good modules for a lot of the things you'd expect to find in your window manager.  Unfortunately it's still beta so it might be missing something you need.

---

### Post by por100pre1 on 2007-08-24
Install Fluxbox it is light and simple:

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install fbdesk fbpager fluxbox fluxconf menu idesk
```

If you want a light file browser install rox too:

```
sudo apt-get install rox-filer
```

When finished build the Fluxbox menu:

```
sudo update-menus
```

Finally look for Fluxbox in the login menu.

Hope this helps. :)

---

### Post by RedSquirrel on 2007-08-24
Here's another link to consult for a minimal install:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

> **por100pre1 said:**
> Install Fluxbox it is light and simple:

```
sudo apt-get update && sudo apt-get upgrade
``````
sudo apt-get install fbdesk fbpager fluxbox fluxconf menu idesk
```If you want a light file browser install rox too:

```
sudo apt-get install rox-filer
```When finished build the Fluxbox menu:

```
sudo update-menus
```I would advise stopping here. These steps...

> **por100pre1 said:**
> ```
cd ..
``````
mkdir .fluxbox
``````
cp /etc/X11/fluxbox/fluxbox-menu /home/*your-user-name*/.fluxbox/menu
```

are not necessary. When you login to Fluxbox, the script /usr/bin/startfluxbox runs automatically and it will create the ~/.fluxbox directory and the necessary configuration files.

---

### Post by mojoman on 2007-08-24
+1 for fluxbox. I use it on my laptop with similar specs, running on Debian Etch. It's quite fast.

Check out x-term or a-term, both are lightweight consoles (I use x-term on my laptop). For *really* lightweight web surfing you could use links or links2. Otherwise Opera might be an option. I think it's a little less bloated then Firefox but I might be wrong.  For video mplayer is probably a good bet but an alternative might be vlc.

Check out DSL (Damn Small Linux), you could have a look at the apps that comes with it by default. That should give you a nice list of lightweight applications.

---

### Post by K.Mandla on 2007-08-24
> **Seisen said:**
> The only thing is that Openbox has a slight learning curve compared to Fluxbox.
:D That's funny, I thought the same thing about Fluxbox. ;)

---

### Post by cebobbitt on 2007-08-24
I've used Fluxbox, Blackbox, Openbox, Icewm and some I can't even remember their names. I cast my vote for Fvwm, you can do just about anything with it and it looks good. All of them are good but I just adore Fvwm, it too has somewhat of a learning curve. Good Luck

---

