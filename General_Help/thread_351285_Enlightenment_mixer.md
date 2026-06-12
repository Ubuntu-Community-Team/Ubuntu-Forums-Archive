---
title: "Enlightenment mixer ?"
date: 2007-02-01
forum: General Help
---

### Post by bestial on 2007-02-01
Just installed Enlightenment and it feels very nice, but I can't get the mixer to work. I guess that I have to direct it to the mixer I used in gnome, which I assume is the "original one". But I have no idea what it's namned or where it lies.

Anyone with an idea? I rip my head everytime I have to go to XMMS and lower the volume through it.

---

### Post by PetePete on 2007-02-02
if you install the epplets there is a volume control one u can use.

---

### Post by bestial on 2007-02-02
installed epplets, but I can't find it anywhere, I feel so stupid right now. >_<

---

### Post by tcrroadie on 2007-02-02
> **bestial said:**
> Just installed Enlightenment and it feels very nice, but I can't get the mixer to work. I guess that I have to direct it to the mixer I used in gnome, which I assume is the "original one". But I have no idea what it's namned or where it lies.

Anyone with an idea? I rip my head everytime I have to go to XMMS and lower the volume through it.

The sound mixer for Gnome is called gnome-volume-control.  

```
gnome-volume-control
```

---

### Post by bestial on 2007-02-02
gnome-volume-control in Xterm works fine, but I want it to interact with the mixer witch follows E17. Cause in "configuration" it says "mixer app" so I think it want's me to give it the right directories. And the only thing I can find in /usr/share is gnome-volume-manager.

The thing is that I have increase-decrease -buttons on my keyboard that I want to use.

---

### Post by tcrroadie on 2007-02-03
> **bestial said:**
> gnome-volume-control in Xterm works fine, but I want it to interact with the mixer witch follows E17. Cause in "configuration" it says "mixer app" so I think it want's me to give it the right directories. And the only thing I can find in /usr/share is gnome-volume-manager.

The thing is that I have increase-decrease -buttons on my keyboard that I want to use.

To use E17's mixer, just enable mixer in the modules settings menu of E17.  Then add the mixer module to your shelf by right clicking the shelf and selecting configure shelf contents.  Add the mixer module to your shelf.  The speaker icon for the mixer module should now be visible on your shelf.  Right click the mixer icon and select configuration at the top of the pop up menu and set your setting to your own needs.  

I'm including a screenshot from my system to show you how my mixer settings are configured. 

After the Mixer is configured you can bring up the sound mixer you set in the configuration menu by middle clicking your mouse (press the mouse wheel).  For example when I middle click on the mixer icon, gnome-volume-control launches.  

As far as using your media buttons on your keyboard, that is beyond my knowledge.  I also have media keys on my keyboard but have never had the desire to use them. 

Hope this helps.  :)

---

### Post by bestial on 2007-02-04
I've tried to put it on my shelf but it doesn't work, I'm getting really confused. My friend has an extra alternative to "available cards" in the config-menu, I see that you don't have it either, but it apperantly works anyway.

Can't figure out what the heck the problem is! >_<

I don't have the "master"-choice under Available Mixer either

EDIT: Okey, I can open gnome-volume-control by clicking on it with the scroll-wheel, but the mixer itself stands in mute. :D

---

