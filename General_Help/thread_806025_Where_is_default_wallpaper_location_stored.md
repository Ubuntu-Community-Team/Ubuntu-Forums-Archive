---
title: "Where is default wallpaper location stored?"
date: 2008-05-24
forum: General Help
---

### Post by DaddyX3 on 2008-05-24
Hello all, I'm trying to make a custom .iso with my own apps installed and have successfully made .iso's with all that I wanted to include except for one ... the wallpaper in a live session is just plain brown and not even the stock Hardy wallpaper! I need to find out where to specify the default wallpaper for all users and new users that are created. If I can find out how to do this I think the result will be burned to the .iso, but for the life of me I can't find out where!?

-anybody know where to specify what the default wallpaper is supposed to be? I have a sneaking suspicion that it is in some kind of gconf file but don't know how to edit these?

---

### Post by drs305 on 2008-05-24
The default wallpapers are in /usr/share/backgrounds

---

### Post by DaddyX3 on 2008-05-24
> **drs305 said:**
> The default wallpapers are in /usr/share/backgrounds

Thank you for the reply, but this is not where the actual data is called upon. I've tried this directory and for some reason the wallpaper does not show up as the default wallpaper when I create the .iso. I believe that I am looking for not just an actual "holding-place" but rather the spot within gnome configuration files that specifies it for the default paper of all new users. I'm sorry if this sounds confusing, but I know it exists, but just not how to edit gnome.conf files and which file it actually is. 
-once again, thank you for your response. You are correct, but not exactly what I was looking for. (yes, this is where wallpaper is stored for global, but not the code that calls upon it:( )

---

### Post by drs305 on 2008-05-24
My wallpaper is designated in gconf-editor in: /desktop/gnome/background/picture_filename

The background settings also control centering, opacity, etc.

It references an image I have in one of my data folders.

Is that what you are looking for?

---

### Post by DaddyX3 on 2008-05-24
> **drs305 said:**
> My wallpaper is designated in gconf-editor in: /desktop/gnome/background/picture_filename

The background settings also control centering, opacity, etc.

It references an image I have in one of my data folders.

Is that what you are looking for?

Nope, sorry. You are close though. I know that it is prob. in an .xml file somewhere. The one you just referred to is where your particular user that is logged into right now has their wallpaper set. But this is not the location of the default wallpaper that will be shown upon a creation of all new users. For example, create a new user and see what wallpaper comes up on their desktop. Now, this is a "trick" statement. I have found somewhere that I can create a new user and have the wallpaper I have setup be their new wallpaper by default, but for some reason it does not transfer over onto the .iso image created of my setup using remastersys. I have hit a wall with help from the creator of remastersys, because he is an KDE guy and I run gnome. He says that he is not familure with the gnome configuration files. Everything else works beautifully and I have a sweet .iso with custom theme setup, FireFox themes by default changed, all programs installed and usable, but NO WALLPAPER! Not even the stock Hardy one shows up on the live session DVD (prob. because of stuff I've changed trying to get it to load the one I want:oops:
-now I fear that even if I start over with a virgin copy of Hardy and start from scratch with "fresh config. files" I'll still be at a loss here. 

Once again, thank you very much for your time and consideration --- it is greatly appreciated!

---

