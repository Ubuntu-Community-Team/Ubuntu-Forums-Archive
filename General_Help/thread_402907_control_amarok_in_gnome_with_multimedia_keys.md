---
title: "control amarok in gnome with multimedia keys"
date: 2007-04-06
forum: General Help
---

### Post by harty83 on 2007-04-06
I use amarok in gnome because I like it better than the other players.  Does anyone know if it is possible to get my multimedia keys to control amarok (play,pause,stop,volume,forward,back, etc)?  They will control rhythmbox of course but not amarok.

Thanks!
Alan

---

### Post by mand0 on 2007-04-06
Is this for a laptop or keyboard?

Seems like you're missing some essential kde packages.

---

### Post by harty83 on 2007-04-06
> **mand0 said:**
> Is this for a laptop or keyboard?

Seems like you're missing some essential kde packages.

It is for a desktop.  I doubt that it is a kde package because I have the complete kubuntu installed also.  Of course the keyboard works with amarok while in kde but I prefer gnome.

Thanks!

---

### Post by lukew on 2007-04-06
> **harty83 said:**
> I use amarok in gnome because I like it better than the other players.  Does anyone know if it is possible to get my multimedia keys to control amarok (play,pause,stop,volume,forward,back, etc)?  They will control rhythmbox of course but not amarok.

Thanks!
Alan

There is an option to capture the keys and assign them to different functions.

---

### Post by strabes on 2007-04-06
I wrote a blog post about (something close to) this awhile ago. Basically you use gconf editor to set up commands for certain buttons. 

[http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/)

You'll just have to find out the names of your multimedia buttons which you should be able to do with System, Preferences, Keyboard Shortcuts. The commands for amarok are "amarok --previous" etc etc. Just type "amarok --help" to see the rest.

---

### Post by BrowneR on 2007-06-22
I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

### Post by harty83 on 2007-06-22
Thanks!  That works like a charm for me!

---

### Post by hmsf on 2007-06-26
Thanks!! It's working fine for me too!

---

### Post by crazy ivan on 2007-11-01
Thanks a lot. I got it via Script-manager and before that some keys would not work properly.

---

### Post by tresdey on 2007-11-19
Thanks a lot!! its works for me too!!!

---

### Post by BrowneR on 2007-11-19
glad people are still finding it useful.

---

### Post by Luis Macias on 2007-11-19
Thanks! the script worked for me too

---

### Post by MxGB on 2007-11-27
Thanks, script worked for me.

---

### Post by mattismyname on 2008-04-06
Thanks!  Worked beautifully.

Edit: Worked in Hardy.  Wish it were installed by default.

---

### Post by hermes0710 on 2008-05-08
Is there anything similar for kaffeine too?

---

### Post by BrowneR on 2008-05-08
> **hermes0710 said:**
> Is there anything similar for kaffeine too?

I myself don't know of anything however as the author of the Amarok script i'm sure it could easily be adapted for kaffeine.

I personally use VLC/Mplayer for most video duties but when I get a minute I'll install kaffeine and have a poke around. It's exam time for me at the moment so dont expect anything too soon ;)

---

### Post by BrowneR on 2008-05-09
> **hermes0710 said:**
> Is there anything similar for kaffeine too?

OK, I have managed to put together a [script]("http://chris.scotland.googlepages.com/") that enables the use of multimedia keys in Kaffeine. It's adapted from the Amarok script I made and packaged up with a little installer.

Let me know if you encounter any problems with it.

Cheers.

[Get it HERE]("http://chris.scotland.googlepages.com/")

---

### Post by hermes0710 on 2008-05-12
@Browner

Thank you very much! Weldone=D>

---

### Post by BrowneR on 2008-05-12
> **hermes0710 said:**
> @Browner

Thank you very much! Weldone=D>

A pleasure :)

---

